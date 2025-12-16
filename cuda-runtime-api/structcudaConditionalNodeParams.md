# CUDA Runtime API

[< Previous](structcudaChildGraphNodeParams.html) | [Next >](structcudaDeviceProp.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.8. cudaConditionalNodeParams Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA conditional node parameters


### Public Variables


cudaExecutionContext_t ctxcudaGraphConditionalHandle handlecudaGraph_t phGraph_outunsigned int  sizeenumcudaGraphConditionalNodeType type

### Variables


cudaExecutionContext_tcudaConditionalNodeParams::ctx [inherited]
CUDA Execution Context

cudaGraphConditionalHandlecudaConditionalNodeParams::handle [inherited]
Conditional node handle. Handles must be created in advance of creating the node using cudaGraphConditionalHandleCreate.

cudaGraph_t cudaConditionalNodeParams::phGraph_out [inherited]
CUDA-owned array populated with conditional node child graphs during creation of the node. Valid for the lifetime of the
                                 conditional node. The contents of the graph(s) are subject to the following constraints:


Allowed node types are kernel nodes, empty nodes, child graphs, memsets, memcopies, and conditionals. This applies recursively
                                          to child graphs and conditional bodies.


All kernels, including kernels in nested conditionals or child graphs at any level, must belong to the same CUDA context.

These graphs may be populated using graph node creation APIs or cudaStreamBeginCaptureToGraph. cudaGraphCondTypeIf: phGraph_out[0] is executed when the condition is non-zero. If size == 2, phGraph_out[1] will be executed when the condition is zero. cudaGraphCondTypeWhile: phGraph_out[0] is executed as long
                                 as the condition is non-zero. cudaGraphCondTypeSwitch: phGraph_out[n] is executed when the condition is equal to n. If the
                                 condition >= size, no body graph is executed.

unsigned int  cudaConditionalNodeParams::size [inherited]
Size of graph output array. Allowed values are 1 for cudaGraphCondTypeWhile, 1 or 2 for cudaGraphCondTypeIf, or any value
                                 greater than zero for cudaGraphCondTypeSwitch.

enumcudaGraphConditionalNodeTypecudaConditionalNodeParams::type [inherited]
Type of conditional node.


---