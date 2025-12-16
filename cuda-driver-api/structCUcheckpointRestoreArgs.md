# CUDA Driver API

[< Previous](structCUcheckpointLockArgs.html) | [Next >](structCUcheckpointUnlockArgs.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.8. CUcheckpointRestoreArgs Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


CUDA checkpoint optional restore arguments


### Public Variables


CUcheckpointGpuPair
                           * gpuPairsunsigned int  gpuPairsCountchar  reserved[52-sizeof(CUcheckpointGpuPair *)]cuuint64_t  reserved1

### Variables


CUcheckpointGpuPair
                              * CUcheckpointRestoreArgs::gpuPairs [inherited]
Pointer to array of gpu pairs that indicate how to remap GPUs during restore

unsigned int  CUcheckpointRestoreArgs::gpuPairsCount [inherited]
Number of gpu pairs to remap

char  CUcheckpointRestoreArgs::reserved[52-sizeof(CUcheckpointGpuPair *)] [inherited]
Reserved for future use, must be zeroed

cuuint64_t  CUcheckpointRestoreArgs::reserved1 [inherited]
Reserved for future use, must be zeroed


---