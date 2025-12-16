# CUDA Runtime API

[< Previous](structcudaArraySparseProperties.html) | [Next >](structcudaChannelFormatDesc.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.5. cudaAsyncNotificationInfo_t Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Information describing an async notification event


### Public Variables


unsigned long long  bytesOverBudgetcudaAsyncNotificationInfo_t::@34  infocudaAsyncNotificationInfo_t::@34::@35  overBudgetcudaAsyncNotificationType type

### Variables


unsigned long long  cudaAsyncNotificationInfo_t::bytesOverBudget [inherited]
The number of bytes that the process has allocated above its device memory budget

cudaAsyncNotificationInfo_t::@34  cudaAsyncNotificationInfo_t::info [inherited]
Information about the notification. type must be checked in order to interpret this field.

cudaAsyncNotificationInfo_t::@34::@35  cudaAsyncNotificationInfo_t::overBudget [inherited]
Information about notifications of type cudaAsyncNotificationTypeOverBudget

cudaAsyncNotificationTypecudaAsyncNotificationInfo_t::type [inherited]
The type of notification being sent


---