# CUDA Runtime API

[< Previous](structcudaMemPoolPtrExportData.html) | [Next >](structcudaMemsetParamsV2.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.58. cudaMemsetParams Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA Memset node parameters


### Public Variables


void
                           * dstunsigned int  elementSizesize_t  heightsize_t  pitchunsigned int  valuesize_t  width

### Variables


void
                              * cudaMemsetParams::dst [inherited]
Destination device pointer

unsigned int  cudaMemsetParams::elementSize [inherited]
Size of each element in bytes. Must be 1, 2, or 4.

size_t  cudaMemsetParams::height [inherited]
Number of rows

size_t  cudaMemsetParams::pitch [inherited]
Pitch of destination device pointer. Unused if height is 1

unsigned int  cudaMemsetParams::value [inherited]
Value to be set

size_t  cudaMemsetParams::width [inherited]
Width of the row in elements


---