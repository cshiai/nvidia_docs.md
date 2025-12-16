# CUDA Runtime API

[< Previous](structcudaMemAllocNodeParams.html) | [Next >](structcudaMemcpy3DOperand.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.48. cudaMemAllocNodeParamsV2 Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Memory allocation node parameters


### Public Variables


size_t  accessDescCountcudaMemAccessDesc
                           * accessDescssize_t  bytesizevoid
                           * dptrstruct cudaMemPoolProps poolProps

### Variables


size_t  cudaMemAllocNodeParamsV2::accessDescCount [inherited]
in: Number of `accessDescs`s

cudaMemAccessDesc
                              * cudaMemAllocNodeParamsV2::accessDescs [inherited]
in: number of memory access descriptors. Must not exceed the number of GPUs.

size_t  cudaMemAllocNodeParamsV2::bytesize [inherited]
in: size in bytes of the requested allocation

void
                              * cudaMemAllocNodeParamsV2::dptr [inherited]
out: address of the allocation returned by CUDA

struct cudaMemPoolPropscudaMemAllocNodeParamsV2::poolProps [inherited]
in: location where the allocation should reside (specified in location). handleTypes must be cudaMemHandleTypeNone. IPC is not supported. in: array of memory access descriptors. Used to describe peer GPU access


---