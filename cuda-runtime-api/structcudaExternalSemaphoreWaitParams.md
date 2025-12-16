# CUDA Runtime API

[< Previous](structcudaExternalSemaphoreWaitNodeParamsV2.html) | [Next >](structcudaFuncAttributes.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.29. cudaExternalSemaphoreWaitParams Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


External semaphore wait parameters, compatible with driver type


### Public Variables


void
                           * fencecudaExternalSemaphoreWaitParams::@19::@20  fenceunsigned int  flagsunsigned long long  keycudaExternalSemaphoreWaitParams::@19::@22  keyedMutexunsigned int  timeoutMsunsigned long long  value

### Variables


void
                              * cudaExternalSemaphoreWaitParams::fence [inherited]
Pointer to NvSciSyncFence. Valid if cudaExternalSemaphoreHandleType is of type cudaExternalSemaphoreHandleTypeNvSciSync.

cudaExternalSemaphoreWaitParams::@19::@20  cudaExternalSemaphoreWaitParams::fence [inherited]
Parameters for fence objects

unsigned int  cudaExternalSemaphoreWaitParams::flags [inherited]
Only when cudaExternalSemaphoreSignalParams is used to signal a cudaExternalSemaphore_t of type cudaExternalSemaphoreHandleTypeNvSciSync, the valid flag is cudaExternalSemaphoreSignalSkipNvSciBufMemSync: which indicates that while waiting for the cudaExternalSemaphore_t, no memory synchronization operations should be performed for any external memory object imported as cudaExternalMemoryHandleTypeNvSciBuf. For all other types of cudaExternalSemaphore_t, flags must be zero.

unsigned long long  cudaExternalSemaphoreWaitParams::key [inherited]
Value of key to acquire the mutex with

cudaExternalSemaphoreWaitParams::@19::@22  cudaExternalSemaphoreWaitParams::keyedMutex [inherited]
Parameters for keyed mutex objects

unsigned int  cudaExternalSemaphoreWaitParams::timeoutMs [inherited]
Timeout in milliseconds to wait to acquire the mutex

unsigned long long  cudaExternalSemaphoreWaitParams::value [inherited]
Value of fence to be waited on


---