# CUDA Runtime API

[< Previous](structcudaExternalSemaphoreSignalNodeParamsV2.html) | [Next >](structcudaExternalSemaphoreWaitNodeParams.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.26. cudaExternalSemaphoreSignalParams Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


External semaphore signal parameters, compatible with driver type


### Public Variables


void
                           * fencecudaExternalSemaphoreSignalParams::@15::@16  fenceunsigned int  flagscudaExternalSemaphoreSignalParams::@15::@18  keyedMutexunsigned long long  value

### Variables


void
                              * cudaExternalSemaphoreSignalParams::fence [inherited]
Pointer to NvSciSyncFence. Valid if cudaExternalSemaphoreHandleType is of type cudaExternalSemaphoreHandleTypeNvSciSync.

cudaExternalSemaphoreSignalParams::@15::@16  cudaExternalSemaphoreSignalParams::fence [inherited]
Parameters for fence objects

unsigned int  cudaExternalSemaphoreSignalParams::flags [inherited]
Only when cudaExternalSemaphoreSignalParams is used to signal a cudaExternalSemaphore_t of type cudaExternalSemaphoreHandleTypeNvSciSync, the valid flag is cudaExternalSemaphoreSignalSkipNvSciBufMemSync: which indicates that while signaling the cudaExternalSemaphore_t, no memory synchronization operations should be performed for any external memory object imported as cudaExternalMemoryHandleTypeNvSciBuf. For all other types of cudaExternalSemaphore_t, flags must be zero.

cudaExternalSemaphoreSignalParams::@15::@18  cudaExternalSemaphoreSignalParams::keyedMutex [inherited]
Parameters for keyed mutex objects

unsigned long long  cudaExternalSemaphoreSignalParams::value [inherited]
Value of fence to be signaled


---