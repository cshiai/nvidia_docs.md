# CUDA Driver API

[< Previous](group__CUDA__EXTRES__INTEROP.html) | [Next >](group__CUDA__EXEC.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.21. Stream Memory Operations


This section describes the stream memory operations of the low-level CUDA driver application programming interface.


Support for the [CU_STREAM_WAIT_VALUE_NOR](group__CUDA__TYPES.html#group__CUDA__TYPES_1ggf16864e8693d888f8178067470001b212f10c357c1882ae7b0b947225c1a0d55) flag can be queried with CU_DEVICE_ATTRIBUTE_CAN_USE_STREAM_WAIT_VALUE_NOR_V2.


Support for the [cuStreamWriteValue64()](group__CUDA__MEMOP.html#group__CUDA__MEMOP_1gc8af1e8b96d7561840affd5217dd6830) and [cuStreamWaitValue64()](group__CUDA__MEMOP.html#group__CUDA__MEMOP_1g6910c1258c5f15aa5d699f0fd60d6933) functions, as well as for the [CU_STREAM_MEM_OP_WAIT_VALUE_64](group__CUDA__TYPES.html#group__CUDA__TYPES_1ggb257b534afdb704b6ebdb99c16a5b2927e4ff0402540ee028226c47858cf8a99) and [CU_STREAM_MEM_OP_WRITE_VALUE_64](group__CUDA__TYPES.html#group__CUDA__TYPES_1ggb257b534afdb704b6ebdb99c16a5b2926e576dc8791fa4abf7a3b36e428cd8de) flags, can be queried with [CU_DEVICE_ATTRIBUTE_CAN_USE_64_BIT_STREAM_MEM_OPS](group__CUDA__TYPES.html#group__CUDA__TYPES_1gge12b8a782bebe21b1ac0091bf9f4e2a320db4c9e8d81eb05a937d4ed5c132575).


Support for both [CU_STREAM_WAIT_VALUE_FLUSH](group__CUDA__TYPES.html#group__CUDA__TYPES_1ggf16864e8693d888f8178067470001b215dd93e7173619c943fae495568f4d771) and [CU_STREAM_MEM_OP_FLUSH_REMOTE_WRITES](group__CUDA__TYPES.html#group__CUDA__TYPES_1ggb257b534afdb704b6ebdb99c16a5b292d4e126a89b57ebf4a213ee1774ed103f) requires dedicated platform hardware features and can be queried with [cuDeviceGetAttribute()](group__CUDA__DEVICE.html#group__CUDA__DEVICE_1g9c3e1414f0ad901d3278a4d6645fc266) and [CU_DEVICE_ATTRIBUTE_CAN_FLUSH_REMOTE_WRITES](group__CUDA__TYPES.html#group__CUDA__TYPES_1gge12b8a782bebe21b1ac0091bf9f4e2a34c702e528f71bf513ee0f3f32878ce9d).


Note that all memory pointers passed as parameters to these operations are device pointers. Where necessary a device pointer should be obtained, for example with [cuMemHostGetDevicePointer()](group__CUDA__MEM.html#group__CUDA__MEM_1g57a39e5cba26af4d06be67fc77cc62f0).


None of the operations accepts pointers to managed memory buffers ([cuMemAllocManaged](group__CUDA__MEM.html#group__CUDA__MEM_1gb347ded34dc326af404aa02af5388a32)).



  Note:
Warning: Improper use of these APIs may deadlock the application. Synchronization ordering established through these APIs is not visible to CUDA. CUDA tasks that are (even indirectly) ordered by these APIs should also have that order expressed with CUDA-visible dependencies such as events. This ensures that the scheduler does not serialize them in an improper order.




### Functions


CUresult cuStreamBatchMemOp (  CUstream stream, unsigned int  count, CUstreamBatchMemOpParams* paramArray, unsigned int  flags )
Batch operations to synchronize the stream via memory operations.

CUresult cuStreamWaitValue32 (  CUstream stream, CUdeviceptr addr, cuuint32_t value, unsigned int  flags )
Wait on a memory location.

CUresult cuStreamWaitValue64 (  CUstream stream, CUdeviceptr addr, cuuint64_t value, unsigned int  flags )
Wait on a memory location.

CUresult cuStreamWriteValue32 (  CUstream stream, CUdeviceptr addr, cuuint32_t value, unsigned int  flags )
Write a value to memory.

CUresult cuStreamWriteValue64 (  CUstream stream, CUdeviceptr addr, cuuint64_t value, unsigned int  flags )
Write a value to memory.


### Functions


CUresult cuStreamBatchMemOp (  CUstream stream, unsigned int  count, CUstreamBatchMemOpParams* paramArray, unsigned int  flags )
Batch operations to synchronize the stream via memory operations.

                                 Parameters



stream
The stream to enqueue the operations in.
count
The number of operations in the array. Must be less than 256.
paramArray
The types and parameters of the individual operations.
flags
Reserved for future expansion; must be 0.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_NOT_SUPPORTED

Description
This is a batch version of cuStreamWaitValue32() and cuStreamWriteValue32(). Batching operations may avoid some performance overhead in both the API call and the device execution versus adding them
                                 to the stream in separate API calls. The operations are enqueued in the order they appear in the array.

See CUstreamBatchMemOpType for the full set of supported operations, and cuStreamWaitValue32(), cuStreamWaitValue64(), cuStreamWriteValue32(), and cuStreamWriteValue64() for details of specific operations.

See related APIs for details on querying support for specific operations.

Note:Warning: Improper use of this API may deadlock the application. Synchronization ordering established through this API is not
                                       visible to CUDA. CUDA tasks that are (even indirectly) ordered by this API should also have that order expressed with CUDA-visible
                                       dependencies such as events. This ensures that the scheduler does not serialize them in an improper order.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuStreamWaitValue32, cuStreamWaitValue64, cuStreamWriteValue32, cuStreamWriteValue64, cuMemHostRegister

CUresult cuStreamWaitValue32 (  CUstream stream, CUdeviceptr addr, cuuint32_t value, unsigned int  flags )
Wait on a memory location.

                                 Parameters



stream
The stream to synchronize on the memory location.
addr
The memory location to wait on.
value
The value to compare with the memory location.
flags
See CUstreamWaitValue_flags.


Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_NOT_SUPPORTED

Description
Enqueues a synchronization of the stream on the given memory location. Work ordered after the operation will block until the
                                 given condition on the memory is satisfied. By default, the condition is to wait for (int32_t)(*addr - value) >= 0, a cyclic
                                 greater-or-equal. Other condition types can be specified via flags.

If the memory was registered via cuMemHostRegister(), the device pointer should be obtained with cuMemHostGetDevicePointer(). This function cannot be used with managed memory (cuMemAllocManaged).

Support for CU_STREAM_WAIT_VALUE_NOR can be queried with cuDeviceGetAttribute() and CU_DEVICE_ATTRIBUTE_CAN_USE_STREAM_WAIT_VALUE_NOR_V2.


Note:Warning: Improper use of this API may deadlock the application. Synchronization ordering established through this API is not
                                       visible to CUDA. CUDA tasks that are (even indirectly) ordered by this API should also have that order expressed with CUDA-visible
                                       dependencies such as events. This ensures that the scheduler does not serialize them in an improper order.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuStreamWaitValue64, cuStreamWriteValue32, cuStreamWriteValue64, cuStreamBatchMemOp, cuMemHostRegister, cuStreamWaitEvent

CUresult cuStreamWaitValue64 (  CUstream stream, CUdeviceptr addr, cuuint64_t value, unsigned int  flags )
Wait on a memory location.

                                 Parameters



stream
The stream to synchronize on the memory location.
addr
The memory location to wait on.
value
The value to compare with the memory location.
flags
See CUstreamWaitValue_flags.


Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_NOT_SUPPORTED

Description
Enqueues a synchronization of the stream on the given memory location. Work ordered after the operation will block until the
                                 given condition on the memory is satisfied. By default, the condition is to wait for (int64_t)(*addr - value) >= 0, a cyclic
                                 greater-or-equal. Other condition types can be specified via flags.

If the memory was registered via cuMemHostRegister(), the device pointer should be obtained with cuMemHostGetDevicePointer().

Support for this can be queried with cuDeviceGetAttribute() and CU_DEVICE_ATTRIBUTE_CAN_USE_64_BIT_STREAM_MEM_OPS.


Note:Warning: Improper use of this API may deadlock the application. Synchronization ordering established through this API is not
                                       visible to CUDA. CUDA tasks that are (even indirectly) ordered by this API should also have that order expressed with CUDA-visible
                                       dependencies such as events. This ensures that the scheduler does not serialize them in an improper order.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuStreamWaitValue32, cuStreamWriteValue32, cuStreamWriteValue64, cuStreamBatchMemOp, cuMemHostRegister, cuStreamWaitEvent

CUresult cuStreamWriteValue32 (  CUstream stream, CUdeviceptr addr, cuuint32_t value, unsigned int  flags )
Write a value to memory.

                                 Parameters



stream
The stream to do the write in.
addr
The device address to write to.
value
The value to write.
flags
See CUstreamWriteValue_flags.


Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_NOT_SUPPORTED

Description
Write a value to memory.
If the memory was registered via cuMemHostRegister(), the device pointer should be obtained with cuMemHostGetDevicePointer(). This function cannot be used with managed memory (cuMemAllocManaged).


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuStreamWriteValue64, cuStreamWaitValue32, cuStreamWaitValue64, cuStreamBatchMemOp, cuMemHostRegister, cuEventRecord

CUresult cuStreamWriteValue64 (  CUstream stream, CUdeviceptr addr, cuuint64_t value, unsigned int  flags )
Write a value to memory.

                                 Parameters



stream
The stream to do the write in.
addr
The device address to write to.
value
The value to write.
flags
See CUstreamWriteValue_flags.


Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_NOT_SUPPORTED

Description
Write a value to memory.
If the memory was registered via cuMemHostRegister(), the device pointer should be obtained with cuMemHostGetDevicePointer().

Support for this can be queried with cuDeviceGetAttribute() and CU_DEVICE_ATTRIBUTE_CAN_USE_64_BIT_STREAM_MEM_OPS.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuStreamWriteValue32, cuStreamWaitValue32, cuStreamWaitValue64, cuStreamBatchMemOp, cuMemHostRegister, cuEventRecord


---