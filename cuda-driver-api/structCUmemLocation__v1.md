# CUDA Driver API

[< Previous](structCUmemFabricHandle__v1.html) | [Next >](structCUmemPoolProps__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.76. CUmemLocation_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Specifies a memory location.


### Public Variables


int  idCUmemLocationType type

### Variables


int  CUmemLocation_v1::id [inherited]
identifier for a given this location's CUmemLocationType.

CUmemLocationTypeCUmemLocation_v1::type [inherited]
Specifies the location type, which modifies the meaning of id.


---