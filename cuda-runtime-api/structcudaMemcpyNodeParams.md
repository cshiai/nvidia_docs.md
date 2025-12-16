# CUDA Runtime API

[< Previous](structcudaMemcpyAttributes.html) | [Next >](structcudaMemFreeNodeParams.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.53. cudaMemcpyNodeParams Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Memcpy node parameters


### Public Variables


struct cudaMemcpy3DParms copyParamscudaExecutionContext_t ctxint  flagsint  reserved

### Variables


struct cudaMemcpy3DParmscudaMemcpyNodeParams::copyParams [inherited]
Parameters for the memory copy

cudaExecutionContext_tcudaMemcpyNodeParams::ctx [inherited]
Context in which to run the memcpy. If NULL will try to use the current context.

int  cudaMemcpyNodeParams::flags [inherited]
Must be zero

int  cudaMemcpyNodeParams::reserved [inherited]
Must be zero


---