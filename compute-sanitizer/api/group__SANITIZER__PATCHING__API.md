# Sanitizer Patching API


Functions, types, and enums that implement the Sanitizer Patching API.


## Typedefs


SanitizerCallbackAsyncReduction
Function type for an asynchronous reduction operation on shared memory.

SanitizerCallbackAsyncStore
Function type for an asynchronous store operation on shared memory.

SanitizerCallbackBarrier
Function type for a barrier callback.

SanitizerCallbackBlockEnter
Function type for a CUDA block enter callback.

SanitizerCallbackBlockExit
Function type for a CUDA block exit callback.

SanitizerCallbackBulkCopyGlobalToShared
Function type for a async bulk copy from global to shared memory.

SanitizerCallbackBulkCopySharedToGlobal
Function type for a async bulk copy from shared to global memory.

SanitizerCallbackBulkCopySharedToShared
Function type for a async bulk copy from shared to shered memory.

SanitizerCallbackBulkReductionSharedToGlobal
Function type for a async bulk reduction from shared to global memory.

SanitizerCallbackBulkReductionSharedToShared
Function type for a async bulk reduction from shared to shered memory.

SanitizerCallbackCacheControl
Function type for a cache control instruction callback.

SanitizerCallbackCall
Function type for a function call callback.

SanitizerCallbackClusterBarrierArrive
Function type for a cluster barrier arrive.

SanitizerCallbackClusterBarrierWait
Function type for a cluster barrier wait.

SanitizerCallbackCudaBarrier
Function type for a CUDA Barrier action callback.

SanitizerCallbackCudaBarrierAttempt
Function type for a CUDA Barrier action callback.

SanitizerCallbackDeviceSideFree
Function type for a device-side free call.

SanitizerCallbackDeviceSideMalloc
Function type for a device-side malloc call.

SanitizerCallbackMatrixMemoryAccess
Function type for a matrix shared memory access callback.

SanitizerCallbackMemcpyAsync
Function type for a global to shared memory asynchronous copy.

SanitizerCallbackMemcpyAsyncBarrier
Function type for a cuda barrier used for mbarrier completion.

SanitizerCallbackMemoryAccess
Function type for a memory access callback.

SanitizerCallbackMemsetShared
Function type for a memset on shared memory.

SanitizerCallbackPipelineCommit
Function type for a pipeline commit.

SanitizerCallbackPipelineWait
Function type for a pipeline wait.

SanitizerCallbackRet
Function type for a function return callback.

SanitizerCallbackSetSmemSize
Function type for setting the shared memory size allocated to a block.

SanitizerCallbackShfl
Function type for a shfl callback.

SanitizerCallbackSyncwarp
Function type for a syncwarp callback.

SanitizerCallbackTensorCoreBarrier
Function type for a Blackwell tensor core barrier.

SanitizerCallbackWarpgroupFence
Function type for a warpgroup MMA fence.

SanitizerCallbackWarpgroupMMAAsync
Function type for a warpgroup aligned async MMA.

SanitizerCallbackWarpgroupWaitGroup
Function type for a warpgroup MMA wait group.

Sanitizer_LaunchHandle

## Enumerations


SanitizerPatchResult
Sanitizer patch result codes.

Sanitizer_BarrierFlags
Flags describing a barrier.

Sanitizer_CacheControlInstructionKind
Cache control action.

Sanitizer_CallFlags
Flags describing a function call.

Sanitizer_CudaBarrierInstructionKind
CUDA Barrier action kind.

Sanitizer_DeviceMemoryFlags
Flags describing a memory access.

Sanitizer_FunctionLoadedStatusSanitizer_InstructionId
Instrumentation.

Sanitizer_WarpgroupMMAAsyncFlags
Flags describing a warpgroup aligned MMA async.


## Functions


SanitizerResult sanitizerAddPatches(const void *image, CUcontext ctx)
Load a module containing patches that can be used by the patching API.

SanitizerResult sanitizerAddPatchesFromFile(const char *filename, CUcontext ctx)
Load a module containing patches that can be used by the patching API.

SanitizerResult sanitizerGetCallbackPcAndSize(CUcontext ctx, const char *deviceCallbackName, uint64_t *pc, uint64_t *size)
Get PC and size of a device callback.

SanitizerResult sanitizerGetFunctionLoadedStatus(CUfunction func, Sanitizer_FunctionLoadedStatus *loadingStatus)
Get the loading status of a function.

SanitizerResult sanitizerGetFunctionPcAndSize(CUmodule module, const char *functionName, uint64_t *pc, uint64_t *size)
Get PC and size of a CUDA function.

SanitizerResult sanitizerPatchInstructions(const Sanitizer_InstructionId instructionId, CUmodule module, const char *deviceCallbackName)
Set instrumentation points and patches to be applied in a module.

SanitizerResult sanitizerPatchModule(CUmodule module)
Perform the actual instrumentation of a module.

SanitizerResult sanitizerSetCallbackData(CUfunction kernel, const void *userdata)
Specifies the user data pointer for callbacks.

SanitizerResult sanitizerSetDeviceGraphData(CUgraphExec graphExec, Sanitizer_StreamHandle stream, const void *userdata)
Specifies the user data pointer accessible from callbacks in the device-launched graphs launched by the specified host-launched graphExec.

