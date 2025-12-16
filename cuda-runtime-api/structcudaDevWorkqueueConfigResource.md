# CUDA Runtime API

[< Previous](structcudaDevSmResourceGroupParams.html) | [Next >](structcudaDevWorkqueueResource.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.13. cudaDevWorkqueueConfigResource Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Data for workqueue configuration related resources


### Public Variables


int  deviceenumcudaDevWorkqueueConfigScope sharingScopeunsigned int  wqConcurrencyLimit

### Variables


int  cudaDevWorkqueueConfigResource::device [inherited]
The device on which the workqueue resources are available

enumcudaDevWorkqueueConfigScopecudaDevWorkqueueConfigResource::sharingScope [inherited]
The sharing scope for the workqueue resources

unsigned int  cudaDevWorkqueueConfigResource::wqConcurrencyLimit [inherited]
The expected maximum number of concurrent stream-ordered workloads


---