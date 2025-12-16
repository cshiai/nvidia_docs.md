# CUDA Runtime API

[< Previous](structcudaMemcpy3DOperand.html) | [Next >](structcudaMemcpy3DPeerParms.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.50. cudaMemcpy3DParms Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA 3D memory copying parameters


### Public Variables


cudaArray_t dstArraystruct cudaPos dstPosstruct cudaPitchedPtr dstPtrstruct cudaExtent extentenumcudaMemcpyKind kindcudaArray_t srcArraystruct cudaPos srcPosstruct cudaPitchedPtr srcPtr

### Variables


cudaArray_tcudaMemcpy3DParms::dstArray [inherited]
Destination memory address

struct cudaPoscudaMemcpy3DParms::dstPos [inherited]
Destination position offset

struct cudaPitchedPtrcudaMemcpy3DParms::dstPtr [inherited]
Pitched destination memory address

struct cudaExtentcudaMemcpy3DParms::extent [inherited]
Requested memory copy size

enumcudaMemcpyKindcudaMemcpy3DParms::kind [inherited]
Type of transfer

cudaArray_tcudaMemcpy3DParms::srcArray [inherited]
Source memory address

struct cudaPoscudaMemcpy3DParms::srcPos [inherited]
Source position offset

struct cudaPitchedPtrcudaMemcpy3DParms::srcPtr [inherited]
Pitched source memory address


---