SanitizerResult sanitizerSetLaunchCallbackData(Sanitizer_LaunchHandle launch, CUfunction kernel, Sanitizer_StreamHandle stream, const void *userdata)
Specifies the user data pointer for callbacks.

SanitizerResult sanitizerUnpatchModule(CUmodule module)
Remove existing instrumentation of a module.


## Typedefs


typedef SanitizerPatchResult (*SanitizerCallbackAsyncReduction)(void *userdata, uint64_t pc, uint32_t address, uint32_t mbarAddress, uint32_t accessSize)
Function type for an asynchronous reduction operation on shared memory.
This can be generated by a red.async PTX instruction.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param address:
Destination address in shared memory.

Param mbarAddress:
Address of the mbarrier object.

Param accessSize:
Size of the access in bytes. Valid values are 4 and 8.


typedef SanitizerPatchResult (*SanitizerCallbackAsyncStore)(void *userdata, uint64_t pc, uint32_t address, uint32_t mbarAddress, void *pNewValue, uint32_t accessSize)
Function type for an asynchronous store operation on shared memory.
This can be generated by a st.async PTX instruction.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param address:
Destination address in shared memory.

Param mbarAddress:
Address of the mbarrier object.

Param pNewValue:
Pointer to the new value being written.

Param accessSize:
Size of the access in bytes. Valid values are 4 and 8.


typedef SanitizerPatchResult (*SanitizerCallbackBarrier)(void *userdata, uint64_t pc, uint32_t barIndex, uint32_t threadCount, uint32_t flags)
Function type for a barrier callback.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param barIndex:
Barrier index.

Param threadCount:
Number of expected threads (must be a multiple of the warp size).

Param flags:
Contains information about the barrier. See Sanitizer_BarrierFlags to interpret this value. 0 means that all threads are participating in the barrier.


typedef SanitizerPatchResult (*SanitizerCallbackBlockEnter)(void *userdata, uint64_t pc)
Function type for a CUDA block enter callback.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the entry point of the block.


typedef SanitizerPatchResult (*SanitizerCallbackBlockExit)(void *userdata, uint64_t pc)
Function type for a CUDA block exit callback.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.


typedef SanitizerPatchResult (*SanitizerCallbackBulkCopyGlobalToShared)(void *userdata, uint64_t pc, uint64_t src, uint32_t dst, uint32_t barrier, uint32_t data, uint32_t isMulticast)
Function type for a async bulk copy from global to shared memory.
This can be generated by a cp.async.bulk.shared::cluster.global instruction.

All the active threads in a warp have the same parameter values.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param src:
Source global memory address.

Param dst:
Destination DSMEM address.

Param barrier:
DSMEM address for the associated mbarrier completion mechanism.

Param data:
Contains in bits 0:15 the number of 16 bytes blocks requested and in bits 16:31 the multicast mask.

Param isMulticast:
Boolean value indicating if the operation is a multicast.


typedef SanitizerPatchResult (*SanitizerCallbackBulkCopySharedToGlobal)(void *userdata, uint64_t pc, uint64_t dst, uint32_t src, uint32_t numBlocks)
Function type for a async bulk copy from shared to global memory.
This can be generated by a cp.async.bulk.global.shared::cta instruction.

All the active threads in a warp have the same parameter values.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param dst:
Destination global memory address.

Param src:
Source DSMEM address.

Param numBlocks:
Contains the number of 16 bytes blocks requested to be copied.


typedef SanitizerPatchResult (*SanitizerCallbackBulkCopySharedToShared)(void *userdata, uint64_t pc, uint32_t src, uint32_t dst, uint32_t barrier, uint32_t numBlocks)
Function type for a async bulk copy from shared to shered memory.
This can be generated by a cp.async.bulk.shared::cluster.shared::cta instruction.

All the active threads in a warp have the same parameter values.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param src:
Source DSMEM address.

Param dst:
Destination DSMEM address.

Param barrier:
DSMEM address for the associated mbarrier completion mechanism.

Param numBlocks:
Contains the number of 16 bytes blocks requested to be copied.


typedef SanitizerPatchResult (*SanitizerCallbackBulkReductionSharedToGlobal)(void *userdata, uint64_t pc, uint64_t dst, uint32_t src, uint32_t numBlocks)
Function type for a async bulk reduction from shared to global memory.
This can be generated by a cp.reduce.async.bulk.global.shared::cta.bulk_group instruction.

All the active threads in a warp have the same parameter values.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param dst:
Destination DSMEM address.

Param src:
Source DSMEM address.

Param barrier:
DSMEM address for the associated mbarrier completion mechanism.

Param numBlocks:
Contains the number of 16 bytes blocks requested to be copied.


typedef SanitizerPatchResult (*SanitizerCallbackBulkReductionSharedToShared)(void *userdata, uint64_t pc, uint32_t src, uint32_t dst, uint32_t barrier, uint32_t numBlocks)
Function type for a async bulk reduction from shared to shered memory.
This can be generated by a cp.reduce.async.bulk.shared::cluster.shared::cta.mbarrier::complete_tx::bytes instruction.

All the active threads in a warp have the same parameter values.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param src:
Source DSMEM address.

Param dst:
Destination DSMEM address.

Param barrier:
DSMEM address for the associated mbarrier completion mechanism.

Param numBlocks:
Contains the number of 16 bytes blocks requested to be copied.


