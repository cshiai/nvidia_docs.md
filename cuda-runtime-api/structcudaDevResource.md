# CUDA Runtime API

[< Previous](structcudaDeviceProp.html) | [Next >](structcudaDevSmResource.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.10. cudaDevResource Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


A tagged union describing different resources identified by the type field. This structure should not be directly modified outside of the API that created it.


```
‎ struct {
           enum cudaDevResourceType
               type;
           union {
               struct cudaDevSmResource
               sm;
               struct cudaDevWorkqueueConfigResource
               wqConfig;
               struct cudaDevWorkqueueResource
               wq;
           };
       };
```


 - If type is cudaDevResourceTypeInvalid, this resoure is not valid and cannot be further accessed.
 - If type is cudaDevResourceTypeSm, the [cudaDevSmResource](structcudaDevSmResource.html#structcudaDevSmResource) structure sm is filled in. For example, sm.smCount will reflect the amount of streaming multiprocessors available in this resource.
 - If type is cudaDevResourceTypeWorkqueueConfig, the [cudaDevWorkqueueConfigResource](structcudaDevWorkqueueConfigResource.html#structcudaDevWorkqueueConfigResource) structure wqConfig is filled in.
 - If type is cudaDevResourceTypeWorkqueue, the [cudaDevWorkqueueResource](structcudaDevWorkqueueResource.html#structcudaDevWorkqueueResource) structure wq is filled in.


### Public Variables


struct cudaDevSmResource smenumcudaDevResourceType typestruct cudaDevWorkqueueResource wqstruct cudaDevWorkqueueConfigResource wqConfig

### Variables


struct cudaDevSmResourcecudaDevResource::sm [inherited]
Resource corresponding to cudaDevResourceTypeSm type.

enumcudaDevResourceTypecudaDevResource::type [inherited]
Type of resource, dictates which union field was last set

struct cudaDevWorkqueueResourcecudaDevResource::wq [inherited]
Resource corresponding to cudaDevResourceTypeWorkqueue type.

struct cudaDevWorkqueueConfigResourcecudaDevResource::wqConfig [inherited]
Resource corresponding to cudaDevResourceTypeWorkqueueConfig type.


---