# CUDA Runtime API

[< Previous](unioncudaLaunchAttributeValue.html) | [Next >](structcudaLaunchMemSyncDomainMap.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.44. cudaLaunchConfig_t Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA extensible launch configuration


### Public Variables


cudaLaunchAttribute
                           * attrsdim3  blockDimsize_t  dynamicSmemBytesdim3  gridDimunsigned int  numAttrscudaStream_t stream

### Variables


cudaLaunchAttribute
                              * cudaLaunchConfig_t::attrs [inherited]
List of attributes; nullable if cudaLaunchConfig_t::numAttrs == 0

dim3  cudaLaunchConfig_t::blockDim [inherited]
Block dimensions

size_t  cudaLaunchConfig_t::dynamicSmemBytes [inherited]
Dynamic shared-memory size per thread block in bytes

dim3  cudaLaunchConfig_t::gridDim [inherited]
Grid dimensions

unsigned int  cudaLaunchConfig_t::numAttrs [inherited]
Number of attributes populated in cudaLaunchConfig_t::attrs

cudaStream_tcudaLaunchConfig_t::stream [inherited]
Stream identifier


---