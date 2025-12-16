# CUDA Driver API

[< Previous](https://docs.nvidia.com/cuda/cuda-driver-api/structCUDA__BATCH__MEM__OP__NODE__PARAMS__v2.html) | [Next >](structCUDA__CONDITIONAL__NODE__PARAMS.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.18. CUDA_CHILD_GRAPH_NODE_PARAMS Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Child graph node parameters


### Public Variables


CUgraph graphCUgraphChildGraphNodeOwnership ownership

### Variables


CUgraphCUDA_CHILD_GRAPH_NODE_PARAMS::graph [inherited]
The child graph to clone into the node for node creation, or a handle to the graph owned by the node for node query. The
                                 graph must not contain conditional nodes. Graphs containing memory allocation or memory free nodes must set the ownership
                                 to be moved to the parent.

CUgraphChildGraphNodeOwnershipCUDA_CHILD_GRAPH_NODE_PARAMS::ownership [inherited]
The ownership relationship of the child graph node.


---