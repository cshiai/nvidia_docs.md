# CUDA Driver API

[< Previous](structCUarrayMapInfo__v1.html) | [Next >](structCUcheckpointCheckpointArgs.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.4. CUasyncNotificationInfo Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Information passed to the user via the async notification callback


### Public Variables


unsigned long long  bytesOverBudgetCUasyncNotificationInfo::@4  infoCUasyncNotificationInfo::@4::@5  overBudgetCUasyncNotificationType type

### Variables


unsigned long long  CUasyncNotificationInfo::bytesOverBudget [inherited]
The number of bytes that the process has allocated above its device memory budget

CUasyncNotificationInfo::@4  CUasyncNotificationInfo::info [inherited]
Information about the notification. type must be checked in order to interpret this field.

CUasyncNotificationInfo::@4::@5  CUasyncNotificationInfo::overBudget [inherited]
Information about notifications of type CU_ASYNC_NOTIFICATION_TYPE_OVER_BUDGET

CUasyncNotificationTypeCUasyncNotificationInfo::type [inherited]
The type of notification being sent


---