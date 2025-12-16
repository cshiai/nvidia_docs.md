# CUDA Driver API

[< Previous](unionCUlaunchAttributeValue.html) | [Next >](structCUlaunchMemSyncDomainMap.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.68. CUlaunchConfig Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


CUDA extensible launch configuration


### Public Variables


CUlaunchAttribute
                           * attrsunsigned int  blockDimXunsigned int  blockDimYunsigned int  blockDimZunsigned int  gridDimXunsigned int  gridDimYunsigned int  gridDimZCUstream hStreamunsigned int  numAttrsunsigned int  sharedMemBytes

### Variables


CUlaunchAttribute
                              * CUlaunchConfig::attrs [inherited]
List of attributes; nullable if CUlaunchConfig::numAttrs == 0

unsigned int  CUlaunchConfig::blockDimX [inherited]
X dimension of each thread block

unsigned int  CUlaunchConfig::blockDimY [inherited]
Y dimension of each thread block

unsigned int  CUlaunchConfig::blockDimZ [inherited]
Z dimension of each thread block

unsigned int  CUlaunchConfig::gridDimX [inherited]
Width of grid in blocks

unsigned int  CUlaunchConfig::gridDimY [inherited]
Height of grid in blocks

unsigned int  CUlaunchConfig::gridDimZ [inherited]
Depth of grid in blocks

CUstreamCUlaunchConfig::hStream [inherited]
Stream identifier

unsigned int  CUlaunchConfig::numAttrs [inherited]
Number of attributes populated in CUlaunchConfig::attrs

unsigned int  CUlaunchConfig::sharedMemBytes [inherited]
Dynamic shared-memory size per thread block in bytes


---