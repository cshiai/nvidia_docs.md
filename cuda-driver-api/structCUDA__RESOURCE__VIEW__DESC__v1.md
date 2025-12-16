# CUDA Driver API

[< Previous](structCUDA__RESOURCE__DESC__v1.html) | [Next >](structCUDA__TEXTURE__DESC__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.50. CUDA_RESOURCE_VIEW_DESC_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Resource view descriptor


### Public Variables


size_t  depthunsigned int  firstLayerunsigned int  firstMipmapLevelCUresourceViewFormat formatsize_t  heightunsigned int  lastLayerunsigned int  lastMipmapLevelsize_t  width

### Variables


size_t  CUDA_RESOURCE_VIEW_DESC_v1::depth [inherited]
Depth of the resource view

unsigned int  CUDA_RESOURCE_VIEW_DESC_v1::firstLayer [inherited]
First layer index

unsigned int  CUDA_RESOURCE_VIEW_DESC_v1::firstMipmapLevel [inherited]
First defined mipmap level

CUresourceViewFormatCUDA_RESOURCE_VIEW_DESC_v1::format [inherited]
Resource view format

size_t  CUDA_RESOURCE_VIEW_DESC_v1::height [inherited]
Height of the resource view

unsigned int  CUDA_RESOURCE_VIEW_DESC_v1::lastLayer [inherited]
Last layer index

unsigned int  CUDA_RESOURCE_VIEW_DESC_v1::lastMipmapLevel [inherited]
Last defined mipmap level

size_t  CUDA_RESOURCE_VIEW_DESC_v1::width [inherited]
Width of the resource view


---