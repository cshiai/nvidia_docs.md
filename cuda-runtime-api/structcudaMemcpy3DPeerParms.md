# CUDA Runtime API

[< Previous](structcudaMemcpy3DParms.html) | [Next >](structcudaMemcpyAttributes.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.51. cudaMemcpy3DPeerParms Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA 3D cross-device memory copying parameters


### Public Variables


cudaArray_t dstArrayint  dstDevicestruct cudaPos dstPosstruct cudaPitchedPtr dstPtrstruct cudaExtent extentcudaArray_t srcArrayint  srcDevicestruct cudaPos srcPosstruct cudaPitchedPtr srcPtr

### Variables


cudaArray_tcudaMemcpy3DPeerParms::dstArray [inherited]
Destination memory address

int  cudaMemcpy3DPeerParms::dstDevice [inherited]
Destination device

struct cudaPoscudaMemcpy3DPeerParms::dstPos [inherited]
Destination position offset

struct cudaPitchedPtrcudaMemcpy3DPeerParms::dstPtr [inherited]
Pitched destination memory address

struct cudaExtentcudaMemcpy3DPeerParms::extent [inherited]
Requested memory copy size

cudaArray_tcudaMemcpy3DPeerParms::srcArray [inherited]
Source memory address

int  cudaMemcpy3DPeerParms::srcDevice [inherited]
Source device

struct cudaPoscudaMemcpy3DPeerParms::srcPos [inherited]
Source position offset

struct cudaPitchedPtrcudaMemcpy3DPeerParms::srcPtr [inherited]
Pitched source memory address


---