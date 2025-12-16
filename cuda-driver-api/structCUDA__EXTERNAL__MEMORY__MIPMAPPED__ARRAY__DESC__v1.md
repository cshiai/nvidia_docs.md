# CUDA Driver API

[< Previous](structCUDA__EXTERNAL__MEMORY__HANDLE__DESC__v1.html) | [Next >](structCUDA__EXTERNAL__SEMAPHORE__HANDLE__DESC__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.28. CUDA_EXTERNAL_MEMORY_MIPMAPPED_ARRAY_DESC_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


External memory mipmap descriptor


### Public Variables


struct CUDA_ARRAY3D_DESCRIPTOR arrayDescunsigned int  numLevelsunsigned long long  offset

### Variables


struct CUDA_ARRAY3D_DESCRIPTORCUDA_EXTERNAL_MEMORY_MIPMAPPED_ARRAY_DESC_v1::arrayDesc [inherited]
Format, dimension and type of base level of the mipmap chain

unsigned int  CUDA_EXTERNAL_MEMORY_MIPMAPPED_ARRAY_DESC_v1::numLevels [inherited]
Total number of levels in the mipmap chain

unsigned long long  CUDA_EXTERNAL_MEMORY_MIPMAPPED_ARRAY_DESC_v1::offset [inherited]
Offset into the memory object where the base level of the mipmap chain is.


---