# CUDA Driver API

[< Previous](structCUDA__EXTERNAL__MEMORY__BUFFER__DESC__v1.html) | [Next >](structCUDA__EXTERNAL__MEMORY__MIPMAPPED__ARRAY__DESC__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.27. CUDA_EXTERNAL_MEMORY_HANDLE_DESC_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


External memory handle descriptor


### Public Variables


int  fdunsigned int  flagsvoid
                           * handleconst
                           void
                           * nameconst
                           void
                           * nvSciBufObjectunsigned long long  sizeCUexternalMemoryHandleType typeCUDA_EXTERNAL_MEMORY_HANDLE_DESC_v1::@19::@20  win32

### Variables


int  CUDA_EXTERNAL_MEMORY_HANDLE_DESC_v1::fd [inherited]
File descriptor referencing the memory object. Valid when type is CU_EXTERNAL_MEMORY_HANDLE_TYPE_OPAQUE_FD

unsigned int  CUDA_EXTERNAL_MEMORY_HANDLE_DESC_v1::flags [inherited]
Flags must either be zero or CUDA_EXTERNAL_MEMORY_DEDICATED

void
                              * CUDA_EXTERNAL_MEMORY_HANDLE_DESC_v1::handle [inherited]
Valid NT handle. Must be NULL if 'name' is non-NULL

const

                              void
                              * CUDA_EXTERNAL_MEMORY_HANDLE_DESC_v1::name [inherited]
Name of a valid memory object. Must be NULL if 'handle' is non-NULL.

const

                              void
                              * CUDA_EXTERNAL_MEMORY_HANDLE_DESC_v1::nvSciBufObject [inherited]
A handle representing an NvSciBuf Object. Valid when type is CU_EXTERNAL_MEMORY_HANDLE_TYPE_NVSCIBUF

unsigned long long  CUDA_EXTERNAL_MEMORY_HANDLE_DESC_v1::size [inherited]
Size of the memory allocation

CUexternalMemoryHandleTypeCUDA_EXTERNAL_MEMORY_HANDLE_DESC_v1::type [inherited]
Type of the handle

CUDA_EXTERNAL_MEMORY_HANDLE_DESC_v1::@19::@20  CUDA_EXTERNAL_MEMORY_HANDLE_DESC_v1::win32 [inherited]
Win32 handle referencing the semaphore object. Valid when type is one of the following:


CU_EXTERNAL_MEMORY_HANDLE_TYPE_OPAQUE_WIN32

CU_EXTERNAL_MEMORY_HANDLE_TYPE_OPAQUE_WIN32_KMT

CU_EXTERNAL_MEMORY_HANDLE_TYPE_D3D12_HEAP

CU_EXTERNAL_MEMORY_HANDLE_TYPE_D3D12_RESOURCE

CU_EXTERNAL_MEMORY_HANDLE_TYPE_D3D11_RESOURCE

CU_EXTERNAL_MEMORY_HANDLE_TYPE_D3D11_RESOURCE_KMT Exactly one of 'handle' and 'name' must be non-NULL. If type is one of the following: CU_EXTERNAL_MEMORY_HANDLE_TYPE_OPAQUE_WIN32_KMTCU_EXTERNAL_MEMORY_HANDLE_TYPE_D3D11_RESOURCE_KMT then 'name' must be NULL.


---