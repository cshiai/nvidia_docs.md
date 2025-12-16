# CUDA Driver API

[< Previous](structCUDA__ARRAY__MEMORY__REQUIREMENTS__v1.html) | [Next >](structCUDA__BATCH__MEM__OP__NODE__PARAMS__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.15. CUDA_ARRAY_SPARSE_PROPERTIES_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


CUDA array sparse properties


### Public Variables


unsigned int  depthunsigned int  flagsunsigned int  heightunsigned int  miptailFirstLevelunsigned long long  miptailSizeunsigned int  width

### Variables


unsigned int  CUDA_ARRAY_SPARSE_PROPERTIES_v1::depth [inherited]
Depth of sparse tile in elements

unsigned int  CUDA_ARRAY_SPARSE_PROPERTIES_v1::flags [inherited]
Flags will either be zero or CU_ARRAY_SPARSE_PROPERTIES_SINGLE_MIPTAIL

unsigned int  CUDA_ARRAY_SPARSE_PROPERTIES_v1::height [inherited]
Height of sparse tile in elements

unsigned int  CUDA_ARRAY_SPARSE_PROPERTIES_v1::miptailFirstLevel [inherited]
First mip level at which the mip tail begins.

unsigned long long  CUDA_ARRAY_SPARSE_PROPERTIES_v1::miptailSize [inherited]
Total size of the mip tail.

unsigned int  CUDA_ARRAY_SPARSE_PROPERTIES_v1::width [inherited]
Width of sparse tile in elements


---