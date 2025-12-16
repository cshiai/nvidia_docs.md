# CUDA Runtime API

[< Previous](structcudaExternalMemoryBufferDesc.html) | [Next >](structcudaExternalMemoryMipmappedArrayDesc.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.21. cudaExternalMemoryHandleDesc Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


External memory handle descriptor


### Public Variables


int  fdunsigned int  flagsvoid
                           * handleconst
                           void
                           * nameconst
                           void
                           * nvSciBufObjectunsigned int  reserved[16]unsigned long long  sizeenumcudaExternalMemoryHandleType typecudaExternalMemoryHandleDesc::@11::@12  win32

### Variables


int  cudaExternalMemoryHandleDesc::fd [inherited]
File descriptor referencing the memory object. Valid when type is cudaExternalMemoryHandleTypeOpaqueFd

unsigned int  cudaExternalMemoryHandleDesc::flags [inherited]
Flags must either be zero or cudaExternalMemoryDedicated

void
                              * cudaExternalMemoryHandleDesc::handle [inherited]
Valid NT handle. Must be NULL if 'name' is non-NULL

const

                              void
                              * cudaExternalMemoryHandleDesc::name [inherited]
Name of a valid memory object. Must be NULL if 'handle' is non-NULL.

const

                              void
                              * cudaExternalMemoryHandleDesc::nvSciBufObject [inherited]
A handle representing NvSciBuf Object. Valid when type is cudaExternalMemoryHandleTypeNvSciBuf

unsigned int  cudaExternalMemoryHandleDesc::reserved[16] [inherited]
Must be zero

unsigned long long  cudaExternalMemoryHandleDesc::size [inherited]
Size of the memory allocation

enumcudaExternalMemoryHandleTypecudaExternalMemoryHandleDesc::type [inherited]
Type of the handle

cudaExternalMemoryHandleDesc::@11::@12  cudaExternalMemoryHandleDesc::win32 [inherited]
Win32 handle referencing the semaphore object. Valid when type is one of the following:


cudaExternalMemoryHandleTypeOpaqueWin32

cudaExternalMemoryHandleTypeOpaqueWin32Kmt

cudaExternalMemoryHandleTypeD3D12Heap

cudaExternalMemoryHandleTypeD3D12Resource

cudaExternalMemoryHandleTypeD3D11Resource

cudaExternalMemoryHandleTypeD3D11ResourceKmt Exactly one of 'handle' and 'name' must be non-NULL. If type is one of the following: cudaExternalMemoryHandleTypeOpaqueWin32KmtcudaExternalMemoryHandleTypeD3D11ResourceKmt then 'name' must be NULL.


---