# CUDA Runtime API

[< Previous](structcudaArrayMemoryRequirements.html) | [Next >](structcudaAsyncNotificationInfo__t.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.4. cudaArraySparseProperties Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Sparse CUDA array and CUDA mipmapped array properties


### Public Variables


unsigned int  depthunsigned int  flagsunsigned int  heightunsigned int  miptailFirstLevelunsigned long long  miptailSizeunsigned int  width

### Variables


unsigned int  cudaArraySparseProperties::depth [inherited]
Tile depth in elements

unsigned int  cudaArraySparseProperties::flags [inherited]
Flags will either be zero or cudaArraySparsePropertiesSingleMipTail

unsigned int  cudaArraySparseProperties::height [inherited]
Tile height in elements

unsigned int  cudaArraySparseProperties::miptailFirstLevel [inherited]
First mip level at which the mip tail begins

unsigned long long  cudaArraySparseProperties::miptailSize [inherited]
Total size of the mip tail.

unsigned int  cudaArraySparseProperties::width [inherited]
Tile width in elements


---