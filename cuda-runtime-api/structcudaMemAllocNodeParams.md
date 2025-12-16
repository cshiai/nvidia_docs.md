# CUDA Runtime API

[< Previous](structcudaMemAccessDesc.html) | [Next >](structcudaMemAllocNodeParamsV2.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.47. cudaMemAllocNodeParams Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Memory allocation node parameters


### Public Variables


size_t  accessDescCountcudaMemAccessDesc
                           * accessDescssize_t  bytesizevoid
                           * dptrstruct cudaMemPoolProps poolProps

### Variables


size_t  cudaMemAllocNodeParams::accessDescCount [inherited]
in: Number of `accessDescs`s

cudaMemAccessDesc
                              * cudaMemAllocNodeParams::accessDescs [inherited]
in: number of memory access descriptors. Must not exceed the number of GPUs.

size_t  cudaMemAllocNodeParams::bytesize [inherited]
in: size in bytes of the requested allocation

void
                              * cudaMemAllocNodeParams::dptr [inherited]
out: address of the allocation returned by CUDA

struct cudaMemPoolPropscudaMemAllocNodeParams::poolProps [inherited]
in: location where the allocation should reside (specified in location). handleTypes must be cudaMemHandleTypeNone. IPC is not supported. in: array of memory access descriptors. Used to describe peer GPU access


---