typedef SanitizerPatchResult (*SanitizerCallbackCacheControl)(void *userdata, uint64_t pc, void *address, Sanitizer_CacheControlInstructionKind kind)
Function type for a cache control instruction callback.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param address:
Address of the memory being controlled.

Param kind:
Type of cache control. See Sanitizer_CacheControlInstructionKind.


typedef SanitizerPatchResult (*SanitizerCallbackCall)(void *userdata, uint64_t pc, uint64_t targetPc, uint32_t flags)
Function type for a function call callback.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param targetPc:
PC where the called function is located.

Param flags:
Contains information about the function call.


typedef SanitizerPatchResult (*SanitizerCallbackClusterBarrierArrive)(void *userdata, uint64_t pc)
Function type for a cluster barrier arrive.
This can be generated by a cg::this_cluster().sync() (C++ API), or a barrier.cluster.arrive (PTX API).

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.


typedef SanitizerPatchResult (*SanitizerCallbackClusterBarrierWait)(void *userdata, uint64_t pc)
Function type for a cluster barrier wait.
This can be generated by a cg::this_cluster().sync() (C++ API), or a barrier.cluster.wait (PTX API).

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Retval SANITIZER_PATCH_SUCCESS:
Warp execution continues.

Retval SANITIZER_PATCH_ERROR:
Warp should be exited.


typedef SanitizerPatchResult (*SanitizerCallbackCudaBarrier)(void *userdata, uint64_t pc, void *barrier, uint32_t kind, uint32_t data)
Function type for a CUDA Barrier action callback.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param barrier:
Barrier address which can be used as a unique identifier.

Param kind:
Barrier action type. See Sanitizer_CudaBarrierInstructionKind.

Param data:
Barrier data. This is specific to each action type, refer to Sanitizer_CudaBarrierInstructionKind.


typedef SanitizerPatchResult (*SanitizerCallbackCudaBarrierAttempt)(void *userdata, uint64_t pc, void *barrier, uint32_t kind, uint32_t data, uint32_t result)
Function type for a CUDA Barrier action callback.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param barrier:
Barrier address which can be used as a unique identifier.

Param kind:
Barrier action type. See Sanitizer_CudaBarrierInstructionKind.

Param data:
Barrier data. This is specific to each action type, refer to Sanitizer_CudaBarrierInstructionKind.

Param result:
In case of a barrier wait, this indicates whether the wait was successful or not.


typedef SanitizerPatchResult (*SanitizerCallbackDeviceSideFree)(void *userdata, uint64_t pc, void *ptr)
Function type for a device-side free call.

Note
This is called prior to the actual call.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param ptr:
Pointer passed to device-side free.


typedef SanitizerPatchResult (*SanitizerCallbackDeviceSideMalloc)(void *userdata, uint64_t pc, void *allocatedPtr, uint64_t allocatedSize)
Function type for a device-side malloc call.

Note
This is called after the call has completed.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param allocatedPtr:
Pointer returned by device-side malloc.

Param allocatedSize:
Size requested by the user to device-side malloc.


typedef SanitizerPatchResult (*SanitizerCallbackMatrixMemoryAccess)(void *userdata, uint64_t pc, uint32_t address, uint32_t accessSize, uint32_t flags, uint32_t count, const void *pNewValue)
Function type for a matrix shared memory access callback.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param address:
Address of the shared memory being read or written. This is an offset within the shared memory window.

Param accessSize:
Size of the access in bytes. Valid value is 16.

Param flags:
Contains information about the type of access. See Sanitizer_DeviceMemoryFlags to interpret this value.

Param count:
Number of matrices accessed.

Param pNewValue:
Pointer to the new value being written if the access is a write. If the access is a read or an atomic, the pointer will be NULL.


typedef SanitizerPatchResult (*SanitizerCallbackMemcpyAsync)(void *userdata, uint64_t pc, void *src, uint32_t dst, uint32_t accessSize)
Function type for a global to shared memory asynchronous copy.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param src:
Address of the global memory being read. This can be NULL if src-size is 0.

Param dst:
Address of the shared memory being written. This is an offset within the shared memory window.

Param accessSize:
Size of the access in bytes. Valid values are 4, 8 and 16.


typedef SanitizerPatchResult (*SanitizerCallbackMemcpyAsyncBarrier)(void *userdata, uint64_t pc, uint32_t barrier)
Function type for a cuda barrier used for mbarrier completion.
This can be generated by cp.async.mbarrier.arrive.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param barrier:
Shared memory address of the barrier.


typedef SanitizerPatchResult (*SanitizerCallbackMemoryAccess)(void *userdata, uint64_t pc, void *ptr, uint32_t accessSize, uint32_t flags, const void *pData)
Function type for a memory access callback.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param ptr:
Address of the memory being accessed. For local or shared memory access, this is the offset within the local or shared memory window.

Param accessSize:
Size of the access in bytes. Valid values are 1, 2, 4, 8, and 16.

Param flags:
Contains information about the type of access. See Sanitizer_DeviceMemoryFlags to interpret this value.

Param pData:
Pointer which value depends on the type of access:
If the access is a write, pData points to the new value being written.
If the access is a read and pData is not NULL, then it points to a 32-bit mask of loaded bytes being used (padding bytes will not appear).
If the access is an atomic, the pointer will be NULL.


typedef SanitizerPatchResult (*SanitizerCallbackMemsetShared)(void *userdata, uint64_t pc, uint32_t dst, uint32_t numBlocks)
Function type for a memset on shared memory.
This can be generated by st.bulk.

