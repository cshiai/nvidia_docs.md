# CUDA Driver API

[< Previous](structCUDA__EXTERNAL__SEMAPHORE__WAIT__PARAMS__v1.html) | [Next >](structCUDA__HOST__NODE__PARAMS__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.32. CUDA_GRAPH_INSTANTIATE_PARAMS Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Graph instantiation parameters


### Public Variables


cuuint64_t  flagsCUgraphNode hErrNode_outCUstream hUploadStreamCUgraphInstantiateResult result_out

### Variables


cuuint64_t  CUDA_GRAPH_INSTANTIATE_PARAMS::flags [inherited]
Instantiation flags

CUgraphNodeCUDA_GRAPH_INSTANTIATE_PARAMS::hErrNode_out [inherited]
The node which caused instantiation to fail, if any

CUstreamCUDA_GRAPH_INSTANTIATE_PARAMS::hUploadStream [inherited]
Upload stream

CUgraphInstantiateResultCUDA_GRAPH_INSTANTIATE_PARAMS::result_out [inherited]
Whether instantiation was successful. If it failed, the reason why


---