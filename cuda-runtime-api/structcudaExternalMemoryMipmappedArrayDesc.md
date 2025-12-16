# CUDA Runtime API

[< Previous](structcudaExternalMemoryHandleDesc.html) | [Next >](structcudaExternalSemaphoreHandleDesc.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.22. cudaExternalMemoryMipmappedArrayDesc Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


External memory mipmap descriptor


### Public Variables


struct cudaExtent extentunsigned int  flagsstruct cudaChannelFormatDesc formatDescunsigned int  numLevelsunsigned long long  offsetunsigned int  reserved[16]

### Variables


struct cudaExtentcudaExternalMemoryMipmappedArrayDesc::extent [inherited]
Dimensions of base level of the mipmap chain

unsigned int  cudaExternalMemoryMipmappedArrayDesc::flags [inherited]
Flags associated with CUDA mipmapped arrays. See cudaMallocMipmappedArray

struct cudaChannelFormatDesccudaExternalMemoryMipmappedArrayDesc::formatDesc [inherited]
Format of base level of the mipmap chain

unsigned int  cudaExternalMemoryMipmappedArrayDesc::numLevels [inherited]
Total number of levels in the mipmap chain

unsigned long long  cudaExternalMemoryMipmappedArrayDesc::offset [inherited]
Offset into the memory object where the base level of the mipmap chain is.

unsigned int  cudaExternalMemoryMipmappedArrayDesc::reserved[16] [inherited]
Must be zero


---