# CUDA Driver API

[< Previous](structCUdevSmResource.html) | [Next >](structCUdevWorkqueueResource.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.55. CUdevWorkqueueConfigResource Struct Reference


## [[Green Contexts](group__CUDA__GREEN__CONTEXTS.html#group__CUDA__GREEN__CONTEXTS)]


Data for workqueue configuration related resources


### Public Variables


CUdevice deviceCUdevWorkqueueConfigScope sharingScopeunsigned int  wqConcurrencyLimit

### Variables


CUdeviceCUdevWorkqueueConfigResource::device [inherited]
The device on which the workqueue resources are available

CUdevWorkqueueConfigScopeCUdevWorkqueueConfigResource::sharingScope [inherited]
The sharing scope for the workqueue resources

unsigned int  CUdevWorkqueueConfigResource::wqConcurrencyLimit [inherited]
The expected maximum number of concurrent stream-ordered workloads


---