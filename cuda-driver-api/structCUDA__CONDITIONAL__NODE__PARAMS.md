# CUDA Driver API

[< Previous](structCUDA__CHILD__GRAPH__NODE__PARAMS.html) | [Next >](structCUDA__EVENT__RECORD__NODE__PARAMS.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.19. CUDA_CONDITIONAL_NODE_PARAMS Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Conditional node parameters


### Public Variables


CUcontext ctxCUgraphConditionalHandle handleCUgraph phGraph_outunsigned int  sizeCUgraphConditionalNodeType type

### Variables


CUcontextCUDA_CONDITIONAL_NODE_PARAMS::ctx [inherited]
Context on which to run the node. Must match context used to create the handle and all body nodes.

CUgraphConditionalHandleCUDA_CONDITIONAL_NODE_PARAMS::handle [inherited]
Conditional node handle. Handles must be created in advance of creating the node using cuGraphConditionalHandleCreate.

CUgraph CUDA_CONDITIONAL_NODE_PARAMS::phGraph_out [inherited]
CUDA-owned array populated with conditional node child graphs during creation of the node. Valid for the lifetime of the
                                 conditional node. The contents of the graph(s) are subject to the following constraints:


Allowed node types are kernel nodes, empty nodes, child graphs, memsets, memcopies, and conditionals. This applies recursively
                                          to child graphs and conditional bodies.


All kernels, including kernels in nested conditionals or child graphs at any level, must belong to the same CUDA context.

These graphs may be populated using graph node creation APIs or cuStreamBeginCaptureToGraph.

CU_GRAPH_COND_TYPE_IF: phGraph_out[0] is executed when the condition is non-zero. If size == 2, phGraph_out[1] will be executed when the condition is zero. CU_GRAPH_COND_TYPE_WHILE: phGraph_out[0] is executed as
                                 long as the condition is non-zero. CU_GRAPH_COND_TYPE_SWITCH: phGraph_out[n] is executed when the condition is equal to n.
                                 If the condition >= size, no body graph is executed.

unsigned int  CUDA_CONDITIONAL_NODE_PARAMS::size [inherited]
Size of graph output array. Allowed values are 1 for CU_GRAPH_COND_TYPE_WHILE, 1 or 2 for CU_GRAPH_COND_TYPE_IF, or any value
                                 greater than zero for CU_GRAPH_COND_TYPE_SWITCH.

CUgraphConditionalNodeTypeCUDA_CONDITIONAL_NODE_PARAMS::type [inherited]
Type of conditional node.


---