# CUDA Driver API

[< Previous](structCUmemAccessDesc__v1.html) | [Next >](structCUmemcpy3DOperand__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.71. CUmemAllocationProp_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Specifies the allocation properties for a allocation.


### Public Variables


unsigned char  compressionTypestruct CUmemLocation locationCUmemAllocationHandleType requestedHandleTypesCUmemAllocationType typeunsigned short  usagevoid
                           * win32HandleMetaData

### Variables


unsigned char  CUmemAllocationProp_v1::compressionType [inherited]
Allocation hint for requesting compressible memory. On devices that support Compute Data Compression, compressible memory
                                 can be used to accelerate accesses to data with unstructured sparsity and other compressible data patterns. Applications are
                                 expected to query allocation property of the handle obtained with cuMemCreate using cuMemGetAllocationPropertiesFromHandle to validate if the obtained allocation is compressible or not. Note that compressed memory may not be mappable on all devices.

struct CUmemLocationCUmemAllocationProp_v1::location [inherited]
Location of allocation

CUmemAllocationHandleTypeCUmemAllocationProp_v1::requestedHandleTypes [inherited]
requested CUmemAllocationHandleType

CUmemAllocationTypeCUmemAllocationProp_v1::type [inherited]
Allocation type

unsigned short  CUmemAllocationProp_v1::usage [inherited]
Bitmask indicating intended usage for this allocation

void
                              * CUmemAllocationProp_v1::win32HandleMetaData [inherited]
Windows-specific POBJECT_ATTRIBUTES required when CU_MEM_HANDLE_TYPE_WIN32 is specified. This object attributes structure includes security attributes that define the scope of which exported allocations
                                 may be transferred to other processes. In all other cases, this field is required to be zero.


---