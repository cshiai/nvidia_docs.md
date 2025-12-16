# CUDA Driver API

[< Previous](structCUDA__MEMCPY3D__PEER__v1.html) | [Next >](structCUDA__MEMCPY__NODE__PARAMS.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.44. CUDA_MEMCPY3D_v2 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


3D memory copy parameters


### Public Variables


size_t  Depthsize_t  Heightsize_t  WidthInBytesCUarray dstArrayCUdeviceptr dstDevicesize_t  dstHeightvoid
                           * dstHostsize_t  dstLODCUmemorytype dstMemoryTypesize_t  dstPitchsize_t  dstXInBytessize_t  dstYsize_t  dstZvoid
                           * reserved0void
                           * reserved1CUarray srcArrayCUdeviceptr srcDevicesize_t  srcHeightconst
                           void
                           * srcHostsize_t  srcLODCUmemorytype srcMemoryTypesize_t  srcPitchsize_t  srcXInBytessize_t  srcYsize_t  srcZ

### Variables


size_t  CUDA_MEMCPY3D_v2::Depth [inherited]
Depth of 3D memory copy

size_t  CUDA_MEMCPY3D_v2::Height [inherited]
Height of 3D memory copy

size_t  CUDA_MEMCPY3D_v2::WidthInBytes [inherited]
Width of 3D memory copy in bytes

CUarrayCUDA_MEMCPY3D_v2::dstArray [inherited]
Destination array reference

CUdeviceptrCUDA_MEMCPY3D_v2::dstDevice [inherited]
Destination device pointer

size_t  CUDA_MEMCPY3D_v2::dstHeight [inherited]
Destination height (ignored when dst is array; may be 0 if Depth==1)

void
                              * CUDA_MEMCPY3D_v2::dstHost [inherited]
Destination host pointer

size_t  CUDA_MEMCPY3D_v2::dstLOD [inherited]
Destination LOD

CUmemorytypeCUDA_MEMCPY3D_v2::dstMemoryType [inherited]
Destination memory type (host, device, array)

size_t  CUDA_MEMCPY3D_v2::dstPitch [inherited]
Destination pitch (ignored when dst is array)

size_t  CUDA_MEMCPY3D_v2::dstXInBytes [inherited]
Destination X in bytes

size_t  CUDA_MEMCPY3D_v2::dstY [inherited]
Destination Y

size_t  CUDA_MEMCPY3D_v2::dstZ [inherited]
Destination Z

void
                              * CUDA_MEMCPY3D_v2::reserved0 [inherited]
Must be NULL

void
                              * CUDA_MEMCPY3D_v2::reserved1 [inherited]
Must be NULL

CUarrayCUDA_MEMCPY3D_v2::srcArray [inherited]
Source array reference

CUdeviceptrCUDA_MEMCPY3D_v2::srcDevice [inherited]
Source device pointer

size_t  CUDA_MEMCPY3D_v2::srcHeight [inherited]
Source height (ignored when src is array; may be 0 if Depth==1)

const

                              void
                              * CUDA_MEMCPY3D_v2::srcHost [inherited]
Source host pointer

size_t  CUDA_MEMCPY3D_v2::srcLOD [inherited]
Source LOD

CUmemorytypeCUDA_MEMCPY3D_v2::srcMemoryType [inherited]
Source memory type (host, device, array)

size_t  CUDA_MEMCPY3D_v2::srcPitch [inherited]
Source pitch (ignored when src is array)

size_t  CUDA_MEMCPY3D_v2::srcXInBytes [inherited]
Source X in bytes

size_t  CUDA_MEMCPY3D_v2::srcY [inherited]
Source Y

size_t  CUDA_MEMCPY3D_v2::srcZ [inherited]
Source Z


---