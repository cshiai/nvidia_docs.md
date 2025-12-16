# CUDA Runtime API

[< Previous](structcudaExternalMemoryMipmappedArrayDesc.html) | [Next >](structcudaExternalSemaphoreSignalNodeParams.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.23. cudaExternalSemaphoreHandleDesc Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


External semaphore handle descriptor


### Public Variables


int  fdunsigned int  flagsvoid
                           * handleconst
                           void
                           * nameconst
                           void
                           * nvSciSyncObjunsigned int  reserved[16]enumcudaExternalSemaphoreHandleType typecudaExternalSemaphoreHandleDesc::@13::@14  win32

### Variables


int  cudaExternalSemaphoreHandleDesc::fd [inherited]
File descriptor referencing the semaphore object. Valid when type is one of the following:


cudaExternalSemaphoreHandleTypeOpaqueFd

cudaExternalSemaphoreHandleTypeTimelineSemaphoreFd

unsigned int  cudaExternalSemaphoreHandleDesc::flags [inherited]
Flags reserved for the future. Must be zero.

void
                              * cudaExternalSemaphoreHandleDesc::handle [inherited]
Valid NT handle. Must be NULL if 'name' is non-NULL

const

                              void
                              * cudaExternalSemaphoreHandleDesc::name [inherited]
Name of a valid synchronization primitive. Must be NULL if 'handle' is non-NULL.

const

                              void
                              * cudaExternalSemaphoreHandleDesc::nvSciSyncObj [inherited]
Valid NvSciSyncObj. Must be non NULL

unsigned int  cudaExternalSemaphoreHandleDesc::reserved[16] [inherited]
Must be zero

enumcudaExternalSemaphoreHandleTypecudaExternalSemaphoreHandleDesc::type [inherited]
Type of the handle

cudaExternalSemaphoreHandleDesc::@13::@14  cudaExternalSemaphoreHandleDesc::win32 [inherited]
Win32 handle referencing the semaphore object. Valid when type is one of the following:


cudaExternalSemaphoreHandleTypeOpaqueWin32

cudaExternalSemaphoreHandleTypeOpaqueWin32Kmt

cudaExternalSemaphoreHandleTypeD3D12Fence

cudaExternalSemaphoreHandleTypeD3D11Fence

cudaExternalSemaphoreHandleTypeKeyedMutex

cudaExternalSemaphoreHandleTypeTimelineSemaphoreWin32 Exactly one of 'handle' and 'name' must be non-NULL. If type is one of the following: cudaExternalSemaphoreHandleTypeOpaqueWin32KmtcudaExternalSemaphoreHandleTypeKeyedMutexKmt then 'name' must be NULL.


---