All the active threads in a warp have the same parameter values.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param dst:
Destination shared memory address.

Param numBlocks:
Number of 8 byte blocks to be set to zero.


typedef SanitizerPatchResult (*SanitizerCallbackPipelineCommit)(void *userdata, uint64_t pc)
Function type for a pipeline commit.
This can be generated by a pipeline::producer_commit (C++ API), a pipeline_commit (C API) or a cp.async.commit_group (PTX API).

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.


typedef SanitizerPatchResult (*SanitizerCallbackPipelineWait)(void *userdata, uint64_t pc, uint32_t groups)
Function type for a pipeline wait.
This can be generated by a pipeline::consumer_wait (C++ API), a pipeline_wait_prior (C API), cp.async.wait_group or cp.async.wait_all (PTX API).

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param groups:
Number of groups the pipeline will wait for. 0 is used to wait for all groups.


typedef SanitizerPatchResult (*SanitizerCallbackRet)(void *userdata, uint64_t pc)
Function type for a function return callback.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.


typedef SanitizerPatchResult (*SanitizerCallbackSetSmemSize)(void *userdata, uint64_t pc, uint32_t size)
Function type for setting the shared memory size allocated to a block.
This can be generated by a setsmemsize.sync instruction.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param size:
Requested size in bytes.


typedef SanitizerPatchResult (*SanitizerCallbackShfl)(void *userdata, uint64_t pc)
Function type for a shfl callback.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.


typedef SanitizerPatchResult (*SanitizerCallbackSyncwarp)(void *userdata, uint64_t pc, uint32_t mask)
Function type for a syncwarp callback.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param mask:
Thread mask passed to __syncwarp().


typedef SanitizerPatchResult (*SanitizerCallbackTensorCoreBarrier)(void *userdata, uint64_t pc, uint32_t barrier, uint32_t isMulticast, uint32_t multicastMask)
Function type for a Blackwell tensor core barrier.
This can be generated by a tcgen05.commit instruction.

All the active threads in a warp have the same parameter values.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param barrier:
DSMEM address for the associated mbarrier completion mechanism.

Param isMulticast:
Boolean value indicating if the operation is a multicast.

Param multicastMask:
Multicast mask, if isMulticast is true.


typedef SanitizerPatchResult (*SanitizerCallbackWarpgroupFence)(void *userdata, uint64_t pc, uint32_t warpMask)
Function type for a warpgroup MMA fence.
This can be generated by a wgmma.fence in PTX.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param warpMask:
Mask of threads that will perform the fence operation. Expected values are either 0x0 or 0xffffffff (full). The value is expected to be the same across the warpgroup. Other values can be reported but signal a programming error in the target application.


typedef SanitizerPatchResult (*SanitizerCallbackWarpgroupMMAAsync)(void *userdata, uint64_t pc, uint32_t addressMatrixA, uint32_t sizeMatrixA, uint32_t addressMatrixB, uint32_t sizeMatrixB, uint32_t flags, uint32_t warpMask)
Function type for a warpgroup aligned async MMA.
This can be generated by a wgmma.mma_async in PTX.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param addressMatrixA:
Address in shared memory of the matrix A being read. This field is only valid if sizeMatrixA is non-zero and warpMask is full.

Param sizeMatrixA:
Size of the matrix A in shared memory. A value of 0 means that the matrix A is read from registers instead.

Param addressMatrixB:
Address in shared memory of the matrix B being read. This field is only valid if warpMask is full.

Param sizeMatrixB:
Size of the matrix B in shared memory. The value will always be non-zero.

Param flags:
Type is Sanitizer_WarpgroupMMAAsyncFlags. Provide information about the access. These flags are to be taken into account even if the warpMask is zero.

Param warpMask:
Mask of threads that will perform the operation and read the operands. Expected values are either 0x0 or 0xffffffff (full). The value is expected to be the same across the warpgroup. Other values can be reported but signal a programming error in the target application.


typedef SanitizerPatchResult (*SanitizerCallbackWarpgroupWaitGroup)(void *userdata, uint64_t pc, uint32_t numGroups, uint32_t warpMask)
Function type for a warpgroup MMA wait group.
This can be generated by a wgmma.wait_group in PTX.

Param userdata:
Pointer to user data. See sanitizerPatchModule.

Param pc:
Program counter of the patched instruction.

Param numGroups:
Maximum number of group that will be left pending after the operation. A value of zero means that all MMA async of the warpgroup are guaranteed to have completed after the operation.

Param warpMask:
Mask of threads for which the expected values are either 0x0 or 0xffffffff (full). The value is expected to be the same across the warpgroup. Other values can be reported but signal a programming error in the target application. If the value is valid, the value has no influence on the operation.


typedef struct Sanitizer_Launch_st *Sanitizer_LaunchHandle

## Enumerations


enum SanitizerPatchResult
Sanitizer patch result codes.
Error and result codes returned by Sanitizer patches. If a patch returns SANITIZER_PATCH_ERROR, the full warp which the thread belongs to will be exited.
Values:

enumerator SANITIZER_PATCH_SUCCESS
No error.

enumerator SANITIZER_PATCH_ERROR
An error was detected in the patch.

enumerator SANITIZER_PATCH_FORCE_INT


