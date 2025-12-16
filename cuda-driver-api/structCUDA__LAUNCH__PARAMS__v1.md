# CUDA Driver API

[< Previous](structCUDA__KERNEL__NODE__PARAMS__v3.html) | [Next >](structCUDA__MEM__ALLOC__NODE__PARAMS__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.38. CUDA_LAUNCH_PARAMS_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Kernel launch parameters


### Public Variables


unsigned int  blockDimXunsigned int  blockDimYunsigned int  blockDimZCUfunction functionunsigned int  gridDimXunsigned int  gridDimYunsigned int  gridDimZCUstream hStream* kernelParamsunsigned int  sharedMemBytes

### Variables


unsigned int  CUDA_LAUNCH_PARAMS_v1::blockDimX [inherited]
X dimension of each thread block

unsigned int  CUDA_LAUNCH_PARAMS_v1::blockDimY [inherited]
Y dimension of each thread block

unsigned int  CUDA_LAUNCH_PARAMS_v1::blockDimZ [inherited]
Z dimension of each thread block

CUfunctionCUDA_LAUNCH_PARAMS_v1::function [inherited]
Kernel to launch

unsigned int  CUDA_LAUNCH_PARAMS_v1::gridDimX [inherited]
Width of grid in blocks

unsigned int  CUDA_LAUNCH_PARAMS_v1::gridDimY [inherited]
Height of grid in blocks

unsigned int  CUDA_LAUNCH_PARAMS_v1::gridDimZ [inherited]
Depth of grid in blocks

CUstreamCUDA_LAUNCH_PARAMS_v1::hStream [inherited]
Stream identifier

* CUDA_LAUNCH_PARAMS_v1::kernelParams [inherited]
Array of pointers to kernel parameters

unsigned int  CUDA_LAUNCH_PARAMS_v1::sharedMemBytes [inherited]
Dynamic shared-memory size per thread block in bytes


---