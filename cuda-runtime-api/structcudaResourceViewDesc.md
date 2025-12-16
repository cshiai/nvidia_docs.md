# CUDA Runtime API

[< Previous](structcudaResourceDesc.html) | [Next >](structcudaTextureDesc.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.65. cudaResourceViewDesc Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA resource view descriptor


### Public Variables


size_t  depthunsigned int  firstLayerunsigned int  firstMipmapLevelenumcudaResourceViewFormat formatsize_t  heightunsigned int  lastLayerunsigned int  lastMipmapLevelunsigned int  reserved[16]size_t  width

### Variables


size_t  cudaResourceViewDesc::depth [inherited]
Depth of the resource view

unsigned int  cudaResourceViewDesc::firstLayer [inherited]
First layer index

unsigned int  cudaResourceViewDesc::firstMipmapLevel [inherited]
First defined mipmap level

enumcudaResourceViewFormatcudaResourceViewDesc::format [inherited]
Resource view format

size_t  cudaResourceViewDesc::height [inherited]
Height of the resource view

unsigned int  cudaResourceViewDesc::lastLayer [inherited]
Last layer index

unsigned int  cudaResourceViewDesc::lastMipmapLevel [inherited]
Last defined mipmap level

unsigned int  cudaResourceViewDesc::reserved[16] [inherited]
Must be zero

size_t  cudaResourceViewDesc::width [inherited]
Width of the resource view


---