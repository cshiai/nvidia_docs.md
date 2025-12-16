# CUDA Runtime API

[< Previous](structcudaMemcpy3DPeerParms.html) | [Next >](structcudaMemcpyNodeParams.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.52. cudaMemcpyAttributes Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Attributes specific to copies within a batch. For more details on usage see [cudaMemcpyBatchAsync](group__CUDART__HIGHLEVEL.html#group__CUDART__HIGHLEVEL_1g58cf0d0f10efd8c0748b1722ef9eb070).


### Public Variables


struct cudaMemLocation dstLocHintunsigned int  flagsenumcudaMemcpySrcAccessOrder srcAccessOrderstruct cudaMemLocation srcLocHint

### Variables


struct cudaMemLocationcudaMemcpyAttributes::dstLocHint [inherited]
Hint location for the destination operand. Ignored when the pointers are not managed memory or memory allocated outside CUDA.

unsigned int  cudaMemcpyAttributes::flags [inherited]
Additional flags for copies with this attribute. See cudaMemcpyFlags.

enumcudaMemcpySrcAccessOrdercudaMemcpyAttributes::srcAccessOrder [inherited]
Source access ordering to be observed for copies with this attribute.

struct cudaMemLocationcudaMemcpyAttributes::srcLocHint [inherited]
Hint location for the source operand. Ignored when the pointers are not managed memory or memory allocated outside CUDA.


---