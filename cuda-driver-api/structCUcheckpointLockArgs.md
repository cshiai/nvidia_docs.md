# CUDA Driver API

[< Previous](structCUcheckpointGpuPair.html) | [Next >](structCUcheckpointRestoreArgs.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.7. CUcheckpointLockArgs Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


CUDA checkpoint optional lock arguments


### Public Variables


unsigned int  reserved0cuuint64_t  reserved1[7]unsigned int  timeoutMs

### Variables


unsigned int  CUcheckpointLockArgs::reserved0 [inherited]
Reserved for future use, must be zero

cuuint64_t  CUcheckpointLockArgs::reserved1[7] [inherited]
Reserved for future use, must be zeroed

unsigned int  CUcheckpointLockArgs::timeoutMs [inherited]
Timeout in milliseconds to attempt to lock the process, 0 indicates no timeout


---