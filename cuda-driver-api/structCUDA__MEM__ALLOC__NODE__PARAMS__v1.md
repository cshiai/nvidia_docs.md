# CUDA Driver API

[< Previous](structCUDA__LAUNCH__PARAMS__v1.html) | [Next >](structCUDA__MEM__ALLOC__NODE__PARAMS__v2.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.39. CUDA_MEM_ALLOC_NODE_PARAMS_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Memory allocation node parameters


### Public Variables


size_t  accessDescCountconst
                           CUmemAccessDesc
                           * accessDescssize_t  bytesizeCUdeviceptr dptrstruct CUmemPoolProps poolProps

### Variables


size_t  CUDA_MEM_ALLOC_NODE_PARAMS_v1::accessDescCount [inherited]
in: number of memory access descriptors. Must not exceed the number of GPUs.

const

                              CUmemAccessDesc
                              * CUDA_MEM_ALLOC_NODE_PARAMS_v1::accessDescs [inherited]
in: array of memory access descriptors. Used to describe peer GPU access

size_t  CUDA_MEM_ALLOC_NODE_PARAMS_v1::bytesize [inherited]
in: size in bytes of the requested allocation

CUdeviceptrCUDA_MEM_ALLOC_NODE_PARAMS_v1::dptr [inherited]
out: address of the allocation returned by CUDA

struct CUmemPoolPropsCUDA_MEM_ALLOC_NODE_PARAMS_v1::poolProps [inherited]
in: location where the allocation should reside (specified in location). handleTypes must be CU_MEM_HANDLE_TYPE_NONE. IPC is not supported.


---