# CUDA Driver API

[< Previous](structCUDA__MEMCPY2D__v2.html) | [Next >](structCUDA__MEMCPY3D__v2.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.43. CUDA_MEMCPY3D_PEER_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


3D memory cross-context copy parameters


### Public Variables


size_t  Depthsize_t  Heightsize_t  WidthInBytesCUarray dstArrayCUcontext dstContextCUdeviceptr dstDevicesize_t  dstHeightvoid
                           * dstHostsize_t  dstLODCUmemorytype dstMemoryTypesize_t  dstPitchsize_t  dstXInBytessize_t  dstYsize_t  dstZCUarray srcArrayCUcontext srcContextCUdeviceptr srcDevicesize_t  srcHeightconst
                           void
                           * srcHostsize_t  srcLODCUmemorytype srcMemoryTypesize_t  srcPitchsize_t  srcXInBytessize_t  srcYsize_t  srcZ

### Variables


size_t  CUDA_MEMCPY3D_PEER_v1::Depth [inherited]
Depth of 3D memory copy

size_t  CUDA_MEMCPY3D_PEER_v1::Height [inherited]
Height of 3D memory copy

size_t  CUDA_MEMCPY3D_PEER_v1::WidthInBytes [inherited]
Width of 3D memory copy in bytes

CUarrayCUDA_MEMCPY3D_PEER_v1::dstArray [inherited]
Destination array reference

CUcontextCUDA_MEMCPY3D_PEER_v1::dstContext [inherited]
Destination context (ignored with dstMemoryType is CU_MEMORYTYPE_ARRAY)

CUdeviceptrCUDA_MEMCPY3D_PEER_v1::dstDevice [inherited]
Destination device pointer

size_t  CUDA_MEMCPY3D_PEER_v1::dstHeight [inherited]
Destination height (ignored when dst is array; may be 0 if Depth==1)

void
                              * CUDA_MEMCPY3D_PEER_v1::dstHost [inherited]
Destination host pointer

size_t  CUDA_MEMCPY3D_PEER_v1::dstLOD [inherited]
Destination LOD

CUmemorytypeCUDA_MEMCPY3D_PEER_v1::dstMemoryType [inherited]
Destination memory type (host, device, array)

size_t  CUDA_MEMCPY3D_PEER_v1::dstPitch [inherited]
Destination pitch (ignored when dst is array)

size_t  CUDA_MEMCPY3D_PEER_v1::dstXInBytes [inherited]
Destination X in bytes

size_t  CUDA_MEMCPY3D_PEER_v1::dstY [inherited]
Destination Y

size_t  CUDA_MEMCPY3D_PEER_v1::dstZ [inherited]
Destination Z

CUarrayCUDA_MEMCPY3D_PEER_v1::srcArray [inherited]
Source array reference

CUcontextCUDA_MEMCPY3D_PEER_v1::srcContext [inherited]
Source context (ignored with srcMemoryType is CU_MEMORYTYPE_ARRAY)

CUdeviceptrCUDA_MEMCPY3D_PEER_v1::srcDevice [inherited]
Source device pointer

size_t  CUDA_MEMCPY3D_PEER_v1::srcHeight [inherited]
Source height (ignored when src is array; may be 0 if Depth==1)

const

                              void
                              * CUDA_MEMCPY3D_PEER_v1::srcHost [inherited]
Source host pointer

size_t  CUDA_MEMCPY3D_PEER_v1::srcLOD [inherited]
Source LOD

CUmemorytypeCUDA_MEMCPY3D_PEER_v1::srcMemoryType [inherited]
Source memory type (host, device, array)

size_t  CUDA_MEMCPY3D_PEER_v1::srcPitch [inherited]
Source pitch (ignored when src is array)

size_t  CUDA_MEMCPY3D_PEER_v1::srcXInBytes [inherited]
Source X in bytes

size_t  CUDA_MEMCPY3D_PEER_v1::srcY [inherited]
Source Y

size_t  CUDA_MEMCPY3D_PEER_v1::srcZ [inherited]
Source Z


---