enum Sanitizer_BarrierFlags
Flags describing a barrier.
Flags describing a barrier. These values are to be or-combined in the value of flags for a SanitizerCallbackBarrier callback.
Values:

enumerator SANITIZER_BARRIER_FLAG_NONE
Empty flag.

enumerator SANITIZER_BARRIER_FLAG_UNALIGNED_ALLOWED
Specifies that the barrier can be called unaligned.
This flag is only valid on SM 7.0 and above.

enumerator SANITIZER_BARRIER_FLAG_FORCE_INT


enum Sanitizer_CacheControlInstructionKind
Cache control action.
Values:

enumerator SANITIZER_CACHE_CONTROL_INVALID
Invalid action ID.

enumerator SANITIZER_CACHE_CONTROL_L1_PREFETCH
Prefetch to L1.

enumerator SANITIZER_CACHE_CONTROL_L2_PREFETCH
Prefetch to L2.

enumerator SANITIZER_CACHE_CONTROL_FORCE_INT


enum Sanitizer_CallFlags
Flags describing a function call.
Flags describing a function call. These values are to be or-combined in the value of flags for a SanitizerCallbackCall callback.
Values:

enumerator SANITIZER_CALL_FLAG_NONE
Empty flag.

enumerator SANITIZER_CALL_FLAG_UNALIGNED_ALLOWED
Specifies that barriers within this function call can be called unaligned.
This flag is only valid on SM 7.0 and above.

enumerator SANITIZER_CALL_FLAG_FORCE_INT


enum Sanitizer_CudaBarrierInstructionKind
CUDA Barrier action kind.
Refer to the CUDA Barrier interface section of the CUDA toolkit documentation for a more extensive description of these actions.
Values:

enumerator SANITIZER_CUDA_BARRIER_INVALID
Invalid action ID.

enumerator SANITIZER_CUDA_BARRIER_INIT
Barrier initialization.

enumerator SANITIZER_CUDA_BARRIER_ARRIVE
Barrier arrive operation.
On Hopper and newer architectures, barrier data is the count argument to the arrive-on operation.

enumerator SANITIZER_CUDA_BARRIER_ARRIVE_DROP
Barrier arrive and drop operation.
On Hopper and newer architectures, barrier data is the count argument to the arrive-on operation.

enumerator SANITIZER_CUDA_BARRIER_ARRIVE_NOCOMPLETE
Barrier arrive operation without phase completion.
Barrier data is the count argument to the arrive-on operation.

enumerator SANITIZER_CUDA_BARRIER_ARRIVE_DROP_NOCOMPLETE
Barrier arrive and drop operation without phase completion.
Barrier data is the count argument to the arrive-on operation.

enumerator SANITIZER_CUDA_BARRIER_WAIT
Barrier wait operation.

enumerator SANITIZER_CUDA_BARRIER_INVALIDATE
Barrier invalidation.

enumerator SANITIZER_CUDA_BARRIER_CP_ASYNC_ARRIVE
Barrier arrive operation issued from cp.async.mbarrier.arrive.

enumerator SANITIZER_CUDA_BARRIER_CP_ASYNC_ARRIVE_NO_INC
Barrier arrive operation issued from cp.async.mbarrier.arrive.noinc.

enumerator SANITIZER_CUDA_BARRIER_FORCE_INT


enum Sanitizer_DeviceMemoryFlags
Flags describing a memory access.
Flags describing a memory access. These values are to be or-combined in the value of flags for a SanitizerCallbackMemoryAccess callback.
Values:

enumerator SANITIZER_MEMORY_DEVICE_FLAG_NONE
Empty flag.

enumerator SANITIZER_MEMORY_DEVICE_FLAG_READ
Specifies that the access is a read.

enumerator SANITIZER_MEMORY_DEVICE_FLAG_WRITE
Specifies that the access is a write.

enumerator SANITIZER_MEMORY_DEVICE_FLAG_ATOMSYS
Specifies that the access is a system-scoped atomic.

enumerator SANITIZER_MEMORY_DEVICE_FLAG_PREFETCH
Specifies that the access is a cache prefetch.

enumerator SANITIZER_MEMORY_DEVICE_FLAG_FORCE_INT


enum Sanitizer_FunctionLoadedStatus
Values:

enumerator SANITIZER_FUNCTION_NOT_LOADED
The function is not loaded.

enumerator SANITIZER_FUNCTION_PARTIALLY_LOADED
The function is being loaded.

enumerator SANITIZER_FUNCTION_LOADED
The function is fully loaded.

enumerator SANITIZER_FUNCTION_LOADED_FORCE_INT


enum Sanitizer_InstructionId
Instrumentation.
Instrumentation. Every entry represent an instruction type or a function call where a callback patch can be inserted.
Values:

enumerator SANITIZER_INSTRUCTION_INVALID
Invalid instruction ID.

enumerator SANITIZER_INSTRUCTION_BLOCK_ENTER
CUDA block enter.
This is called prior to any user code. The type of the callback must be SanitizerCallbackBlockEnter.

enumerator SANITIZER_INSTRUCTION_BLOCK_EXIT
CUDA block exit.
This is called after all user code has executed. The type of the callback must be SanitizerCallbackBlockExit.

enumerator SANITIZER_INSTRUCTION_GLOBAL_MEMORY_ACCESS
Global Memory Access.
This can be a store, load or atomic operation. The type of the callback must be SanitizerCallbackMemoryAccess.

