# CUDA Runtime API

[< Previous](structcudaChannelFormatDesc.html) | [Next >](structcudaConditionalNodeParams.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.7. cudaChildGraphNodeParams Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Child graph node parameters


### Public Variables


cudaGraph_t graphenumcudaGraphChildGraphNodeOwnership ownership

### Variables


cudaGraph_tcudaChildGraphNodeParams::graph [inherited]
The child graph to clone into the node for node creation, or a handle to the graph owned by the node for node query. The
                                 graph must not contain conditional nodes. Graphs containing memory allocation or memory free nodes must set the ownership
                                 to be moved to the parent.

enumcudaGraphChildGraphNodeOwnershipcudaChildGraphNodeParams::ownership [inherited]
The ownership relationship of the child graph node.


---