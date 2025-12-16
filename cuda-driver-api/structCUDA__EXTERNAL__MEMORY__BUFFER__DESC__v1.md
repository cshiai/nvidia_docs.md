# CUDA Driver API

[< Previous](structCUDA__EXT__SEM__WAIT__NODE__PARAMS__v2.html) | [Next >](structCUDA__EXTERNAL__MEMORY__HANDLE__DESC__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.26. CUDA_EXTERNAL_MEMORY_BUFFER_DESC_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


External memory buffer descriptor


### Public Variables


unsigned int  flagsunsigned long long  offsetunsigned long long  size

### Variables


unsigned int  CUDA_EXTERNAL_MEMORY_BUFFER_DESC_v1::flags [inherited]
Flags reserved for future use. Must be zero.

unsigned long long  CUDA_EXTERNAL_MEMORY_BUFFER_DESC_v1::offset [inherited]
Offset into the memory object where the buffer's base is

unsigned long long  CUDA_EXTERNAL_MEMORY_BUFFER_DESC_v1::size [inherited]
Size of the buffer


---