enumerator SANITIZER_INSTRUCTION_SHARED_MEMORY_ACCESS
Shared Memory Access.
This can be a store, load or atomic operation. The type of the callback must be SanitizerCallbackMemoryAccess.

enumerator SANITIZER_INSTRUCTION_LOCAL_MEMORY_ACCESS
Local Memory Access.
This can be a store or load operation. The type of the callback must be SanitizerCallbackMemoryAccess.

enumerator SANITIZER_INSTRUCTION_BARRIER
Barrier.
The type of the callback must be SanitizerCallbackBarrier.

enumerator SANITIZER_INSTRUCTION_SYNCWARP
Syncwarp.
The type of the callback must be SanitizerCallbackSyncwarp.

enumerator SANITIZER_INSTRUCTION_SHFL
Shfl.
The type of the callback must be SanitizerCallbackShfl.

enumerator SANITIZER_INSTRUCTION_CALL
Function call.
The type of the callback must be SanitizerCallbackCall.

enumerator SANITIZER_INSTRUCTION_RET
Function return.
The type of the callback must be SanitizerCallbackRet.

enumerator SANITIZER_INSTRUCTION_DEVICE_SIDE_MALLOC
Device-side malloc.
The type of the callback must be SanitizerCallbackDeviceSideMalloc.

enumerator SANITIZER_INSTRUCTION_DEVICE_SIDE_FREE
Device-side free.
The type of the callback must be SanitizerCallbackDeviceSideFree.

enumerator SANITIZER_INSTRUCTION_CUDA_BARRIER
CUDA Barrier operation.
The type of the callback must be SanitizerCallbackCudaBarrier.

enumerator SANITIZER_INSTRUCTION_MEMCPY_ASYNC
Global to shared memory asynchronous copy.
The type of the callback must be SanitizerCallbackMemcpyAsync.

enumerator SANITIZER_INSTRUCTION_PIPELINE_COMMIT
Pipeline commit.
The type of the callback must be SanitizerCallbackPipelineCommit.

enumerator SANITIZER_INSTRUCTION_PIPELINE_WAIT
Pipeline wait.
The type of the callback must be SanitizerCallbackPipelineWait.

enumerator SANITIZER_INSTRUCTION_REMOTE_SHARED_MEMORY_ACCESS
Remote Shared Memory Access.
This can be a store or load operation. The type of the callback must be SanitizerCallbackMemoryAccess.

enumerator SANITIZER_INSTRUCTION_DEVICE_ALIGNED_MALLOC
Device-side aligned malloc.
The type of the callback must be SanitizerCallbackDeviceSideMalloc.

enumerator SANITIZER_INSTRUCTION_MATRIX_MEMORY_ACCESS
Matrix shared memory access.
The type of the callback must be SanitizerCallbackMatrixMemoryAccess.

enumerator SANITIZER_INSTRUCTION_CACHE_CONTROL
Cache control instruction.
The type of the callback must be SanitizerCallbackCacheControl.

enumerator SANITIZER_INSTRUCTION_CLUSTER_BARRIER_ARRIVE
Cluster barrier arrive instruction.
The type of the callback must be SanitizerCallbackClusterBarrierArrive.

enumerator SANITIZER_INSTRUCTION_CLUSTER_BARRIER_WAIT
Cluster barrier wait instruction.
The type of the callback must be SanitizerCallbackClusterBarrierWait.

enumerator SANITIZER_INSTRUCTION_WARPGROUP_MMA_ASYNC
Warpgroup aligned async MMA instruction.
The type of the callback must be SanitizerCallbackWarpgroupMMAAsync.

enumerator SANITIZER_INSTRUCTION_WARPGROUP_WAIT_GROUP
Warpgroup wait MMA group instruction.
The type of the callback must be SanitizerCallbackWarpgroupWaitGroup.

enumerator SANITIZER_INSTRUCTION_WARPGROUP_FENCE
Warpgroup fence instruction.
The type of the callback must be SanitizerCallbackWarpgroupFence.

enumerator SANITIZER_INSTRUCTION_ASYNC_STORE
Asynchronous store instruction.
The type of the callback must be SanitizerCallbackAsyncStore.

enumerator SANITIZER_INSTRUCTION_ASYNC_REDUCTION
Asynchronous reduction instruction.
The type of the callback must be SanitizerCallbackAsyncReduction.

enumerator SANITIZER_INSTRUCTION_SET_SHARED_MEMORY_SIZE
Set the shared memory size allocated to a block instruction.
The type of the callback must be SanitizerCallbackSetSmemSize.

enumerator SANITIZER_INSTRUCTION_BARRIER_RELEASE
Barrier after it is released.
The type of the callback must be SanitizerCallbackBarrier.

enumerator SANITIZER_INSTRUCTION_BULK_COPY_GLOBAL_TO_SHARED
Bulk copy instruction from global to shared memory.
The type of the callback must be SanitizerCallbackBulkCopyGlobalToShared.

enumerator SANITIZER_INSTRUCTION_TENSOR_CORE_BARRIER
Tensor Core barrier.
The type of the callback must be SanitizerCallbackTensorCoreBarrier.

enumerator SANITIZER_INSTRUCTION_MEMSET_SHARED
Bulk copy instruction from global to shared memory.
The type of the callback must be SanitizerCallbackMemsetShared.

