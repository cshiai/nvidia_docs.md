# CUDA Runtime API

[< Previous](structcudaMemsetParams.html) | [Next >](structcudaOffset3D.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.59. cudaMemsetParamsV2 Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA Memset node parameters


### Public Variables


cudaExecutionContext_t ctxvoid
                           * dstunsigned int  elementSizesize_t  heightsize_t  pitchunsigned int  valuesize_t  width

### Variables


cudaExecutionContext_tcudaMemsetParamsV2::ctx [inherited]
Context in which to run the memset. If NULL will try to use the current context.

void
                              * cudaMemsetParamsV2::dst [inherited]
Destination device pointer

unsigned int  cudaMemsetParamsV2::elementSize [inherited]
Size of each element in bytes. Must be 1, 2, or 4.

size_t  cudaMemsetParamsV2::height [inherited]
Number of rows

size_t  cudaMemsetParamsV2::pitch [inherited]
Pitch of destination device pointer. Unused if height is 1

unsigned int  cudaMemsetParamsV2::value [inherited]
Value to be set

size_t  cudaMemsetParamsV2::width [inherited]
Width of the row in elements


---