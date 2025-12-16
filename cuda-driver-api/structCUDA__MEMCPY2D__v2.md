# CUDA Driver API

[< Previous](structCUDA__MEM__FREE__NODE__PARAMS.html) | [Next >](structCUDA__MEMCPY3D__PEER__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.42. CUDA_MEMCPY2D_v2 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


2D memory copy parameters


### Public Variables


size_t  Heightsize_t  WidthInBytesCUarray dstArrayCUdeviceptr dstDevicevoid
                           * dstHostCUmemorytype dstMemoryTypesize_t  dstPitchsize_t  dstXInBytessize_t  dstYCUarray srcArrayCUdeviceptr srcDeviceconst
                           void
                           * srcHostCUmemorytype srcMemoryTypesize_t  srcPitchsize_t  srcXInBytessize_t  srcY

### Variables


size_t  CUDA_MEMCPY2D_v2::Height [inherited]
Height of 2D memory copy

size_t  CUDA_MEMCPY2D_v2::WidthInBytes [inherited]
Width of 2D memory copy in bytes

CUarrayCUDA_MEMCPY2D_v2::dstArray [inherited]
Destination array reference

CUdeviceptrCUDA_MEMCPY2D_v2::dstDevice [inherited]
Destination device pointer

void
                              * CUDA_MEMCPY2D_v2::dstHost [inherited]
Destination host pointer

CUmemorytypeCUDA_MEMCPY2D_v2::dstMemoryType [inherited]
Destination memory type (host, device, array)

size_t  CUDA_MEMCPY2D_v2::dstPitch [inherited]
Destination pitch (ignored when dst is array)

size_t  CUDA_MEMCPY2D_v2::dstXInBytes [inherited]
Destination X in bytes

size_t  CUDA_MEMCPY2D_v2::dstY [inherited]
Destination Y

CUarrayCUDA_MEMCPY2D_v2::srcArray [inherited]
Source array reference

CUdeviceptrCUDA_MEMCPY2D_v2::srcDevice [inherited]
Source device pointer

const

                              void
                              * CUDA_MEMCPY2D_v2::srcHost [inherited]
Source host pointer

CUmemorytypeCUDA_MEMCPY2D_v2::srcMemoryType [inherited]
Source memory type (host, device, array)

size_t  CUDA_MEMCPY2D_v2::srcPitch [inherited]
Source pitch (ignored when src is array)

size_t  CUDA_MEMCPY2D_v2::srcXInBytes [inherited]
Source X in bytes

size_t  CUDA_MEMCPY2D_v2::srcY [inherited]
Source Y


---