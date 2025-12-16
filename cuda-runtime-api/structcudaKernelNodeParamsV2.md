# CUDA Runtime API

[< Previous](structcudaKernelNodeParams.html) | [Next >](structcudaLaunchAttribute.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.41. cudaKernelNodeParamsV2 Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA GPU kernel node parameters


### Public Variables


uint3  blockDimcudaExecutionContext_t ctx* extravoid
                           * funcuint3  gridDim* kernelParamsunsigned int  sharedMemBytes

### Variables


uint3  cudaKernelNodeParamsV2::blockDim [inherited]
Block dimensions

cudaExecutionContext_tcudaKernelNodeParamsV2::ctx [inherited]
Context in which to run the kernel. If NULL will try to use the current context.

* cudaKernelNodeParamsV2::extra [inherited]
Pointer to kernel arguments in the "extra" format

void
                              * cudaKernelNodeParamsV2::func [inherited]
Kernel to launch

uint3  cudaKernelNodeParamsV2::gridDim [inherited]
Grid dimensions

* cudaKernelNodeParamsV2::kernelParams [inherited]
Array of pointers to individual kernel arguments

unsigned int  cudaKernelNodeParamsV2::sharedMemBytes [inherited]
Dynamic shared-memory size per thread block in bytes


---