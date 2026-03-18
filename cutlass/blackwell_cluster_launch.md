# Blackwell Cluster Launch Control[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/blackwell_cluster_launch_control.html#blackwell-cluster-launch-control "Link to this heading")

## Overview[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/blackwell_cluster_launch_control.html#overview "Link to this heading")

A GEMM workload usually consists of three phases: prologue, mainloop and epilogue. Each SM will process multiple output tiles in series if the number of output tiles are much more than the number of SMs, completely exposing the overhead of prologue and epilogue.

Consider a GEMM that has `20x20x1` output tiles, running on a GPU with `100` SMs. There is another kernel occupying all the resources of `20` SMs so only `80` SMs can be used. Assume cluster shape is `1x1x1`. The following diagram shows how the schedule would look like for such a kernel.

![GEMM tiles are evenly divided among available SMs](https://docs.nvidia.com/cutlass/latest/_images/non_persistent.png)

### Static Scheduler[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/blackwell_cluster_launch_control.html#static-scheduler "Link to this heading")

CUTLASS has adopted a software technique named **persistent kernels**. Persistent clusters, or Workers, can stay on the GPU throughout kernel execution and process multiple tiles, hiding prologue and epilogue costs. The tile scheduler statically determines the next output tile to process with zero overhead.

However, static scheduler is susceptible to workload imbalance if the resources of some SMs are unavailable. The following diagram illustrates this issue.

![GEMM tiles are unevenly divided among available SMs, leading to workload imbalance](https://docs.nvidia.com/cutlass/latest/_images/persistent_static.png)

### Dynamic Scheduler with Cluster Launch Control[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/blackwell_cluster_launch_control.html#dynamic-scheduler-with-cluster-launch-control "Link to this heading")

A fundamental limitation of persistent scheduling is that the number of SMs this kernel can utilize is unknown in real time. Some SMs might be occupied by another kernel and thus their resources are unavailable. This makes it challenging to load-balance work across SMs.

Blackwell introduces cluster launch control (CLC) for dynamic scheduling. (See https://docs.nvidia.com/cuda/parallel-thread-execution). With this feature, the kernel launches a grid containing as many threadblocks as there are output tiles to compute in the kernel – just like one would in a non-persistent kernel. Here we define `ClcID` to be a coordinate from the 3D grid launched on GPU.

Cluster launch control follows the below rules:

1.  A `ClcID` will be launched as a Worker when there are available resources.
2.  A `ClcID` can be queried by an existing Worker via `clusterlaunchcontrol.try_cancel` instruction.
3.  Every `ClcID` is guaranteed to be processed by either (1) or (2).
4.  Each worker uses the `{blockIdx.x, blockIdx.y, blockIdx.z}` coordinate as the first output tile to process and uses the CLC query for subsequent processing of output tiles.
5.  `clusterlaunchcontrol.try_cancel` instruction returns either a success signal with a `ClcID` or a decline signal. The most common reason of a decline is that all `ClcID`s have been processed.
6.  Cluster launch control works on the granularity of clusters. For example, a 2x2 persistent worker cluster’s query will consume 2x2 `ClcID`s at once.

The following diagram shows how the schedule would look like with cluster launch control.

![GEMM tiles are dynamically allocated among available SMs, leading to a balanced workload](https://docs.nvidia.com/cutlass/latest/_images/persistent_clc.png)

## Programming Model[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/blackwell_cluster_launch_control.html#programming-model "Link to this heading")

### Pseudo Code[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/blackwell_cluster_launch_control.html#pseudo-code "Link to this heading")

#### Non-persistent kernel[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/blackwell_cluster_launch_control.html#non-persistent-kernel "Link to this heading")

// Non-persistent kernel
\_\_device\_\_ non\_persistent\_kernel(...) {
  setup\_common\_data\_structures();
  dim3 workCoordinates \= blockIdx;
  coordinate\_specific\_compute(workCoordinates);
}

Copy to clipboard

#### Static Persistent Kernel[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/blackwell_cluster_launch_control.html#static-persistent-kernel "Link to this heading")

// Static Persistent Kernel
\_\_device\_\_ static\_persistent\_kernel(...) {
  setup\_common\_data\_structures(...);
  dim3 workCoordinates \= blockIdx;
  bool isValidId;
  do {
    coordinate\_specific\_compute(workCoordinates);
    std::tie(isValidId, workCoordinates) \= staticTileScheduler.fetch\_next\_work();
  } while (isValidId);
}

Copy to clipboard

#### Blackwell Dynamic Persistent Kernel[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/blackwell_cluster_launch_control.html#blackwell-dynamic-persistent-kernel "Link to this heading")

// Dynamic Persistent Kernel
\_\_device\_\_ clc\_dynamic\_persistent\_kernel(...) {
  setup\_common\_data\_structures(...);
  dim3 workCoordinates \= blockIdx;
  dim3 newClcID;
  bool isValidId;
  do {
    coordinate\_specific\_compute(workCoordinates);
    std::tie(isValidId, newClcID) \= clcTileScheduler.fetch\_next\_work();
    workCoordinates \= newClcID;
  } while (isValidId);
}

Copy to clipboard

### Cluster Launch Control Pipeline Class[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/blackwell_cluster_launch_control.html#cluster-launch-control-pipeline-class "Link to this heading")

Please refer to the `PipelineCLCFetchAsync` pipeline class defined in [Cluster launch control pipeline class](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/pipeline/sm100_pipeline.hpp). Cluster launch control queries can be pipelined and managed by an asynchronous pipeline with producer-consumer relationship (See [pipeline](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/pipeline.html) document). The producer is the scheduler warp of the 0th CTA in the cluster and the consumers are all warps that need `ClcID`s.

To setup a CLC pipeline correctly, we need to make sure the params are set to the right values:

-   `transaction_bytes` is `16` as CLC will return a 16B response and store it in the specified shared memory address.
-   `consumer_arv_count` is the thread count of all the consumer warps in the cluster.
-   `producer_arv_count` is `1` because only one thread from scheduler warp will be elected to issue `clusterlaunchcontrol.try_cancel`.
-   `producer_blockid` is `0` to denote that the first CTA in the cluster is producing.

### Dynamic tile scheduler class[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/blackwell_cluster_launch_control.html#dynamic-tile-scheduler-class "Link to this heading")

Please refer to `PersistentTileSchedulerSm100` class defined in [sm100 dynamic persistent tile scheduler](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/kernel/sm100_tile_scheduler.hpp).

There are two important methods of the CLC scheduler class. The first is `advance_to_next_work`, which is intended to be executed by one elected thread from the scheduler warp. It effectively sends out the CLC query to the CLC. A CLC query response will be broadcast to the same shared memory address of all CTAs in the cluster.

The other method is named `get_current_work`. It simply loads the CLC response from the shared memory buffer indexed by a pipeline state.

The CLC pipeline and scheduler classes are used together to ensure correct functionality and necessary synchronization of CLC feature. Please refer to [cluster launch control pipeline unit test](https://github.com/NVIDIA/cutlass/tree/main/test/unit/pipeline/pipeline_cluster_launch_control_async_warp_specialized_blackwell.cu).

## Blackwell Warp-specialized Persistent Kernel[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/blackwell_cluster_launch_control.html#blackwell-warp-specialized-persistent-kernel "Link to this heading")

Now, let’s take a look at how CLC feature is used in our [Blackwell dense GEMM kernel](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/kernel/sm100_gemm_tma_warpspecialized.hpp).

This particular warp-specialized kernel has the following warp assignment:

| Warp Role | Warp |
| --- | --- |
| MMA | 0   |
| Scheduler | 1   |
| Mainloop Load | 2   |
| Epilogue Load | 3   |
| Epilogue | 4, 5, 6, 7 |

Scheduler warp is the producer of the CLC pipeline. The consumers are the MMA, Mainloop Load, Epilogue Load and Epilogue warps. In addition, the scheduler warp is its own consumer! This is because it needs the `success` information from the query to terminate the persistent loop on end-of-grid.

The CLC pipeline has a depth of 3 to overlap the CLC operations of multiple waves for latency hiding. The first `ClcID` is the preloaded `blockIdx`, which does not require CLC query and is fully static.