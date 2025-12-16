# CUDA Runtime API

[< Previous](structcudaIpcMemHandle__t.html) | [Next >](structcudaKernelNodeParamsV2.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.40. cudaKernelNodeParams Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA GPU kernel node parameters


### Public Variables


dim3  blockDim* extravoid
                           * funcdim3  gridDim* kernelParamsunsigned int  sharedMemBytes

### Variables


dim3  cudaKernelNodeParams::blockDim [inherited]
Block dimensions

* cudaKernelNodeParams::extra [inherited]
Pointer to kernel arguments in the "extra" format

void
                              * cudaKernelNodeParams::func [inherited]
Kernel to launch

dim3  cudaKernelNodeParams::gridDim [inherited]
Grid dimensions

* cudaKernelNodeParams::kernelParams [inherited]
Array of pointers to individual kernel arguments

unsigned int  cudaKernelNodeParams::sharedMemBytes [inherited]
Dynamic shared-memory size per thread block in bytes


---