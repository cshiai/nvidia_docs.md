# CUDA Driver API

[< Previous](structCUDA__EXTERNAL__SEMAPHORE__SIGNAL__PARAMS__v1.html) | [Next >](structCUDA__GRAPH__INSTANTIATE__PARAMS.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.31. CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


External semaphore wait parameters


### Public Variables


CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::@27::@28  fenceunsigned int  flagsunsigned long long  keyCUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::@27::@30  keyedMutexCUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::@27::@29  nvSciSyncunsigned int  timeoutMsunsigned long long  value

### Variables


CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::@27::@28  CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::fence [inherited]
Parameters for fence objects

unsigned int  CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::flags [inherited]
Only when CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS is used to wait on a CUexternalSemaphore of type CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_NVSCISYNC, the valid flag is CUDA_EXTERNAL_SEMAPHORE_WAIT_SKIP_NVSCIBUF_MEMSYNC which indicates that while waiting for the CUexternalSemaphore, no memory synchronization operations should be performed for any external memory object imported as CU_EXTERNAL_MEMORY_HANDLE_TYPE_NVSCIBUF. For all other types of CUexternalSemaphore, flags must be zero.

unsigned long long  CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::key [inherited]
Value of key to acquire the mutex with

CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::@27::@30  CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::keyedMutex [inherited]
Parameters for keyed mutex objects

CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::@27::@29  CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::nvSciSync [inherited]
Pointer to NvSciSyncFence. Valid if CUexternalSemaphoreHandleType is of type CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_NVSCISYNC.

unsigned int  CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::timeoutMs [inherited]
Timeout in milliseconds to wait to acquire the mutex

unsigned long long  CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1::value [inherited]
Value of fence to be waited on


---