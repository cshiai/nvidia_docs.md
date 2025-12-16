# CUDA Driver API

[< Previous](structCUDA__HOST__NODE__PARAMS__v2.html) | [Next >](structCUDA__KERNEL__NODE__PARAMS__v2.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.35. CUDA_KERNEL_NODE_PARAMS_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


GPU kernel node parameters


### Public Variables


unsigned int  blockDimXunsigned int  blockDimYunsigned int  blockDimZ* extraCUfunction funcunsigned int  gridDimXunsigned int  gridDimYunsigned int  gridDimZ* kernelParamsunsigned int  sharedMemBytes

### Variables


unsigned int  CUDA_KERNEL_NODE_PARAMS_v1::blockDimX [inherited]
X dimension of each thread block

unsigned int  CUDA_KERNEL_NODE_PARAMS_v1::blockDimY [inherited]
Y dimension of each thread block

unsigned int  CUDA_KERNEL_NODE_PARAMS_v1::blockDimZ [inherited]
Z dimension of each thread block

* CUDA_KERNEL_NODE_PARAMS_v1::extra [inherited]
Extra options

CUfunctionCUDA_KERNEL_NODE_PARAMS_v1::func [inherited]
Kernel to launch

unsigned int  CUDA_KERNEL_NODE_PARAMS_v1::gridDimX [inherited]
Width of grid in blocks

unsigned int  CUDA_KERNEL_NODE_PARAMS_v1::gridDimY [inherited]
Height of grid in blocks

unsigned int  CUDA_KERNEL_NODE_PARAMS_v1::gridDimZ [inherited]
Depth of grid in blocks

* CUDA_KERNEL_NODE_PARAMS_v1::kernelParams [inherited]
Array of pointers to kernel parameters

unsigned int  CUDA_KERNEL_NODE_PARAMS_v1::sharedMemBytes [inherited]
Dynamic shared-memory size per thread block in bytes


---