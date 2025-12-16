# CUDA Runtime API

[< Previous](structcudaPos.html) | [Next >](structcudaResourceViewDesc.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.64. cudaResourceDesc Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA resource descriptor


### Public Variables


cudaArray_t arraystruct cudaChannelFormatDesc descvoid
                           * devPtrunsigned int  flagssize_t  heightcudaMipmappedArray_t mipmapsize_t  pitchInBytesenumcudaResourceType resTypesize_t  sizeInBytessize_t  width

### Variables


cudaArray_tcudaResourceDesc::array [inherited]
CUDA array

struct cudaChannelFormatDesccudaResourceDesc::desc [inherited]
Channel descriptor

void
                              * cudaResourceDesc::devPtr [inherited]
Device pointer

unsigned int  cudaResourceDesc::flags [inherited]
Flags (must be zero)

size_t  cudaResourceDesc::height [inherited]
Height of the array in elements

cudaMipmappedArray_tcudaResourceDesc::mipmap [inherited]
CUDA mipmapped array

size_t  cudaResourceDesc::pitchInBytes [inherited]
Pitch between two rows in bytes

enumcudaResourceTypecudaResourceDesc::resType [inherited]
Resource type

size_t  cudaResourceDesc::sizeInBytes [inherited]
Size in bytes

size_t  cudaResourceDesc::width [inherited]
Width of the array in elements


---