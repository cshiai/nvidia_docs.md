# CUDA Driver API

[< Previous](structCUDA__EXTERNAL__MEMORY__MIPMAPPED__ARRAY__DESC__v1.html) | [Next >](structCUDA__EXTERNAL__SEMAPHORE__SIGNAL__PARAMS__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.29. CUDA_EXTERNAL_SEMAPHORE_HANDLE_DESC_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


External semaphore handle descriptor


### Public Variables


int  fdunsigned int  flagsvoid
                           * handleconst
                           void
                           * nameconst
                           void
                           * nvSciSyncObjCUexternalSemaphoreHandleType typeCUDA_EXTERNAL_SEMAPHORE_HANDLE_DESC_v1::@21::@22  win32

### Variables


int  CUDA_EXTERNAL_SEMAPHORE_HANDLE_DESC_v1::fd [inherited]
File descriptor referencing the semaphore object. Valid when type is one of the following:


CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_OPAQUE_FD

CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_TIMELINE_SEMAPHORE_FD

unsigned int  CUDA_EXTERNAL_SEMAPHORE_HANDLE_DESC_v1::flags [inherited]
Flags reserved for the future. Must be zero.

void
                              * CUDA_EXTERNAL_SEMAPHORE_HANDLE_DESC_v1::handle [inherited]
Valid NT handle. Must be NULL if 'name' is non-NULL

const

                              void
                              * CUDA_EXTERNAL_SEMAPHORE_HANDLE_DESC_v1::name [inherited]
Name of a valid synchronization primitive. Must be NULL if 'handle' is non-NULL.

const

                              void
                              * CUDA_EXTERNAL_SEMAPHORE_HANDLE_DESC_v1::nvSciSyncObj [inherited]
Valid NvSciSyncObj. Must be non NULL

CUexternalSemaphoreHandleTypeCUDA_EXTERNAL_SEMAPHORE_HANDLE_DESC_v1::type [inherited]
Type of the handle

CUDA_EXTERNAL_SEMAPHORE_HANDLE_DESC_v1::@21::@22  CUDA_EXTERNAL_SEMAPHORE_HANDLE_DESC_v1::win32 [inherited]
Win32 handle referencing the semaphore object. Valid when type is one of the following:


CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_OPAQUE_WIN32

CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_OPAQUE_WIN32_KMT

CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_D3D12_FENCE

CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_D3D11_FENCE

CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_D3D11_KEYED_MUTEX

CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_TIMELINE_SEMAPHORE_WIN32 Exactly one of 'handle' and 'name' must be non-NULL. If type is one of the following:


CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_OPAQUE_WIN32_KMT

CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_D3D11_KEYED_MUTEX_KMT then 'name' must be NULL.


---