# CUDA Runtime API

[< Previous](structcudaEglFrame.html) | [Next >](structcudaEventRecordNodeParams.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.16. cudaEglPlaneDesc Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA EGL Plane Descriptor - structure defining each plane of a CUDA EGLFrame


### Public Variables


struct cudaChannelFormatDesc channelDescunsigned int  depthunsigned int  heightunsigned int  numChannelsunsigned int  pitchunsigned int  reserved[4]unsigned int  width

### Variables


struct cudaChannelFormatDesccudaEglPlaneDesc::channelDesc [inherited]
Channel Format Descriptor

unsigned int  cudaEglPlaneDesc::depth [inherited]
Depth of plane

unsigned int  cudaEglPlaneDesc::height [inherited]
Height of plane

unsigned int  cudaEglPlaneDesc::numChannels [inherited]
Number of channels for the plane

unsigned int  cudaEglPlaneDesc::pitch [inherited]
Pitch of plane

unsigned int  cudaEglPlaneDesc::reserved[4] [inherited]
Reserved for future use

unsigned int  cudaEglPlaneDesc::width [inherited]
Width of plane


---