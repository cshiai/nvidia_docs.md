# CUDA Runtime API

[< Previous](structcudaExtent.html) | [Next >](structcudaExternalMemoryHandleDesc.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.20. cudaExternalMemoryBufferDesc Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


External memory buffer descriptor


### Public Variables


unsigned int  flagsunsigned long long  offsetunsigned int  reserved[16]unsigned long long  size

### Variables


unsigned int  cudaExternalMemoryBufferDesc::flags [inherited]
Flags reserved for future use. Must be zero.

unsigned long long  cudaExternalMemoryBufferDesc::offset [inherited]
Offset into the memory object where the buffer's base is

unsigned int  cudaExternalMemoryBufferDesc::reserved[16] [inherited]
Must be zero

unsigned long long  cudaExternalMemoryBufferDesc::size [inherited]
Size of the buffer


---