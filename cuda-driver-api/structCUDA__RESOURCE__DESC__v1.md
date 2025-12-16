# CUDA Driver API

[< Previous](structCUDA__POINTER__ATTRIBUTE__P2P__TOKENS__v1.html) | [Next >](structCUDA__RESOURCE__VIEW__DESC__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.49. CUDA_RESOURCE_DESC_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


CUDA Resource descriptor


### Public Variables


CUdeviceptr devPtrunsigned int  flagsCUarray_format formatCUarray hArrayCUmipmappedArray hMipmappedArraysize_t  heightunsigned int  numChannelssize_t  pitchInBytesCUresourcetype resTypesize_t  sizeInBytessize_t  width

### Variables


CUdeviceptrCUDA_RESOURCE_DESC_v1::devPtr [inherited]
Device pointer

unsigned int  CUDA_RESOURCE_DESC_v1::flags [inherited]
Flags (must be zero)

CUarray_formatCUDA_RESOURCE_DESC_v1::format [inherited]
Array format

CUarrayCUDA_RESOURCE_DESC_v1::hArray [inherited]
CUDA array

CUmipmappedArrayCUDA_RESOURCE_DESC_v1::hMipmappedArray [inherited]
CUDA mipmapped array

size_t  CUDA_RESOURCE_DESC_v1::height [inherited]
Height of the array in elements

unsigned int  CUDA_RESOURCE_DESC_v1::numChannels [inherited]
Channels per array element

size_t  CUDA_RESOURCE_DESC_v1::pitchInBytes [inherited]
Pitch between two rows in bytes

CUresourcetypeCUDA_RESOURCE_DESC_v1::resType [inherited]
Resource type

size_t  CUDA_RESOURCE_DESC_v1::sizeInBytes [inherited]
Size in bytes

size_t  CUDA_RESOURCE_DESC_v1::width [inherited]
Width of the array in elements


---