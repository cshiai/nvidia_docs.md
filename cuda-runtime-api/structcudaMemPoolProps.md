# CUDA Runtime API

[< Previous](structcudaMemLocation.html) | [Next >](structcudaMemPoolPtrExportData.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.56. cudaMemPoolProps Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Specifies the properties of allocations made from the pool.


### Public Variables


enumcudaMemAllocationType allocTypeenumcudaMemAllocationHandleType handleTypesstruct cudaMemLocation locationsize_t  maxSizeunsigned char  reserved[54]unsigned short  usagevoid
                           * win32SecurityAttributes

### Variables


enumcudaMemAllocationTypecudaMemPoolProps::allocType [inherited]
Allocation type. Currently must be specified as cudaMemAllocationTypePinned

enumcudaMemAllocationHandleTypecudaMemPoolProps::handleTypes [inherited]
Handle types that will be supported by allocations from the pool.

struct cudaMemLocationcudaMemPoolProps::location [inherited]
Location allocations should reside.

size_t  cudaMemPoolProps::maxSize [inherited]
Maximum pool size. When set to 0, defaults to a system dependent value.

unsigned char  cudaMemPoolProps::reserved[54] [inherited]
reserved for future use, must be 0

unsigned short  cudaMemPoolProps::usage [inherited]
Bitmask indicating intended usage for the pool.

void
                              * cudaMemPoolProps::win32SecurityAttributes [inherited]
Windows-specific LPSECURITYATTRIBUTES required when cudaMemHandleTypeWin32 is specified. This security attribute defines the scope of which exported allocations may be tranferred to other processes.
                                 In all other cases, this field is required to be zero.


---