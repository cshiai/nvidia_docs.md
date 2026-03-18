# Efficient GEMM in CUDA[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#efficient-gemm-in-cuda "Link to this heading")

CUTLASS implements the hierarchically blocked structure described in [CUTLASS: Fast Linear Algebra in CUDA C++](https://devblogs.nvidia.com/cutlass-linear-algebra-cuda/) and the [CUTLASS GTC2018 talk](http://on-demand.gputechconf.com/gtc/2018/presentation/s8854-cutlass-software-primitives-for-dense-linear-algebra-at-all-levels-and-scales-within-cuda.pdf).

## Hierarchical Structure[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#hierarchical-structure "Link to this heading")

The basic triple loop nest computing matrix multiply may be blocked and tiled to match concurrency in hardware, memory locality, and parallel programming models. In CUTLASS, GEMM is mapped to NVIDIA GPUs with the structure illustrated by the following loop nest.

for (int cta\_n \= 0; cta\_n < GemmN; cta\_n += CtaTileN) {                     // for each threadblock\_y           } threadblock-level concurrency
  for (int cta\_m \= 0; cta\_m < GemmM; cta\_m += CtaTileM) {                   //    for each threadblock\_x        }

    for (int cta\_k \= 0; cta\_k < GemmK; cta\_k += CtaTileK) {                 //       "GEMM mainloop" - no unrolling
                                                                            //                       - one iteration of this loop is one "stage"
                                                                            //
      for (int warp\_n \= 0; warp\_n < CtaTileN; warp\_n += WarpTileN) {        // for each warp\_y                  } warp-level parallelism
        for (int warp\_m \= 0; warp\_m < CtaTileM; warp\_m += WarpTileM) {      //    for each warp\_x               }
                                                                            //
          for (int warp\_k \= 0; warp\_k < CtaTileK; warp\_k += WarpTileK) {         //       fully unroll across CtaTileK
                                                                            //         - one iteration of this loop is one "k Group"
                                                                            //
            for (int mma\_k \= 0; mma\_k < WarpTileK; mma\_k += MmaK) {         // for each mma instruction         } instruction-level parallelism
              for (int mma\_n \= 0; mma\_n < WarpTileN; mma\_n += MmaN) {       //    for each mma instruction      }
                for (int mma\_m \= 0; mma\_m < WarpTileM; mma\_m += MmaM) {     //        for each mma instruction  }
                                                                            //
                  mma\_instruction(d, a, b, c);                              //            TensorCore matrix computation

                }   // for mma\_m
              }   // for mma\_n
            }   // for mma\_k

          }   // for warp\_k
        }   // for warp\_m
      }   // for warp\_n

    }   // for cta\_k
  }   // for cta\_m
}   // for cta\_n

Copy to clipboard

This tiled loop nest targets concurrency among

-   threadblocks,
-   warps, and
-   CUDA and Tensor Cores.

It takes advantage of memory locality within

-   shared memory and
-   registers.

The figure below illustrates the flow of data within this structure. This is the hierarchical GEMM computation embodied by CUTLASS. Each stage depicts a nested level of tiling which corresponds to a layer of concurrency within the CUDA execution model and to a level within the memory hierarchy, becoming increasingly finer moving left to right.

![ALT](https://docs.nvidia.com/cutlass/latest/_images/gemm-hierarchy-with-epilogue.png)

### Threadblock-level GEMM[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#threadblock-level-gemm "Link to this heading")

Each threadblock computes its portion of the output GEMM by iteratively loading tiles of input matrices and computing an accumulated matrix product. At the threadblock level, data are loaded from global memory. The blocking strategy in general is key to achieving efficiency. However, the programmer must balance multiple conflicting goals. A larger threadblock means fewer fetches from global memory, thereby ensuring that DRAM bandwidth does not become a bottleneck. However, large threadblock tiles may not match the dimensions of the problem well. If either the GEMM _M_ or _N_ dimension is small, some threads within the threadblock may not perform meaningful work, as the threadblock may be partially outside the bounds of the problem. If both _M_ and _N_ are small while _K_ is large, this scheme may launch relatively few threadblocks and fail to make full use of all multiprocessors within the GPU. Strategies to optimize performance for this case, as described in the section [Parallelized Reductions](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#parallelized-reductions), partition the GEMM K dimension across multiple threadblocks or multiple warps. These threadblocks or warps compute matrix products in parallel; the products are then reduced to compute the result.

In CUTLASS, the dimensions of the threadblock tile are specified as `ThreadblockShape::{kM, kN, kK}` and may be tuned to specialize the GEMM computation for the target processor and dimensions of the GEMM problem.

### Warp-level GEMM[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#warp-level-gemm "Link to this heading")

The warp-level GEMM maps to the warp-level parallelism within the CUDA execution model. Multiple warps within a threadblock fetch data from shared memory into registers and perform computations. Warp-level GEMMs may be implemented either by TensorCores issuing [mma.sync](https://docs.nvidia.com/cuda/parallel-thread-execution/index.html#warp-level-matrix-instructions-mma) or [wmma](https://docs.nvidia.com/cuda/parallel-thread-execution/index.html#warp-level-matrix-instructions-wmma-mma) instructions, or by thread-level matrix computations issued to CUDA cores. For maximum performance, access to shared memory should be bank conflict free. To maximize data reuse within the warp, a large warp-level GEMM tile should be chosen.

### Thread-level GEMM[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#thread-level-gemm "Link to this heading")

At the lowest level of blocking, each thread is responsible for processing a certain number of elements. Threads cannot access each other’s registers, so we choose an organization that enables reuse of values held in registers for multiple math instructions. This results in a 2D tiled structure within a thread, in which each thread issues a sequence of independent math instructions to the CUDA cores and computes an accumulated outer product.

SGEMM, IGEMM, HGEMM, and DGEMM are computed by SIMT math instructions issued by thread-level matrix multiply procedures.

## Epilogue[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#epilogue "Link to this heading")

The above code focuses only on the matrix multiply computation **C = AB** whose result is held in the registers of each thread within the threadblock. The mapping of logical elements in the output tile to each thread is chosen to maximize performance of the matrix multiply computation but does not result in efficient, coalesced loads and stores to global memory.

The epilogue is a separate phase in which threads exchange data through shared memory then cooperatively access global memory using efficient striped access patterns. It is also the phase in which linear scaling and other elementwise operations may be conveniently computed using the matrix product results as inputs.

CUTLASS defines several typical epilogue operations such as linear scaling and clamping, but other device-side function call operators may be used to perform custom operations.

## Optimizations[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#optimizations "Link to this heading")

The hierarchical structure described above yields an efficient mapping to the CUDA execution model and CUDA/TensorCores in NVIDIA GPUs. The following sections describe strategies for obtaining peak performance for all corners of the design space, maximizing parallelism and exploiting data locality wherever possible.

### Pipelining[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#pipelining "Link to this heading")

The blocked structure demands a large storage allocation within the registers of each CUDA thread. The accumulator elements typically occupy at least half a thread’s total register budget. Consequently, occupancy – the number of concurrent threads, warps, and threadblocks – is relatively low compared to other classes of GPU workloads. This limits the GPU’s ability to hide memory latency and other stalls by context switching to other concurrent threads within an SM.

To mitigate the effects of memory latency, CUTLASS uses _software pipelining_ to overlap memory accesses with other computation within a thread. CUTLASS accomplishes this by double buffering at the following scopes.

-   **Threadblock-scoped shared memory tiles:** two tiles are allocated in shared memory. One is used to load data for the current matrix operation, while the other tile is used to buffer data loaded from global memory for the next mainloop iteration.
-   **Warp-scoped matrix fragments:** two fragments are allocated within registers. One fragment is passed to CUDA and TensorCores during the current matrix computation, while the other is used to receive shared memory fetch returns for the next warp-level matrix operation.

The following diagram illustrates the efficient, pipelined mainloop body used in CUTLASS GEMMs.

![ALT](https://docs.nvidia.com/cutlass/latest/_images/software-pipeline.png)

### Threadblock Rasterization[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#threadblock-rasterization "Link to this heading")

To maximize reuse of data held in the last level cache, CUTLASS defines several functions to affect the mapping of threadblocks to logical partitions of the GEMM problem. These map consecutively launched threadblocks to packed two-dimensional regions of the partitioned GEMM problem to increase the probability that these will access the same tiles of global memory at approximately the same time.

Several functions are defined in [cutlass/gemm/threadblock\_swizzle.h](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/threadblock/threadblock_swizzle.h).

### Parallelized Reductions[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#parallelized-reductions "Link to this heading")

**Split K - reduction across threadblocks**

Matrix product computations expose parallelism among _O(MN)_ independent inner product computations. For sufficiently large problem sizes, a GEMM kernel in CUTLASS may approach the theoretical maximum computational throughput. For small problems, however, there are too few threadblocks to efficiently occupy the entire GPU.

As a recourse, parallelizing the reduction performed during the inner product computation enables more threadblocks to execute concurrently while still taking advantage of the throughput benefits of large threadblock-level GEMM tiles.

CUTLASS implements parallel reductions across threadblocks by partitioning the GEMM _K_ dimension and launching an additional set of threadblocks for each partition. Consequently, we refer to this strategy within CUTLASS as “parallel reduction splitK.” The “parallel reduction splitK” strategy requires the execution of 2 kernels: partitionedK GEMM, and batched reduction.

PartitionedK GEMM resembles one flavor of batched strided GEMM. Instead of requiring users to specify the problem size of each batch, partitionedK GEMM asks for the overall problem size and the number of partitions that will be applied along the K dimension for operands A and B. For example, parameters of m=128, n=128, k=4096 and partition=16 will result in 16 batched strided GEMMs with each batch of m=128, n=128, k=256. PartitionedK also allows scenario where k is not divisible by the partition count.

For example, parameters of m=128, n=128, k=4096 and partition=20 will result in 20 batched strided GEMMs. The first 19 batches will have m=128, n=128, and k=4096/20=204, and the last batch will have m=128, n=128, and k=220.

The batched reduction kernel takes as input the output (C) of partitionedK GEMM, and performs a reduction along the K-dimension. Users must manage workspace memory to store this intermediate result.

**Sliced K - reduction across warps**

Similar to the split-k scenario, sliced-k aims at improving the efficiency of kernels with smaller M and N dimensions, but large K dimension. At the thread-block level, the parameters CtaTileN and CtaTileM expose parallelism by partitioning the work among warps. Larger warpTiles expose better instruction-level parallelism (ILP) and reuse, but also limit the number of warps running per threadblock, which reduces efficiency.

In order to improve efficiency in such scenarios, partitioning the warpTiles also along ctaTileK helps use the hardware more efficiently by allowing more warps to run concurrently in a CTA. Sliced-k kernels break down a threadblock’s computation among participating warps not just among the CtaTileN, CtaTileM dimension, but also the CtaTileK dimension. Thus, sliced-k entails a small cost in form of a reduction which has to happen at the end among the participating warps. This is because each warp computes using only a “slice” of CtaTileK, so each warp only has a partial sum before the reduction.

### Hopper Warp Specialization[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#hopper-warp-specialization "Link to this heading")

Note: the following section on warp-specialization contains details that are specific to the Hopper kernel design. Blackwell SM100 kernels have a substantially different warp-specialization structure, however, the concept of separating out producer and consumer agents still applies.

Starting with Hopper, CUTLASS 3.0 incorporates the concept of [Warp Specialization](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#spatial-partitioning-also-known-as-warp-specialization) as part of the kernel design. A thread block is partitioned into two sets of warps, [_producer_ warp group](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/kernel/sm90_gemm_tma_warpspecialized.hpp) and [_consumer_ warp group](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/kernel/sm90_gemm_tma_warpspecialized.hpp). The _producer_ warp group loads data from global memory into shared memory buffers using the new [Tensor Memory Accelerator (TMA)](https://developer.nvidia.com/blog/nvidia-hopper-architecture-in-depth/).

[_Producer_ warp group (DMA)](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/collective/sm90_mma_tma_gmma_ss_warpspecialized.hpp) waits for the shared memory buffers to be signaled as [empty](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/collective/sm90_mma_tma_gmma_ss_warpspecialized.hpp) by the _consumer_ warp group using the newly added **Async Pipeline class** ([refer](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/pipeline.html)). Once the data is written into the shared memory, TMA is also updates the barrier associated with that stage to notify affected threads that the buffer has been [filled](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/collective/sm90_mma_tma_gmma_ss_warpspecialized.hpp). The [_Consumer_ warp group (MMA)](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/collective/sm90_mma_tma_gmma_ss_warpspecialized.hpp) on the other hand waits for the _producer_ warp group to signal that the buffer is [filled](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/collective/sm90_mma_tma_gmma_ss_warpspecialized.hpp) and then launches tensor core MMA operations. Finally, the _consumer_ warp group [releases](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/collective/sm90_mma_tma_gmma_ss_warpspecialized.hpp) the buffers for the next set of TMA loads to happens.

**Warp-Specialized Persistent Cooperative kernel design**

Another flavor of Warp-Specialized kernel design being introduced starting with Hopper is the [_Warp-Specialized Persistent Cooperative_](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/kernel/sm90_gemm_tma_warpspecialized_cooperative.hpp) kernel. Like the Warp-Specialized kernel, the concepts of warp groups and barrier synchronization between warp groups remain the same in the cooperative design. The distinctive feature of the Warp-Specialized Persistent Cooperative kernel are the following :

-   Persistent thread blocks launched to occupy as many SMs as mentioned in the [KernelHardwareInfo](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/kernel_hardware_info.hpp) struct. These persistent thread blocks are used to tile the output and thus (potentially) compute multiple output tiles through their lifetime. The main benefit this adds is amortization of the thread-block launch and kernel prologue overheads which are typical of all kernels.
-   Presence of two _consumer_ warp groups cooperating on the same output tile by splitting the tile in half across the M dimension. This allows for larger tile sizes to be enabled - since the register pressure per _consumer_ warp group is reduced - and hence improving performance.

Since each thread block now computes multiple output tiles, the shape of the grid launch and the scheduling of tiles to the thread blocks is managed using the new [_Tile Scheduler_](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/kernel/sm90_tile_scheduler.hpp). The _Tile Scheduler_ considers the shape of the _clusters_ as well as the available number of available SMs to compute a valid scheduling of the output tiles to launched thread blocks.

**Warp-Specialized Persistent Ping-Pong kernel design**

The third kernel design is the [_Warp-Specialized Persistent Ping-Pong_](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/gemm/kernel/sm90_gemm_tma_warpspecialized_pingpong.hpp) kernel. Like the Warp-Specialized Persistent Cooperative, kernel the concepts of warp groups, barrier synchronization between warp groups, and the shape of the grid launch remain the same in the persistent ping-pong design. The distinctive feature of the Warp-Specialized Persistent Ping-Pong kernel is the following :

-   The two _consumer_ warp groups are assigned a different output tile using the Tile Scheduler. This allows for _epilogue_ of one _consumer_ warp group to be overlapped with the math operations of the other _consumer_ warp group - thus maximizing tensor core utilization.
-   The _producer_ warp group synchronizes using the [Ordered Sequence Barrier](https://github.com/NVIDIA/cutlass/tree/main/include/cutlass/pipeline/pipeline.hpp) to fill buffers of the two _consumer_ warp groups one after the other in order.

# Resources[#](https://docs.nvidia.com/cutlass/latest/media/docs/cpp/efficient_gemm.html#resources "Link to this heading")

The following additional resources describe design and implementation details of GEMMs targeting NVIDIA GPUs.

-   [Developing CUDA Kernels to Push Tensor Cores to the Absolute Limit on NVIDIA A100.](https://www.nvidia.com/en-us/gtc) (SR 21745)
-   [CUTLASS: Fast Linear Algebra in CUDA C++](https://devblogs.nvidia.com/cutlass-linear-algebra-cuda/)
-   [CUTLASS: SOFTWARE PRIMITIVES FOR DENSE LINEAR ALGEBRA AT ALL LEVELS AND SCALES WITHIN CUDA](https://on-demand-gtc.gputechconf.com/gtcnew/sessionview.php?sessionName=s8854-cutlass%3a+software+primitives+for+dense+linear+algebra+at+all+levels+and+scales+within+cuda)
-   [Programming Tensor Cores: NATIVE VOLTA TENSOR CORES WITH CUTLASS](https://developer.download.nvidia.com/video/gputechconf/gtc/2019/presentation/s9593-cutensor-high-performance-tensor-operations-in-cuda-v2.pdf)
-   [CUDA Programming Guide: warp matrix functions](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#wmma)
-   [Matrix Multiply Accumulate Instructions](https://docs.nvidia.com/cuda/parallel-thread-execution/index.html#warp-level-matrix-instructions-mma)