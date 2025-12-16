# CUDA Runtime API

[< Previous](structcudaGraphEdgeData.html) | [Next >](structcudaGraphInstantiateParams.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.32. cudaGraphExecUpdateResultInfo Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Result information returned by cudaGraphExecUpdate


### Public Variables


cudaGraphNode_t errorFromNodecudaGraphNode_t errorNodeenumcudaGraphExecUpdateResult result

### Variables


cudaGraphNode_tcudaGraphExecUpdateResultInfo::errorFromNode [inherited]
The from node of error edge when the topologies do not match. Otherwise NULL.

cudaGraphNode_tcudaGraphExecUpdateResultInfo::errorNode [inherited]
The "to node" of the error edge when the topologies do not match. The error node when the error is associated with a specific
                                 node. NULL when the error is generic.

enumcudaGraphExecUpdateResultcudaGraphExecUpdateResultInfo::result [inherited]
Gives more specific detail when a cuda graph update fails.


---