enumerator SANITIZER_INSTRUCTION_SYNCWARP_RELEASE
Syncwarp after it is released.
The type of the callback must be SanitizerCallbackSyncwarp.

enumerator SANITIZER_INSTRUCTION_MEMCPY_ASYNC_BARRIER
Usage of a Cuda Barrier for memcpy async completion.
The type of the callback must be SanitizerCallbackMemcpyAsyncBarrier.

enumerator SANITIZER_INSTRUCTION_BULK_COPY_SHARED_TO_GLOBAL
Bulk copy instruction from shared to global memory.
The type of the callback must be SanitizerCallbackBulkCopyGSharedToGlobal.

enumerator SANITIZER_INSTRUCTION_BULK_COPY_SHARED_TO_SHARED
Bulk copy instruction from shared to shared memory.
The type of the callback must be SanitizerCallbackBulkCopySharedToShared.

enumerator SANITIZER_INSTRUCTION_BULK_REDUCTION_SHARED_TO_GLOBAL
Bulk reduction instruction from shared to global memory.
The type of the callback must be SanitizerCallbackBulkReductionSharedToGlobal.

enumerator SANITIZER_INSTRUCTION_BULK_REDUCTION_SHARED_TO_SHARED
Bulk reduction instruction from shared to shared memory.
The type of the callback must be SanitizerCallbackBulkReductionSharedToShared.

enumerator SANITIZER_INSTRUCTION_CUDA_BARRIER_ATTEMPT
CUDA Barrier operation (potentially unsuccessful).
The type of the callback must be SanitizerCallbackCudaBarrierAttempt.

enumerator SANITIZER_INSTRUCTION_CLUSTER_BARRIER_WAIT_ENTRY
Entering cluster barrier wait instruction.
The type of the callback must be SanitizerCallbackClusterBarrierWait.

enumerator SANITIZER_INSTRUCTION_RESERVED

enumerator SANITIZER_INSTRUCTION_FORCE_INT


enum Sanitizer_WarpgroupMMAAsyncFlags
Flags describing a warpgroup aligned MMA async.
Flags describing a warpgroup aligned MMA async. These values are to be or-combined in the value of flags for a SanitizerCallbackWarpgroupMMAAsync callback.
Values:

enumerator SANITIZER_WARPGROUP_MMA_ASYNC_FLAG_NONE
Empty flag.

enumerator SANITIZER_WARPGROUP_MMA_ASYNC_FLAG_COMMIT_GROUP
Specifies that the MMA async delimits a MMA async group of which it is the last instruction.
Please refer to the PTX documentation for wgmma_async.commit_group for more details. This property is valid even if the warpMask is zero.

enumerator SANITIZER_WARPGROUP_MMA_ASYNC_FLAG_FORCE_INT


## Functions


SanitizerResult sanitizerAddPatches(const void *image, CUcontext ctx)
Load a module containing patches that can be used by the patching API.

Note
Thread-safety: an API user must serialize access to sanitizerAddPatchesFromFile, sanitizerAddPatches, sanitizerPatchInstructions, and sanitizerPatchModule. For example if sanitizerAddPatches(image) and sanitizerPatchInstruction(*, *, cbName) are called concurrently and cbName is intended to be found in the loaded image, the results are undefined.

Note
The patches loaded are only valid for the specified CUDA context.

Parameters:

image – Pointer to module data to load. This API supports the same module formats as the cuModuleLoadData and cuModuleLoadFatBinary functions from the CUDA driver API.
ctx – CUDA context in which to load the patches. If ctx is NULL, the current context will be used.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_NOT_INITIALIZED – if unable to initialize the sanitizer.
SANITIZER_ERROR_INVALID_PARAMETER – if image does not point to a valid CUDA module.


SanitizerResult sanitizerAddPatchesFromFile(

const char *filename,
CUcontext ctx,

)
Load a module containing patches that can be used by the patching API.

Note
Thread-safety: an API user must serialize access to sanitizerAddPatchesFromFile, sanitizerAddPatches, sanitizerPatchInstructions, and sanitizerPatchModule. For example if sanitizerAddPatchesFromFile(filename) and sanitizerPatchInstruction(*, *, cbName) are called concurrently and cbName is intended to be found in the loaded module, the results are undefined.

Note
The patches loaded are only valid for the specified CUDA context.

Parameters:

filename – Path to the module file. This API supports the same module formats as the cuModuleLoad function from the CUDA driver API.
ctx – CUDA context in which to load the patches. If ctx is NULL, the current context will be used.

Return values:

SANITIZER_SUCCESS – on success
SANITIZER_ERROR_NOT_INITIALIZED – if unable to initialize the sanitizer
SANITIZER_ERROR_INVALID_PARAMETER – if filename is not a path to a valid CUDA module.


SanitizerResult sanitizerGetCallbackPcAndSize(

CUcontext ctx,
const char *deviceCallbackName,
uint64_t *pc,
uint64_t *size,

)
Get PC and size of a device callback.

Parameters:

ctx – [in] CUDA context in which the patches were loaded. If ctx is NULL, the current context will be used.
deviceCallbackName – [in] device function callback name.
pc – [out] Callback PC returned.
size – [out] Callback size returned.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_INVALID_PARAMETER – if deviceCallbackName function cannot be located, if pc is NULL or if size is NULL.


SanitizerResult sanitizerGetFunctionLoadedStatus(

CUfunction func,
Sanitizer_FunctionLoadedStatus *loadingStatus,

)
Get the loading status of a function.
Requires a driver version >=515.

