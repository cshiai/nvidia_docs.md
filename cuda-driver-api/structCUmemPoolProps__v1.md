# CUDA Driver API

[< Previous](structCUmemLocation__v1.html) | [Next >](structCUmemPoolPtrExportData__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.77. CUmemPoolProps_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Specifies the properties of allocations made from the pool.


### Public Variables


CUmemAllocationType allocTypeCUmemAllocationHandleType handleTypesstruct CUmemLocation locationsize_t  maxSizeunsigned char  reserved[54]unsigned short  usagevoid
                           * win32SecurityAttributes

### Variables


CUmemAllocationTypeCUmemPoolProps_v1::allocType [inherited]
Allocation type. Currently must be specified as CU_MEM_ALLOCATION_TYPE_PINNED

CUmemAllocationHandleTypeCUmemPoolProps_v1::handleTypes [inherited]
Handle types that will be supported by allocations from the pool.

struct CUmemLocationCUmemPoolProps_v1::location [inherited]
Location where allocations should reside.

size_t  CUmemPoolProps_v1::maxSize [inherited]
Maximum pool size. When set to 0, defaults to a system dependent value.

unsigned char  CUmemPoolProps_v1::reserved[54] [inherited]
reserved for future use, must be 0

unsigned short  CUmemPoolProps_v1::usage [inherited]
Bitmask indicating intended usage for the pool.

void
                              * CUmemPoolProps_v1::win32SecurityAttributes [inherited]
Windows-specific LPSECURITYATTRIBUTES required when CU_MEM_HANDLE_TYPE_WIN32 is specified. This security attribute defines the scope of which exported allocations may be transferred to other processes.
                                 In all other cases, this field is required to be zero.


---