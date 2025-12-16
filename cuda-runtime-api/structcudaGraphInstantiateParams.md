# CUDA Runtime API

[< Previous](structcudaGraphExecUpdateResultInfo.html) | [Next >](structcudaGraphKernelNodeUpdate.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.33. cudaGraphInstantiateParams Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Graph instantiation parameters


### Public Variables


cudaGraphNode_t errNode_outunsigned long long  flagscudaGraphInstantiateResult result_outcudaStream_t uploadStream

### Variables


cudaGraphNode_tcudaGraphInstantiateParams::errNode_out [inherited]
The node which caused instantiation to fail, if any

unsigned long long  cudaGraphInstantiateParams::flags [inherited]
Instantiation flags

cudaGraphInstantiateResultcudaGraphInstantiateParams::result_out [inherited]
Whether instantiation was successful. If it failed, the reason why

cudaStream_tcudaGraphInstantiateParams::uploadStream [inherited]
Upload stream


---