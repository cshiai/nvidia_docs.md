# CUDA Driver API

[< Previous](structCUDA__MEMCPY__NODE__PARAMS.html) | [Next >](structCUDA__MEMSET__NODE__PARAMS__v2.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.46. CUDA_MEMSET_NODE_PARAMS_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Memset node parameters


### Public Variables


CUdeviceptr dstunsigned int  elementSizesize_t  heightsize_t  pitchunsigned int  valuesize_t  width

### Variables


CUdeviceptrCUDA_MEMSET_NODE_PARAMS_v1::dst [inherited]
Destination device pointer

unsigned int  CUDA_MEMSET_NODE_PARAMS_v1::elementSize [inherited]
Size of each element in bytes. Must be 1, 2, or 4.

size_t  CUDA_MEMSET_NODE_PARAMS_v1::height [inherited]
Number of rows

size_t  CUDA_MEMSET_NODE_PARAMS_v1::pitch [inherited]
Pitch of destination device pointer. Unused if height is 1

unsigned int  CUDA_MEMSET_NODE_PARAMS_v1::value [inherited]
Value to be set

size_t  CUDA_MEMSET_NODE_PARAMS_v1::width [inherited]
Width of the row in elements


---