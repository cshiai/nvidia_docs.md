# CUDA Driver API

[< Previous](structCUdevWorkqueueResource.html) | [Next >](structCUexecAffinityParam__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.57. CUeglFrame_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


CUDA EGLFrame structure Descriptor - structure defining one frame of EGL.


Each frame may contain one or more planes depending on whether the surface * is Multiplanar or not.


### Public Variables


CUarray_format cuFormatunsigned int  depthCUeglColorFormat eglColorFormatCUeglFrameType frameTypeunsigned int  heightunsigned int  numChannelsCUarray pArray[MAX_PLANES]void
                           [MAX_PLANES]
                           * pPitchunsigned int  pitchunsigned int  planeCountunsigned int  width

### Variables


CUarray_formatCUeglFrame_v1::cuFormat [inherited]
CUDA Array Format

unsigned int  CUeglFrame_v1::depth [inherited]
Depth of first plane

CUeglColorFormatCUeglFrame_v1::eglColorFormat [inherited]
CUDA EGL Color Format

CUeglFrameTypeCUeglFrame_v1::frameType [inherited]
Array or Pitch

unsigned int  CUeglFrame_v1::height [inherited]
Height of first plane

unsigned int  CUeglFrame_v1::numChannels [inherited]
Number of channels for the plane

CUarrayCUeglFrame_v1::pArray[MAX_PLANES] [inherited]
Array of CUarray corresponding to each plane

void
                              [MAX_PLANES]
                              * CUeglFrame_v1::pPitch [inherited]
Array of Pointers corresponding to each plane

unsigned int  CUeglFrame_v1::pitch [inherited]
Pitch of first plane

unsigned int  CUeglFrame_v1::planeCount [inherited]
Number of planes

unsigned int  CUeglFrame_v1::width [inherited]
Width of first plane


---