# CUDA Driver API

[< Previous](structCUDA__MEMSET__NODE__PARAMS__v1.html) | [Next >](structCUDA__POINTER__ATTRIBUTE__P2P__TOKENS__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.47. CUDA_MEMSET_NODE_PARAMS_v2 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Memset node parameters


### Public Variables


CUcontext ctxCUdeviceptr dstunsigned int  elementSizesize_t  heightsize_t  pitchunsigned int  valuesize_t  width

### Variables


CUcontextCUDA_MEMSET_NODE_PARAMS_v2::ctx [inherited]
Context on which to run the node

CUdeviceptrCUDA_MEMSET_NODE_PARAMS_v2::dst [inherited]
Destination device pointer

unsigned int  CUDA_MEMSET_NODE_PARAMS_v2::elementSize [inherited]
Size of each element in bytes. Must be 1, 2, or 4.

size_t  CUDA_MEMSET_NODE_PARAMS_v2::height [inherited]
Number of rows

size_t  CUDA_MEMSET_NODE_PARAMS_v2::pitch [inherited]
Pitch of destination device pointer. Unused if height is 1

unsigned int  CUDA_MEMSET_NODE_PARAMS_v2::value [inherited]
Value to be set

size_t  CUDA_MEMSET_NODE_PARAMS_v2::width [inherited]
Width of the row in elements


---