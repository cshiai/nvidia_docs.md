# CUDA Driver API

[< Previous](structCUmemcpy3DOperand__v1.html) | [Next >](structCUmemDecompressParams.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.73. CUmemcpyAttributes_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Attributes specific to copies within a batch. For more details on usage see [cuMemcpyBatchAsync](group__CUDA__MEM.html#group__CUDA__MEM_1g6f1ff58e3065df3eb4b573dba77ad31f).


### Public Variables


struct CUmemLocation dstLocHintunsigned int  flagsCUmemcpySrcAccessOrder srcAccessOrderstruct CUmemLocation srcLocHint

### Variables


struct CUmemLocationCUmemcpyAttributes_v1::dstLocHint [inherited]
Hint location for the destination operand. Ignored when the pointers are not managed memory or memory allocated outside CUDA.

unsigned int  CUmemcpyAttributes_v1::flags [inherited]
Additional flags for copies with this attribute. See CUmemcpyFlags

CUmemcpySrcAccessOrderCUmemcpyAttributes_v1::srcAccessOrder [inherited]
Source access ordering to be observed for copies with this attribute.

struct CUmemLocationCUmemcpyAttributes_v1::srcLocHint [inherited]
Hint location for the source operand. Ignored when the pointers are not managed memory or memory allocated outside CUDA.


---