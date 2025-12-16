# CUDA Driver API

[< Previous](structCUgraphEdgeData.html) | [Next >](structCUgraphNodeParams.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.62. CUgraphExecUpdateResultInfo_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Result information returned by cuGraphExecUpdate


### Public Variables


CUgraphNode errorFromNodeCUgraphNode errorNodeCUgraphExecUpdateResult result

### Variables


CUgraphNodeCUgraphExecUpdateResultInfo_v1::errorFromNode [inherited]
The from node of error edge when the topologies do not match. Otherwise NULL.

CUgraphNodeCUgraphExecUpdateResultInfo_v1::errorNode [inherited]
The "to node" of the error edge when the topologies do not match. The error node when the error is associated with a specific
                                 node. NULL when the error is generic.

CUgraphExecUpdateResultCUgraphExecUpdateResultInfo_v1::result [inherited]
Gives more specific detail when a cuda graph update fails.


---