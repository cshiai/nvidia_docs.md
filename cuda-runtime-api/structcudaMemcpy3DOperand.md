# CUDA Runtime API

[< Previous](structcudaMemAllocNodeParamsV2.html) | [Next >](structcudaMemcpy3DParms.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.49. cudaMemcpy3DOperand Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Struct representing an operand for copy with [cudaMemcpy3DBatchAsync](group__CUDART__MEMORY.html#group__CUDART__MEMORY_1g9b3b66be1f930f77f717e54783573f9a)


### Public Variables


cudaMemcpy3DOperand::@8::@10  arraysize_t  layerHeightstruct cudaMemLocation locHintcudaMemcpy3DOperand::@8::@9  ptrsize_t  rowLength

### Variables


cudaMemcpy3DOperand::@8::@10  cudaMemcpy3DOperand::array [inherited]
Struct representing an operand when cudaMemcpy3DOperand::type is cudaMemcpyOperandTypeArray

size_t  cudaMemcpy3DOperand::layerHeight [inherited]
Height of each layer in elements.

struct cudaMemLocationcudaMemcpy3DOperand::locHint [inherited]
Hint location for the operand. Ignored when the pointers are not managed memory or memory allocated outside CUDA.

cudaMemcpy3DOperand::@8::@9  cudaMemcpy3DOperand::ptr [inherited]
Struct representing an operand when cudaMemcpy3DOperand::type is cudaMemcpyOperandTypePointer

size_t  cudaMemcpy3DOperand::rowLength [inherited]
Length of each row in elements.


---