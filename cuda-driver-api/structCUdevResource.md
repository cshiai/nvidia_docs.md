# CUDA Driver API

[< Previous](structCUdevprop__v1.html) | [Next >](structCUdevSmResource.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.53. CUdevResource Struct Reference


## [[Green Contexts](group__CUDA__GREEN__CONTEXTS.html#group__CUDA__GREEN__CONTEXTS)]


A tagged union describing different resources identified by the type field. This structure should not be directly modified outside of the API that created it.


```
‎ struct {
           CUdevResourceType type;
           union {
               CUdevSmResource sm;
                 CUdevWorkqueueConfigResource wqConfig;
                 CUdevWorkqueueResource wq;
           };
       };
```


 - If type is CU_DEV_RESOURCE_TYPE_INVALID, this resoure is not valid and cannot be further accessed.
 - If type is CU_DEV_RESOURCE_TYPE_SM, the [CUdevSmResource](structCUdevSmResource.html#structCUdevSmResource) structure sm is filled in. For example, sm.smCount will reflect the amount of streaming multiprocessors available in this resource.
 - If type is CU_DEV_RESOURCE_TYPE_WORKQUEUE_CONFIG, the [CUdevWorkqueueConfigResource](structCUdevWorkqueueConfigResource.html#structCUdevWorkqueueConfigResource) structure wqConfig is filled in.
 - If type is CU_DEV_RESOURCE_TYPE_WORKQUEUE, the [CUdevWorkqueueResource](structCUdevWorkqueueResource.html#structCUdevWorkqueueResource) structure wq is filled in.


---