# CUDA Runtime API

[< Previous](structcudaEventWaitNodeParams.html) | [Next >](structcudaExternalMemoryBufferDesc.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.19. cudaExtent Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA extent


See also:


[make_cudaExtent](group__CUDART__MEMORY.html#group__CUDART__MEMORY_1g66d2e640656aa155d4ed6650fc7a2a5e)




### Public Variables


size_t  depthsize_t  heightsize_t  width

### Variables


size_t  cudaExtent::depth [inherited]
Depth in elements

size_t  cudaExtent::height [inherited]
Height in elements

size_t  cudaExtent::width [inherited]
Width in elements when referring to array memory, in bytes when referring to linear memory


---