Parameters:

func – [in] CUDA function for which the loading status is queried.
loadingStatus – [out] Loading status returned.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_INVALID_PARAMETER – if func is NULL or if loadingStatus is NULL.
SANITIZER_ERROR_NOT_SUPPORTED – if the loading status cannot be queried with this driver version.


SanitizerResult sanitizerGetFunctionPcAndSize(

CUmodule module,
const char *functionName,
uint64_t *pc,
uint64_t *size,

)
Get PC and size of a CUDA function.

Parameters:

module – [in] CUDA module containing the function.
functionName – [in] CUDA function name.
pc – [out] Function start program counter (PC) returned.
size – [out] Function size in bytes returned.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_INVALID_PARAMETER – if functionName function. cannot be located, if pc is NULL or if size is NULL.


SanitizerResult sanitizerPatchInstructions(

const Sanitizer_InstructionId instructionId,
CUmodule module,
const char *deviceCallbackName,

)
Set instrumentation points and patches to be applied in a module.
Mark that all instrumentation points matching instructionId are to be patched in order to call the device function identified by deviceCallbackName. It is up to the API client to ensure that this device callback exists and match the correct callback format for this instrumentation point.

Note
Thread-safety: an API user must serialize access to sanitizerAddPatchesFromFile, sanitizerAddPatches, sanitizerPatchInstructions, and sanitizerPatchModule. For example if sanitizerAddPatches(fileName) and sanitizerPatchInstruction(*, *, cbName) are called concurrently and cbName is intended to be found in the loaded module, the results are undefined.

Parameters:

instructionId – Instrumentation point for which to insert patches
module – CUDA module to instrument
deviceCallbackName – Name of the device function callback that the inserted patch will call at the instrumented points. This function is expected to be found in code previously loaded by sanitizerAddPatchesFromFile or sanitizerAddPatches.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_NOT_INITIALIZED – if unable to initialize the sanitizer.
SANITIZER_ERROR_INVALID_PARAMETER – if module is not a CUDA module or if deviceCallbackName function cannot be located.


SanitizerResult sanitizerPatchModule(CUmodule module)
Perform the actual instrumentation of a module.
Perform the instrumentation of a CUDA module based on previous calls to sanitizerPatchInstructions. This function also specifies the device memory buffer to be passed in as userdata to all callback functions.

Note
Thread-safety: an API user must serialize access to sanitizerAddPatchesFromFile, sanitizerAddPatches, sanitizerPatchInstructions, and sanitizerPatchModule. For example if sanitizerPatchModule(mod, *) and sanitizerPatchInstruction(*, mod, *) are called concurrently, the results are undefined.

Parameters:
module – CUDA module to instrument.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_INVALID_PARAMETER – if module is not a CUDA module.


SanitizerResult sanitizerSetCallbackData(

CUfunction kernel,
const void *userdata,

)
Specifies the user data pointer for callbacks.
Mark all subsequent launches of kernel to use userdata pointer as the device memory buffer to pass in to callback functions.

Parameters:

kernel – CUDA function to link to user data. Callbacks in subsequent launches on this kernel will use userdata as callback data.
userdata – Device memory buffer. This data will be passed to callback functions via the userdata parameter.

Return values:
SANITIZER_SUCCESS – on success.


SanitizerResult sanitizerSetDeviceGraphData(

CUgraphExec graphExec,
Sanitizer_StreamHandle stream,
const void *userdata,

)
Specifies the user data pointer accessible from callbacks in the device-launched graphs launched by the specified host-launched graphExec.
Mark all subsequent launch of graphExec to make available userdata in device callbacks from device-launched graphs. userdata will not be set in the callback userdata parameter but must be accessed through another mean instead. Please refer to the Sanitizer API reference manual. This function is only available if the driver version is 535 or newer.

Parameters:

graphExec – CUDA graphExec that will launch CUDA graphs from the device.
stream – CUDA stream associated with the stream launch.
userdata – Device memory buffer.

Return values:
SANITIZER_SUCCESS – on success.


SanitizerResult sanitizerSetLaunchCallbackData(

Sanitizer_LaunchHandle launch,
CUfunction kernel,
Sanitizer_StreamHandle stream,
const void *userdata,

)
Specifies the user data pointer for callbacks.
Mark launch to use userdata pointer as the device memory buffer to pass in to callback functions. This function is only available if the driver version is 455 or newer.

Parameters:

launch – Kernel launch to link to user data. Callbacks in this kernel launch will use userdata as callback data.
kernel – CUDA function associated with the kernel launch.
stream – CUDA stream associated with the stream launch.
userdata – Device memory buffer. This data will be passed to callback functions via the userdata parameter.

Return values:
SANITIZER_SUCCESS – on success.


SanitizerResult sanitizerUnpatchModule(CUmodule module)
Remove existing instrumentation of a module.
Remove any instrumentation of a CUDA module performed by previous calls to sanitizerPatchModule.

Note
Thread-safety: an API user must serialize access to sanitizerPatchModule and sanitizerUnpatchModule on the same module. For example, if sanitizerPatchModule(mod) and sanitizerUnpatchModule(mod) are called concurrently, the results are undefined.

Parameters:
module – CUDA module on which to remove instrumentation.

Return values:
SANITIZER_SUCCESS – on success.