# CUDA Runtime API

[< Previous](structcudaDevWorkqueueResource.html) | [Next >](structcudaEglPlaneDesc.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.15. cudaEglFrame Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA EGLFrame Descriptor - structure defining one frame of EGL.


Each frame may contain one or more planes depending on whether the surface is Multiplanar or not. Each plane of EGLFrame is represented by [cudaEglPlaneDesc](structcudaEglPlaneDesc.html#structcudaEglPlaneDesc) which is defined as:


```
‎ typedef struct cudaEglPlaneDesc_st {
           unsigned int width;
           unsigned int height;
           unsigned int depth;
           unsigned int pitch;
           unsigned int numChannels;
           struct cudaChannelFormatDesc channelDesc;
           unsigned int reserved[4];
       } cudaEglPlaneDesc;
```


### Public Variables


cudaEglColorFormat eglColorFormatcudaEglFrameType frameTypecudaArray_t pArray[CUDA_EGL_MAX_PLANES]struct cudaPitchedPtr pPitch[CUDA_EGL_MAX_PLANES]unsigned int  planeCountstruct cudaEglPlaneDesc planeDesc[CUDA_EGL_MAX_PLANES]

### Variables


cudaEglColorFormatcudaEglFrame::eglColorFormat [inherited]
CUDA EGL Color Format

cudaEglFrameTypecudaEglFrame::frameType [inherited]
Array or Pitch

cudaArray_tcudaEglFrame::pArray[CUDA_EGL_MAX_PLANES] [inherited]
Array of CUDA arrays corresponding to each plane

struct cudaPitchedPtrcudaEglFrame::pPitch[CUDA_EGL_MAX_PLANES] [inherited]
Array of Pointers corresponding to each plane

unsigned int  cudaEglFrame::planeCount [inherited]
Number of planes

struct cudaEglPlaneDesccudaEglFrame::planeDesc[CUDA_EGL_MAX_PLANES] [inherited]
CUDA EGL Plane Descriptor cudaEglPlaneDesc


---