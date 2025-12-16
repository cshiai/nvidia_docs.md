# CUDA Driver API

[< Previous](structCUoffset3D__v1.html) | [Next >](structCUtensorMap.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.81. CUstreamBatchMemOpParams_v1 Union Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Per-operation parameters for [cuStreamBatchMemOp](group__CUDA__MEMOP.html#group__CUDA__MEMOP_1g764c442de9b671f9dec856e8ae531ed1)


### Public Variables


CUstreamBatchMemOpParams_v1::CUstreamMemOpFlushRemoteWritesParams_st  flushRemoteWritesCUstreamBatchMemOpParams_v1::CUstreamMemOpMemoryBarrierParams_st  memoryBarrierCUstreamBatchMemOpType operationCUstreamBatchMemOpParams_v1::CUstreamMemOpWaitValueParams_st  waitValueCUstreamBatchMemOpParams_v1::CUstreamMemOpWriteValueParams_st  writeValue

### Variables


CUstreamBatchMemOpParams_v1::CUstreamMemOpFlushRemoteWritesParams_st  CUstreamBatchMemOpParams_v1::flushRemoteWrites [inherited]
Params for CU_STREAM_MEM_OP_FLUSH_REMOTE_WRITES operations.

CUstreamBatchMemOpParams_v1::CUstreamMemOpMemoryBarrierParams_st  CUstreamBatchMemOpParams_v1::memoryBarrier [inherited]
Params for CU_STREAM_MEM_OP_BARRIER operations.

CUstreamBatchMemOpTypeCUstreamBatchMemOpParams_v1::operation [inherited]
Operation. This is the first field of all the union elemets and acts as a TAG to determine which union member is valid.

CUstreamBatchMemOpParams_v1::CUstreamMemOpWaitValueParams_st  CUstreamBatchMemOpParams_v1::waitValue [inherited]
Params for CU_STREAM_MEM_OP_WAIT_VALUE_32 and CU_STREAM_MEM_OP_WAIT_VALUE_64 operations.

CUstreamBatchMemOpParams_v1::CUstreamMemOpWriteValueParams_st  CUstreamBatchMemOpParams_v1::writeValue [inherited]
Params for CU_STREAM_MEM_OP_WRITE_VALUE_32 and CU_STREAM_MEM_OP_WRITE_VALUE_64 operations.


---