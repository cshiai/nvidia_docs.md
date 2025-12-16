# CUDA Driver API

[< Previous](structCUcheckpointCheckpointArgs.html) | [Next >](structCUcheckpointLockArgs.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.6. CUcheckpointGpuPair Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


CUDA checkpoint GPU UUID pairs for device remapping during restore


### Public Variables


CUuuid  newUuidCUuuid  oldUuid

### Variables


CUuuid  CUcheckpointGpuPair::newUuid [inherited]
UUID of the GPU to restore onto

CUuuid  CUcheckpointGpuPair::oldUuid [inherited]
UUID of the GPU that was checkpointed


---