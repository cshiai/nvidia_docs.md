# CUDA Driver API

[< Previous](structCUDA__EXTERNAL__SEMAPHORE__HANDLE__DESC__v1.html) | [Next >](structCUDA__EXTERNAL__SEMAPHORE__WAIT__PARAMS__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.30. CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


External semaphore signal parameters


### Public Variables


void
                           * fenceCUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS_v1::@23::@24  fenceunsigned int  flagsunsigned long long  keyCUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS_v1::@23::@26  keyedMutexunsigned long long  value

### Variables


void
                              * CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS_v1::fence [inherited]
Pointer to NvSciSyncFence. Valid if CUexternalSemaphoreHandleType is of type CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_NVSCISYNC.

CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS_v1::@23::@24  CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS_v1::fence [inherited]
Parameters for fence objects

unsigned int  CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS_v1::flags [inherited]
Only when CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS is used to signal a CUexternalSemaphore of type CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_NVSCISYNC, the valid flag is CUDA_EXTERNAL_SEMAPHORE_SIGNAL_SKIP_NVSCIBUF_MEMSYNC which indicates that while signaling the CUexternalSemaphore, no memory synchronization operations should be performed for any external memory object imported as CU_EXTERNAL_MEMORY_HANDLE_TYPE_NVSCIBUF. For all other types of CUexternalSemaphore, flags must be zero.

unsigned long long  CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS_v1::key [inherited]
Value of key to release the mutex with

CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS_v1::@23::@26  CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS_v1::keyedMutex [inherited]
Parameters for keyed mutex objects

unsigned long long  CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS_v1::value [inherited]
Value of fence to be signaled


---