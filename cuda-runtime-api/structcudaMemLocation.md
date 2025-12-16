# CUDA Runtime API

[< Previous](structcudaMemFreeNodeParams.html) | [Next >](structcudaMemPoolProps.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.55. cudaMemLocation Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Specifies a memory location.


To specify a gpu, set type = [cudaMemLocationTypeDevice](group__CUDART__TYPES.html#group__CUDART__TYPES_1gg2279aa08666f329f3ba4afe397fa60f0e479b8710f3c5270117ee9d8cf5868d4) and set id = the gpu's device ordinal. To specify a cpu NUMA node, set type = [cudaMemLocationTypeHostNuma](group__CUDART__TYPES.html#group__CUDART__TYPES_1gg2279aa08666f329f3ba4afe397fa60f024dc63fb938dee27b41e3842da35d2d0) and set id = host NUMA node id.


### Public Variables


int  idenumcudaMemLocationType type

### Variables


int  cudaMemLocation::id [inherited]
identifier for a given this location's CUmemLocationType.

enumcudaMemLocationTypecudaMemLocation::type [inherited]
Specifies the location type, which modifies the meaning of id.


---