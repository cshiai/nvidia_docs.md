# CUDA Driver API

[< Previous](structCUDA__MEMCPY3D__v2.html) | [Next >](structCUDA__MEMSET__NODE__PARAMS__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.45. CUDA_MEMCPY_NODE_PARAMS Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Memcpy node parameters


### Public Variables


CUcontext copyCtxstruct CUDA_MEMCPY3D copyParamsint  flagsint  reserved

### Variables


CUcontextCUDA_MEMCPY_NODE_PARAMS::copyCtx [inherited]
Context on which to run the node

struct CUDA_MEMCPY3DCUDA_MEMCPY_NODE_PARAMS::copyParams [inherited]
Parameters for the memory copy

int  CUDA_MEMCPY_NODE_PARAMS::flags [inherited]
Must be zero

int  CUDA_MEMCPY_NODE_PARAMS::reserved [inherited]
Must be zero


---