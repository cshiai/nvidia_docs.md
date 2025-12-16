# CUDA Driver API

[< Previous](structCUDA__KERNEL__NODE__PARAMS__v2.html) | [Next >](structCUDA__LAUNCH__PARAMS__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.37. CUDA_KERNEL_NODE_PARAMS_v3 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


GPU kernel node parameters


### Public Variables


unsigned int  blockDimXunsigned int  blockDimYunsigned int  blockDimZCUcontext ctx* extraCUfunction funcunsigned int  gridDimXunsigned int  gridDimYunsigned int  gridDimZCUkernel kern* kernelParamsunsigned int  sharedMemBytes

### Variables


unsigned int  CUDA_KERNEL_NODE_PARAMS_v3::blockDimX [inherited]
X dimension of each thread block

unsigned int  CUDA_KERNEL_NODE_PARAMS_v3::blockDimY [inherited]
Y dimension of each thread block

unsigned int  CUDA_KERNEL_NODE_PARAMS_v3::blockDimZ [inherited]
Z dimension of each thread block

CUcontextCUDA_KERNEL_NODE_PARAMS_v3::ctx [inherited]
Context for the kernel task to run in. The value NULL will indicate the current context should be used by the api. This field
                                 is ignored if func is set.

* CUDA_KERNEL_NODE_PARAMS_v3::extra [inherited]
Extra options

CUfunctionCUDA_KERNEL_NODE_PARAMS_v3::func [inherited]
Kernel to launch

unsigned int  CUDA_KERNEL_NODE_PARAMS_v3::gridDimX [inherited]
Width of grid in blocks

unsigned int  CUDA_KERNEL_NODE_PARAMS_v3::gridDimY [inherited]
Height of grid in blocks

unsigned int  CUDA_KERNEL_NODE_PARAMS_v3::gridDimZ [inherited]
Depth of grid in blocks

CUkernelCUDA_KERNEL_NODE_PARAMS_v3::kern [inherited]
Kernel to launch, will only be referenced if func is NULL

* CUDA_KERNEL_NODE_PARAMS_v3::kernelParams [inherited]
Array of pointers to kernel parameters

unsigned int  CUDA_KERNEL_NODE_PARAMS_v3::sharedMemBytes [inherited]
Dynamic shared-memory size per thread block in bytes


---