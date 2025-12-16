# CUDA Driver API

[< Previous](structCUmemAllocationProp__v1.html) | [Next >](structCUmemcpyAttributes__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.72. CUmemcpy3DOperand_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Struct representing an operand for copy with [cuMemcpy3DBatchAsync](group__CUDA__MEM.html#group__CUDA__MEM_1g97dd29d0e3490379a5cbdb21deb41f12)


### Public Variables


CUmemcpy3DOperand_v1::@37::@39  arraysize_t  layerHeightstruct CUmemLocation locHintCUmemcpy3DOperand_v1::@37::@38  ptrsize_t  rowLength

### Variables


CUmemcpy3DOperand_v1::@37::@39  CUmemcpy3DOperand_v1::array [inherited]
Struct representing an operand when CUmemcpy3DOperand::type is CU_MEMCPY_OPERAND_TYPE_ARRAY

size_t  CUmemcpy3DOperand_v1::layerHeight [inherited]
Height of each layer in elements.

struct CUmemLocationCUmemcpy3DOperand_v1::locHint [inherited]
Hint location for the operand. Ignored when the pointers are not managed memory or memory allocated outside CUDA.

CUmemcpy3DOperand_v1::@37::@38  CUmemcpy3DOperand_v1::ptr [inherited]
Struct representing an operand when CUmemcpy3DOperand::type is CU_MEMCPY_OPERAND_TYPE_POINTER

size_t  CUmemcpy3DOperand_v1::rowLength [inherited]
Length of each row in elements.


---