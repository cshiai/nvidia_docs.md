# 6.1. CUPTI Activity API


Functions, types, and enums that implement the CUPTI Activity API.


## 6.1.1. Data Structures


CUpti_Activity
The base activity record.

CUpti_ActivityAPI
The activity record for a driver or runtime API invocation.

CUpti_ActivityAutoBoostState
Device auto boost state structure.

CUpti_ActivityBranch2
The activity record for source level result branch.

CUpti_ActivityCdpKernel
The activity record for CDP (CUDA Dynamic Parallelism) kernel.

CUpti_ActivityComputeEngineCtxSwitch
The activity record for trace of CUDA context switch events.

CUpti_ActivityConfidentialComputeRotation
Event related to confidential compute encryption rotation.

CUpti_ActivityContext4
The activity record for a context.

CUpti_ActivityCudaEvent2
The activity record for CUDA event.

CUpti_ActivityDevice5
The activity record for a device.

CUpti_ActivityDeviceAttribute
The activity record for a device attribute.

CUpti_ActivityDeviceGraphTrace
The activity record for trace of device graph execution.

CUpti_ActivityEnvironment
The activity record for CUPTI environmental data.

CUpti_ActivityEvent
The activity record for a CUPTI event.

CUpti_ActivityEventInstance
The activity record for a CUPTI event with instance information.

CUpti_ActivityExternalCorrelation
The activity record for correlation with external records.

CUpti_ActivityFunction
The activity record for global/device functions.

CUpti_ActivityGlobalAccess3
The activity record for source-level global access.

CUpti_ActivityGraphHostNodeCUpti_ActivityGraphTrace2
The activity record for trace of graph execution.

CUpti_ActivityHostLaunch
The activity record for host launch functions.

CUpti_ActivityInstantaneousEvent
The activity record for an instantaneous CUPTI event.

CUpti_ActivityInstantaneousEventInstance
The activity record for an instantaneous CUPTI event with event domain instance information.

CUpti_ActivityInstantaneousMetric
The activity record for an instantaneous CUPTI metric.

CUpti_ActivityInstantaneousMetricInstance
The instantaneous activity record for a CUPTI metric with instance information.

CUpti_ActivityInstructionCorrelation
The activity record for source-level sass/source line-by-line correlation.

CUpti_ActivityInstructionExecution
The activity record for source-level instruction execution.

CUpti_ActivityJit2
The activity record for JIT operations.

CUpti_ActivityKernel11
The activity record for kernel.

CUpti_ActivityMarker2
The activity record providing a marker which is an instantaneous point in time.

CUpti_ActivityMarkerData2
The activity record providing detailed information for a marker.

CUpti_ActivityMemDecompress
The activity record for trace of decompression operations.

CUpti_ActivityMemcpy6
The activity record for memory copies.

CUpti_ActivityMemcpyPtoP4
The activity record for peer-to-peer memory copies.

CUpti_ActivityMemory
The activity record for memory.

CUpti_ActivityMemory4
The activity record for memory.

CUpti_ActivityMemoryPool3
The activity record for memory pool.

CUpti_ActivityMemset4
The activity record for memset.

CUpti_ActivityMetric
The activity record for a CUPTI metric.

CUpti_ActivityMetricInstance
The activity record for a CUPTI metric with instance information.

CUpti_ActivityModule
The activity record for a CUDA module.

CUpti_ActivityName
The activity record providing a name.

CUpti_ActivityNvLink4
NVLink information.

CUpti_ActivityObjectKindId
Identifiers for object kinds as specified by CUpti_ActivityObjectKind.

CUpti_ActivityOpenAcc
The base activity record for OpenAcc records.

CUpti_ActivityOpenAccData
The activity record for OpenACC data.

CUpti_ActivityOpenAccLaunch
The activity record for OpenACC launch.

CUpti_ActivityOpenAccOther
The activity record for OpenACC other.

CUpti_ActivityOpenMp
The base activity record for OpenMp records.

CUpti_ActivityOverhead3
The activity record for CUPTI and driver overheads.

CUpti_ActivityOverheadCommandBufferFullData
The structure to provide additional data for CUPTI_ACTIVITY_OVERHEAD_COMMAND_BUFFER_FULL.

CUpti_ActivityPCSampling3
The activity record for PC sampling.

CUpti_ActivityPCSamplingConfig
PC sampling configuration structure.

CUpti_ActivityPCSamplingRecordInfo
The activity record for record status for PC sampling.

CUpti_ActivityPcie
PCI devices information required to construct topology.

CUpti_ActivityPreemption
The activity record for a preemption of a CDP kernel.

CUpti_ActivitySharedAccess
The activity record for source-level shared access.

CUpti_ActivitySourceLocator
The activity record for source locator.

CUpti_ActivityStream
The activity record for CUDA stream.

CUpti_ActivitySynchronization2
The activity record for synchronization management.

CUpti_ActivityUnifiedMemoryCounter3
The activity record for Unified Memory counters (CUDA 7.0 and beyond)

CUpti_ActivityUnifiedMemoryCounterConfig
Unified Memory counters configuration structure.

CUpti_NvtxExtPayloadAttr

## 6.1.2. Macros


CUPTI_AUTO_BOOST_INVALID_CLIENT_PID
An invalid/unknown process id.

CUPTI_CORRELATION_ID_UNKNOWN
An invalid/unknown correlation ID.

CUPTI_DECOMPRESSED_BYTES_UNKNOWN
An invalid/unknown value for decompressed bytes.

CUPTI_FUNCTION_INDEX_ID_INVALID
An invalid function index ID.

CUPTI_GRID_ID_UNKNOWN
An invalid/unknown grid ID.

CUPTI_MAX_GPUSCUPTI_MAX_NVLINK_PORTS
Maximum NVLink port numbers.

CUPTI_NVLINK_INVALID_PORT
Invalid/unknown NVLink port number.

CUPTI_SOURCE_LOCATOR_ID_UNKNOWN
The source-locator ID that indicates an unknown source location.

CUPTI_SYNCHRONIZATION_INVALID_VALUE
An invalid/unknown value.

CUPTI_TIMESTAMP_UNKNOWN
An invalid/unknown timestamp for a start, end, queued, submitted, or completed time.


## 6.1.3. Enumerations


CUpti_ActivityAttribute
Activity attributes.

CUpti_ActivityComputeApiKind
The kind of a compute API.

CUpti_ActivityEnvironmentKind
The kind of environment data.

CUpti_ActivityFlag
Flags associated with activity records.

CUpti_ActivityInstructionClass
SASS instruction classification.

CUpti_ActivityJitEntryType
The types of JIT entry.

CUpti_ActivityJitOperationType
The types of JIT compilation operations.

CUpti_ActivityKind
The kinds of activity records.

CUpti_ActivityLaunchType
The type of the CUDA kernel launch.

CUpti_ActivityMemcpyKind
The kind of a memory copy, indicating the source and destination targets of the copy.

CUpti_ActivityMemoryKind
The kinds of memory accessed by a memory operation/copy.

CUpti_ActivityMemoryOperationType
Memory operation types.

CUpti_ActivityMemoryPoolOperationType
Memory pool operation types.

CUpti_ActivityMemoryPoolType
Memory pool types.

CUpti_ActivityObjectKind
The kinds of activity objects.

CUpti_ActivityOverheadKind
The kinds of activity overhead.

CUpti_ActivityPCSamplingPeriod
Sampling period for PC sampling method.

CUpti_ActivityPCSamplingStallReason
The stall reason for PC sampling activity.

CUpti_ActivityPartitionedGlobalCacheConfig
Partitioned global caching option.

CUpti_ActivityPreemptionKind
The kind of a preemption activity.

CUpti_ActivityStreamFlag
stream type.

CUpti_ActivitySynchronizationType
Synchronization type.

CUpti_ActivityThreadIdType
Thread-Id types.

CUpti_ActivityUnifiedMemoryAccessType
Memory access type for unified memory page faults.

CUpti_ActivityUnifiedMemoryCounterKind
Kind of the Unified Memory counter.

CUpti_ActivityUnifiedMemoryCounterScope
Scope of the unified memory counter (deprecated in CUDA 7.0)

CUpti_ActivityUnifiedMemoryMigrationCause
Migration cause of the Unified Memory counter.

CUpti_ActivityUnifiedMemoryRemoteMapCause
Remote memory map cause of the Unified Memory counter.

CUpti_ChannelTypeCUpti_ComputeEngineCtxSwitchOperationType
The operation type of CUDA context switch event records.

CUpti_ConfidentialComputeRotationEventTypeCUpti_ContextCigMode
CIG (CUDA in Graphics) Modes.

CUpti_DevType
The device type for device connected to NVLink.

CUpti_DeviceGraphLaunchMode
The launch mode for device graph execution.

CUpti_DeviceVirtualizationMode
This indicates the virtualization mode in which CUDA device is running.

CUpti_EnvironmentClocksThrottleReason
Reasons for clock throttling.

CUpti_ExternalCorrelationKind
The kind of external APIs supported for correlation.

CUpti_FuncShmemLimitConfig
The shared memory limit per block config for a kernel This should be used to set 'cudaOccFuncShmemConfig' field in occupancy calculator API.

CUpti_LinkFlag
Link flags.

CUpti_NvtxExtPayloadTypeCUpti_OpenAccConstructKind
The OpenAcc parent construct kind for OpenAcc activity records.

CUpti_OpenAccEventKind
The OpenAcc event kind for OpenAcc activity records.

CUpti_OpenMpEventKindCUpti_PcieDeviceType
Field to differentiate whether PCIE Activity record is of a GPU or a PCI Bridge.

CUpti_PcieGen
PCIE Generation.


## 6.1.4. Functions


CUptiResult cuptiActivityConfigurePCSampling(CUcontext ctx, CUpti_ActivityPCSamplingConfig *config)
Set PC sampling configuration.

CUptiResult cuptiActivityConfigureUnifiedMemoryCounter(CUpti_ActivityUnifiedMemoryCounterConfig *config, uint32_t count)
Set Unified Memory Counter configuration.

CUptiResult cuptiActivityDisable(CUpti_ActivityKind kind)
Disable collection of a specific kind of activity record.

CUptiResult cuptiActivityDisableContext(CUcontext context, CUpti_ActivityKind kind)
Disable collection of a specific kind of activity record for a context.

CUptiResult cuptiActivityEnable(CUpti_ActivityKind kind)
Enable collection of a specific kind of activity record.

CUptiResult cuptiActivityEnableAllSyncRecords(uint8_t enable)
Enables collecting records for all synchronization operations.

CUptiResult cuptiActivityEnableAllocationSource(uint8_t enable)
Enables tracking the source library for memory allocation requests.

CUptiResult cuptiActivityEnableAndDump(CUpti_ActivityKind kind)
Enable collection of a specific kind of activity record.

CUptiResult cuptiActivityEnableContext(CUcontext context, CUpti_ActivityKind kind)
Enable collection of a specific kind of activity record for a context.

CUptiResult cuptiActivityEnableCudaEventDeviceTimestamps(uint8_t enable)
Enable/Disable collecting device timestamp for CUPTI_ACTIVITY_KIND_CUDA_EVENT record.

CUptiResult cuptiActivityEnableDeviceGraph(uint8_t enable)
Controls the collection of records for device launched graphs.

CUptiResult cuptiActivityEnableDriverApi(CUpti_CallbackId cbid, uint8_t enable)
Controls the collection of activity records for specific CUDA Driver APIs.

CUptiResult cuptiActivityEnableHWTrace(uint8_t enable)
Enables the collection of CUDA kernel timestamps through Hardware Event System(HES).

CUptiResult cuptiActivityEnableLatencyTimestamps(uint8_t enable)
Controls the collection of queued and submitted timestamps for kernels.

CUptiResult cuptiActivityEnableLaunchAttributes(uint8_t enable)
Controls the collection of launch attributes for kernels.

CUptiResult cuptiActivityEnableRuntimeApi(CUpti_CallbackId cbid, uint8_t enable)
Controls the collection of activity records for specific CUDA Runtime APIs.

CUptiResult cuptiActivityFlush(CUcontext context, uint32_t streamId, uint32_t flag)
Wait for all activity records to be delivered via the completion callback.

CUptiResult cuptiActivityFlushAll(uint32_t flag)
Request to deliver activity records via the buffer completion callback.

CUptiResult cuptiActivityFlushPeriod(uint32_t time)
Sets the flush period for the worker thread.

CUptiResult cuptiActivityGetAttribute(CUpti_ActivityAttribute attr, size_t *valueSize, void *value)
Read an activity API attribute.

CUptiResult cuptiActivityGetNextRecord(uint8_t *buffer, size_t validBufferSizeBytes, CUpti_Activity record)
Iterate over the activity records in a buffer.

CUptiResult cuptiActivityGetNumDroppedRecords(CUcontext context, uint32_t streamId, size_t *dropped)
Get the number of activity records that were dropped of insufficient buffer space.

CUptiResult cuptiActivityPopExternalCorrelationId(CUpti_ExternalCorrelationKind kind, uint64_t *lastId)
Pop an external correlation id for the calling thread.

CUptiResult cuptiActivityPushExternalCorrelationId(CUpti_ExternalCorrelationKind kind, uint64_t id)
Push an external correlation id for the calling thread.

CUptiResult cuptiActivityRegisterCallbacks(CUpti_BuffersCallbackRequestFunc funcBufferRequested, CUpti_BuffersCallbackCompleteFunc funcBufferCompleted)
Registers callback functions with CUPTI for activity buffer handling.

CUptiResult cuptiActivityRegisterTimestampCallback(CUpti_TimestampCallbackFunc funcTimestamp)
Registers callback function with CUPTI for providing timestamp.

CUptiResult cuptiActivitySetAttribute(CUpti_ActivityAttribute attr, size_t *valueSize, void *value)
Write an activity API attribute.

CUptiResult cuptiComputeCapabilitySupported(int major, int minor, int *support)
Check support for a compute capability.

CUptiResult cuptiDeviceSupported(CUdevice dev, int *support)
Check support for a compute device.

CUptiResult cuptiDeviceVirtualizationMode(CUdevice dev, CUpti_DeviceVirtualizationMode *mode)
Query the virtualization mode of the device.

CUptiResult cuptiFinalize(void)
Detach CUPTI from the running process.

CUptiResult cuptiGetAutoBoostState(CUcontext context, CUpti_ActivityAutoBoostState *state)
Get auto boost state.

CUptiResult cuptiGetContextId(CUcontext context, uint32_t *contextId)
Get the ID of a context.

CUptiResult cuptiGetDeviceId(CUcontext context, uint32_t *deviceId)
Get the ID of a device.

CUptiResult cuptiGetGraphExecId(CUgraphExec graphExec, uint32_t *pId)
Get the unique ID of executable graph.

CUptiResult cuptiGetGraphId(CUgraph graph, uint32_t *pId)
Get the unique ID of graph.

CUptiResult cuptiGetGraphNodeId(CUgraphNode node, uint64_t *nodeId)
Get the unique ID of a graph node.

CUptiResult cuptiGetLastError(void)
Returns the last error from a cupti call or callback.

CUptiResult cuptiGetStreamId(CUcontext context, CUstream stream, uint32_t *streamId)
Get the ID of a stream.

CUptiResult cuptiGetStreamIdEx(CUcontext context, CUstream stream, uint8_t perThreadStream, uint32_t *streamId)
Get the ID of a stream.

CUptiResult cuptiGetThreadIdType(CUpti_ActivityThreadIdType *type)
Get the thread-id type.

CUptiResult cuptiGetTimestamp(uint64_t *timestamp)
Get the CUPTI timestamp.

CUptiResult cuptiSetThreadIdType(CUpti_ActivityThreadIdType type)
Set the thread-id type.


## 6.1.5. Typedefs


CUpti_BuffersCallbackCompleteFunc
Function type for callback used by CUPTI to return a buffer of activity records.

CUpti_BuffersCallbackRequestFunc
Function type for callback used by CUPTI to request an empty buffer for storing activity records.

CUpti_TimestampCallbackFunc
Function type for callback used by CUPTI to request a timestamp to be used in activity records.


## 6.1.6. Macros


CUPTI_AUTO_BOOST_INVALID_CLIENT_PID
An invalid/unknown process id.


CUPTI_CORRELATION_ID_UNKNOWN
An invalid/unknown correlation ID.
A correlation ID of this value indicates that there is no correlation for the activity record.


CUPTI_DECOMPRESSED_BYTES_UNKNOWN
An invalid/unknown value for decompressed bytes.


CUPTI_FUNCTION_INDEX_ID_INVALID
An invalid function index ID.


CUPTI_GRID_ID_UNKNOWN
An invalid/unknown grid ID.


CUPTI_MAX_GPUSCUPTI_MAX_NVLINK_PORTS
Maximum NVLink port numbers.


CUPTI_NVLINK_INVALID_PORT
Invalid/unknown NVLink port number.


CUPTI_SOURCE_LOCATOR_ID_UNKNOWN
The source-locator ID that indicates an unknown source location.
There is not an actual CUpti_ActivitySourceLocator object corresponding to this value.


CUPTI_SYNCHRONIZATION_INVALID_VALUE
An invalid/unknown value.


CUPTI_TIMESTAMP_UNKNOWN
An invalid/unknown timestamp for a start, end, queued, submitted, or completed time.


## 6.1.7. Enumerations


enum CUpti_ActivityAttribute
Activity attributes.
These attributes are used to control the behavior of the activity API.
Values:

enumerator CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_SIZE
The device memory size (in bytes) reserved for storing profiling data for concurrent kernels (activity kind CUPTI_ACTIVITY_KIND_CONCURRENT_KERNEL), memcopies and memsets for each buffer on a context.
The value is a size_t.
There is a limit on how many device buffers can be allocated per context. User can query and set this limit using the attribute CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_POOL_LIMIT. CUPTI doesn’t pre-allocate all the buffers, it pre-allocates only those many buffers as set by the attribute CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_PRE_ALLOCATE_VALUE. When all of the data in a buffer is consumed, it is added in the reuse pool, and CUPTI picks a buffer from this pool when a new buffer is needed. Thus memory footprint does not scale with the kernel count. Applications with the high density of kernels, memcopies and memsets might result in having CUPTI to allocate more device buffers. CUPTI allocates another buffer only when it runs out of the buffers in the reuse pool.
Since buffer allocation happens in the main application thread, this might result in stalls in the critical path. CUPTI pre-allocates 3 buffers of the same size to mitigate this issue. User can query and set the pre-allocation limit using the attribute CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_PRE_ALLOCATE_VALUE.
Having larger buffer size leaves less device memory for the application. Having smaller buffer size increases the risk of dropping timestamps for records if too many kernels or memcopies or memsets are launched at one time.
This value only applies to new buffer allocations. Set this value before initializing CUDA or before creating a context to ensure it is considered for the following allocations.
The default value is 3200000 (~3MB) which can accommodate profiling data up to 100,000 kernels, memcopies and memsets combined.
Note: Starting with the CUDA 12.0 Update 1 release, CUPTI allocates the profiling buffer in the device memory by default, which may improve the performance of the tracing run. To change the preferred location to page-locked host memory, refer to the attribute CUPTI_ACTIVITY_ATTR_MEM_ALLOCATION_TYPE_HOST_PINNED. The size of the memory and maximum number of pools are still controlled by the attributes CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_SIZE and CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_POOL_LIMIT.
Note: The actual amount of device memory per buffer reserved by CUPTI might be larger.

enumerator CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_SIZE_CDP
The device memory size (in bytes) reserved for storing profiling data for CDP operations for each buffer on a context.
The value is a size_t.
Having larger buffer size means less flush operations but consumes more device memory. This value only applies to new allocations.
Set this value before initializing CUDA or before creating a context to ensure it is considered for the following allocations.
The default value is 8388608 (8MB).
Note: The actual amount of device memory per context reserved by CUPTI might be larger.

enumerator CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_POOL_LIMIT
The maximum number of device memory buffers per context.
The value is a size_t.
For an application with high rate of kernel launches, memcopies and memsets having a bigger pool limit helps in timestamp collection for all these activities at the expense of a larger memory footprint. Refer to the description of the attribute CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_SIZE for more details.
Setting this value will not modify the number of memory buffers currently stored.
Set this value before initializing CUDA to ensure the limit is not exceeded.
The default value is 250.

enumerator CUPTI_ACTIVITY_ATTR_PROFILING_SEMAPHORE_POOL_SIZE
This attribute is not supported starting with CUDA 12.3 CUPTI no longer uses profiling semaphore pool to store profiling data.
There is a limit on how many semaphore pools can be allocated per context. User can query and set this limit using the attribute CUPTI_ACTIVITY_ATTR_PROFILING_SEMAPHORE_POOL_LIMIT. CUPTI doesn’t pre-allocate all the semaphore pools, it pre-allocates only those many semaphore pools as set by the attribute CUPTI_ACTIVITY_ATTR_PROFILING_SEMAPHORE_PRE_ALLOCATE_VALUE. When all of the data in a semaphore pool is consumed, it is added in the reuse pool, and CUPTI picks a semaphore pool from the reuse pool when a new semaphore pool is needed. Thus memory footprint does not scale with the kernel count. Applications with the high density of kernels might result in having CUPTI to allocate more semaphore pools. CUPTI allocates another semaphore pool only when it runs out of the semaphore pools in the reuse pool.
Since semaphore pool allocation happens in the main application thread, this might result in stalls in the critical path. CUPTI pre-allocates 3 semaphore pools of the same size to mitigate this issue. User can query and set the pre-allocation limit using the attribute CUPTI_ACTIVITY_ATTR_PROFILING_SEMAPHORE_PRE_ALLOCATE_VALUE.
Having larger semaphore pool size leaves less device memory for the application. Having smaller semaphore pool size increases the risk of dropping timestamps for kernel records if too many kernels are issued/launched at one time.
This value only applies to new semaphore pool allocations. Set this value before initializing CUDA or before creating a context to ensure it is considered for the following allocations.
The default value is 25000 which can accommodate profiling data for upto 25,000 kernels.

enumerator CUPTI_ACTIVITY_ATTR_PROFILING_SEMAPHORE_POOL_LIMIT
This attribute is not supported starting with CUDA 12.3 CUPTI no longer uses profiling semaphore pool to store profiling data.
The maximum number of profiling semaphore pools per context. The value is a size_t.
Refer to the description of the attribute CUPTI_ACTIVITY_ATTR_PROFILING_SEMAPHORE_POOL_SIZE for more details.
Set this value before initializing CUDA to ensure the limit is not exceeded.
The default value is 250.

enumerator CUPTI_ACTIVITY_ATTR_ZEROED_OUT_ACTIVITY_BUFFER
The flag to indicate whether user should provide activity buffer of zero value.
The value is a uint8_t.
If the value of this attribute is non-zero, user should provide a zero value buffer in the CUpti_BuffersCallbackRequestFunc. If the user does not provide a zero value buffer after setting this to non-zero, the activity buffer may contain some uninitialized values when CUPTI returns it in CUpti_BuffersCallbackCompleteFunc
If the value of this attribute is zero, CUPTI will initialize the user buffer received in the CUpti_BuffersCallbackRequestFunc to zero before filling it. If the user sets this to zero, a few stalls may appear in critical path because CUPTI will zero out the buffer in the main thread. Set this value before returning from CUpti_BuffersCallbackRequestFunc to ensure it is considered for all the subsequent user buffers.
The default value is 0.

enumerator CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_PRE_ALLOCATE_VALUE
Number of device buffers to pre-allocate for a context during the initialization phase.
The value is a size_t.
Refer to the description of the attribute CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_SIZE for details.
This value must be less than the maximum number of device buffers set using the attribute CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_POOL_LIMIT
Set this value before initializing CUDA or before creating a context to ensure it is considered by the CUPTI.
The default value is set to 3 to ping pong between these buffers (if possible).

enumerator CUPTI_ACTIVITY_ATTR_PROFILING_SEMAPHORE_PRE_ALLOCATE_VALUE
This attribute is not supported starting with CUDA 12.3 CUPTI no longer uses profiling semaphore pool to store profiling data.
Number of profiling semaphore pools to pre-allocate for a context during the initialization phase. The value is a size_t.
Refer to the description of the attribute CUPTI_ACTIVITY_ATTR_PROFILING_SEMAPHORE_POOL_SIZE for details.
This value must be less than the maximum number of profiling semaphore pools set using the attribute CUPTI_ACTIVITY_ATTR_PROFILING_SEMAPHORE_POOL_LIMIT
Set this value before initializing CUDA or before creating a context to ensure it is considered by the CUPTI.
The default value is set to 3 to ping pong between these pools (if possible).

enumerator CUPTI_ACTIVITY_ATTR_MEM_ALLOCATION_TYPE_HOST_PINNED
Allocate page-locked (pinned) host memory for storing profiling data for concurrent kernels, memcopies and memsets for each buffer on a context.
The value is a uint8_t.
From CUDA 11.2 through CUDA 12.0 GA releases, CUPTI allocated the profiling buffer in pinned host memory by default. Allocating excessive amounts of pinned memory may degrade system performance, as it reduces the amount of memory available to the system for paging. For this reason user might want to change the location from pinned host memory to device memory by setting value of this attribute to 0.
Using page-locked (pinned) host memory buffers is not supported on confidential computing devices. If this attribute is set to 1, CUPTI will return error CUPTI_ERROR_NOT_SUPPORTED.
The default value is 0.

enumerator CUPTI_ACTIVITY_ATTR_PER_THREAD_ACTIVITY_BUFFER
Request activity buffers per-thread to store CUPTI activity records in the activity buffer on per-thread basis.
The value is a uint8_t.
The attribute should be set before registering the buffer callbacks using cuptiActivityRegisterCallbacks API and before any of the CUPTI activity kinds are enabled. This makes sure that all the records are stored in activity buffers allocated per-thread. Changing this attribute in the middle of the profiling session will result in undefined behavior.
The default value is 1.

enumerator CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_SIZE_DEVICE_GRAPHS
The device memory size (in bytes) reserved for storing profiling data for device graph operations for each buffer on a context.
The value is a size_t.
Having larger buffer size means less flush operations but consumes more device memory. This value only applies to new allocations.
Set this value before initializing CUDA or before creating a context to ensure it is considered for the following allocations.
The default value is 16777216 (16MB).
Note: The actual amount of device memory per context reserved by CUPTI might be larger.

enumerator CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_FORCE_INT


enum CUpti_ActivityComputeApiKind
The kind of a compute API.
Values:

enumerator CUPTI_ACTIVITY_COMPUTE_API_UNKNOWN
The compute API is not known.

enumerator CUPTI_ACTIVITY_COMPUTE_API_CUDA
The compute APIs are for CUDA.

enumerator CUPTI_ACTIVITY_COMPUTE_API_CUDA_MPS
The compute APIs are for CUDA running in MPS (Multi-Process Service) environment.

enumerator CUPTI_ACTIVITY_COMPUTE_API_FORCE_INT


enum CUpti_ActivityEnvironmentKind
The kind of environment data.
Used to indicate what type of data is being reported by an environment activity record.
Values:

enumerator CUPTI_ACTIVITY_ENVIRONMENT_UNKNOWN
Unknown data.

enumerator CUPTI_ACTIVITY_ENVIRONMENT_SPEED
The environment data is related to speed.

enumerator CUPTI_ACTIVITY_ENVIRONMENT_TEMPERATURE
The environment data is related to temperature.

enumerator CUPTI_ACTIVITY_ENVIRONMENT_POWER
The environment data is related to power.

enumerator CUPTI_ACTIVITY_ENVIRONMENT_COOLING
The environment data is related to cooling.

enumerator CUPTI_ACTIVITY_ENVIRONMENT_COUNT

enumerator CUPTI_ACTIVITY_ENVIRONMENT_KIND_FORCE_INT


enum CUpti_ActivityFlag
Flags associated with activity records.
Activity record flags. Flags can be combined by bitwise OR to associated multiple flags with an activity record. Each flag is specific to a certain activity kind, as noted below.
Values:

enumerator CUPTI_ACTIVITY_FLAG_NONE
Indicates the activity record has no flags.

enumerator CUPTI_ACTIVITY_FLAG_DEVICE_CONCURRENT_KERNELS
Indicates the activity represents a device that supports concurrent kernel execution.
Valid for CUPTI_ACTIVITY_KIND_DEVICE.

enumerator CUPTI_ACTIVITY_FLAG_DEVICE_ATTRIBUTE_CUDEVICE
Indicates if the activity represents a CUdevice_attribute value or a CUpti_DeviceAttribute value.
Valid for CUPTI_ACTIVITY_KIND_DEVICE_ATTRIBUTE.

enumerator CUPTI_ACTIVITY_FLAG_MEMCPY_ASYNC
Indicates the activity represents an asynchronous memcpy operation.
Valid for CUPTI_ACTIVITY_KIND_MEMCPY.

enumerator CUPTI_ACTIVITY_FLAG_MARKER_INSTANTANEOUS
Indicates the activity represents an instantaneous marker.
Valid for CUPTI_ACTIVITY_KIND_MARKER.

enumerator CUPTI_ACTIVITY_FLAG_MARKER_START
Indicates the activity represents a region start marker.
Valid for CUPTI_ACTIVITY_KIND_MARKER.

enumerator CUPTI_ACTIVITY_FLAG_MARKER_END
Indicates the activity represents a region end marker.
Valid for CUPTI_ACTIVITY_KIND_MARKER.

enumerator CUPTI_ACTIVITY_FLAG_MARKER_SYNC_ACQUIRE
Indicates the activity represents an attempt to acquire a user defined synchronization object.
Valid for CUPTI_ACTIVITY_KIND_MARKER.

enumerator CUPTI_ACTIVITY_FLAG_MARKER_SYNC_ACQUIRE_SUCCESS
Indicates the activity represents success in acquiring the user defined synchronization object.
Valid for CUPTI_ACTIVITY_KIND_MARKER.

enumerator CUPTI_ACTIVITY_FLAG_MARKER_SYNC_ACQUIRE_FAILED
Indicates the activity represents failure in acquiring the user defined synchronization object.
Valid for CUPTI_ACTIVITY_KIND_MARKER.

enumerator CUPTI_ACTIVITY_FLAG_MARKER_SYNC_RELEASE
Indicates the activity represents releasing a reservation on user defined synchronization object.
Valid for CUPTI_ACTIVITY_KIND_MARKER.

enumerator CUPTI_ACTIVITY_FLAG_MARKER_COLOR_NONE
Indicates the activity represents a marker that does not specify a color.
Valid for CUPTI_ACTIVITY_KIND_MARKER_DATA.

enumerator CUPTI_ACTIVITY_FLAG_MARKER_COLOR_ARGB
Indicates the activity represents a marker that specifies a color in alpha-red-green-blue format.
Valid for CUPTI_ACTIVITY_KIND_MARKER_DATA.

enumerator CUPTI_ACTIVITY_FLAG_GLOBAL_ACCESS_KIND_SIZE_MASK
The number of bytes requested by each thread Valid for CUpti_ActivityGlobalAccess3.

enumerator CUPTI_ACTIVITY_FLAG_GLOBAL_ACCESS_KIND_LOAD
If bit in this flag is set, the access was load, else it is a store access.
Valid for CUpti_ActivityGlobalAccess3.

enumerator CUPTI_ACTIVITY_FLAG_GLOBAL_ACCESS_KIND_CACHED
If this bit in flag is set, the load access was cached else it is uncached.
Valid for CUpti_ActivityGlobalAccess3.

enumerator CUPTI_ACTIVITY_FLAG_METRIC_OVERFLOWED
If this bit in flag is set, the metric value overflowed.
Valid for CUpti_ActivityMetric and CUpti_ActivityMetricInstance.

enumerator CUPTI_ACTIVITY_FLAG_METRIC_VALUE_INVALID
If this bit in flag is set, the metric value couldn’t be calculated.
This occurs when a value(s) required to calculate the metric is missing. Valid for CUpti_ActivityMetric and CUpti_ActivityMetricInstance.

enumerator CUPTI_ACTIVITY_FLAG_INSTRUCTION_VALUE_INVALID
If this bit in flag is set, the source level metric value couldn’t be calculated.
This occurs when a value(s) required to calculate the source level metric cannot be evaluated. Valid for CUpti_ActivityInstructionExecution.

enumerator CUPTI_ACTIVITY_FLAG_INSTRUCTION_CLASS_MASK
The mask for the instruction class, CUpti_ActivityInstructionClass Valid for CUpti_ActivityInstructionExecution and CUpti_ActivityInstructionCorrelation.

enumerator CUPTI_ACTIVITY_FLAG_FLUSH_FORCED
When calling cuptiActivityFlushAll, this flag can be set to force CUPTI to flush all records in the buffer, whether finished or not.

enumerator CUPTI_ACTIVITY_FLAG_SHARED_ACCESS_KIND_SIZE_MASK
The number of bytes requested by each thread Valid for CUpti_ActivitySharedAccess.

enumerator CUPTI_ACTIVITY_FLAG_SHARED_ACCESS_KIND_LOAD
If bit in this flag is set, the access was load, else it is a store access.
Valid for CUpti_ActivitySharedAccess.

enumerator CUPTI_ACTIVITY_FLAG_MEMSET_ASYNC
Indicates the activity represents an asynchronous memset operation.
Valid for CUPTI_ACTIVITY_KIND_MEMSET.

enumerator CUPTI_ACTIVITY_FLAG_THRASHING_IN_CPU
Indicates the activity represents thrashing in CPU.
Valid for counter of kind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THRASHING in CUPTI_ACTIVITY_KIND_UNIFIED_MEMORY_COUNTER

enumerator CUPTI_ACTIVITY_FLAG_THROTTLING_IN_CPU
Indicates the activity represents page throttling in CPU.
Valid for counter of kind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THROTTLING in CUPTI_ACTIVITY_KIND_UNIFIED_MEMORY_COUNTER

enumerator CUPTI_ACTIVITY_FLAG_FORCE_INT


enum CUpti_ActivityInstructionClass
SASS instruction classification.
The sass instruction are broadly divided into different class. Each enum represents a classification.
Values:

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_UNKNOWN
The instruction class is not known.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_FP_32
Represents a 32 bit floating point operation.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_FP_64
Represents a 64 bit floating point operation.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_INTEGER
Represents an integer operation.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_BIT_CONVERSION
Represents a bit conversion operation.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_CONTROL_FLOW
Represents a control flow instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_GLOBAL
Represents a global load-store instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_SHARED
Represents a shared load-store instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_LOCAL
Represents a local load-store instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_GENERIC
Represents a generic load-store instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_SURFACE
Represents a surface load-store instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_CONSTANT
Represents a constant load instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_TEXTURE
Represents a texture load-store instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_GLOBAL_ATOMIC
Represents a global atomic instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_SHARED_ATOMIC
Represents a shared atomic instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_SURFACE_ATOMIC
Represents a surface atomic instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_INTER_THREAD_COMMUNICATION
Represents a inter-thread communication instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_BARRIER
Represents a barrier instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_MISCELLANEOUS
Represents some miscellaneous instructions which do not fit in the above classification.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_FP_16
Represents a 16 bit floating point operation.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_UNIFORM
Represents uniform instruction.

enumerator CUPTI_ACTIVITY_INSTRUCTION_CLASS_KIND_FORCE_INT


enum CUpti_ActivityJitEntryType
The types of JIT entry.
To be used in CUpti_ActivityJit.
Values:

enumerator CUPTI_ACTIVITY_JIT_ENTRY_INVALID

enumerator CUPTI_ACTIVITY_JIT_ENTRY_PTX_TO_CUBIN
PTX to CUBIN.

enumerator CUPTI_ACTIVITY_JIT_ENTRY_NVVM_IR_TO_PTX
NVVM-IR to PTX.

enumerator CUPTI_ACTIVITY_JIT_ENTRY_TYPE_FORCE_INT


enum CUpti_ActivityJitOperationType
The types of JIT compilation operations.
To be used in CUpti_ActivityJit.
Values:

enumerator CUPTI_ACTIVITY_JIT_OPERATION_INVALID

enumerator CUPTI_ACTIVITY_JIT_OPERATION_CACHE_LOAD
Loaded from the compute cache.

enumerator CUPTI_ACTIVITY_JIT_OPERATION_CACHE_STORE
Stored in the compute cache.

enumerator CUPTI_ACTIVITY_JIT_OPERATION_COMPILE
JIT compilation.

enumerator CUPTI_ACTIVITY_JIT_OPERATION_TYPE_FORCE_INT


enum CUpti_ActivityKind
The kinds of activity records.
Each activity record kind represents information about a GPU or an activity occurring on a CPU or GPU. Each kind is associated with a activity record structure that holds the information associated with the kind.
See also
CUpti_Activity

See also
CUpti_ActivityAPI

See also
CUpti_ActivityContext

See also
CUpti_ActivityContext2

See also
CUpti_ActivityContext3

See also
CUpti_ActivityContext4

See also
CUpti_ActivityDevice

See also
CUpti_ActivityDevice2

See also
CUpti_ActivityDevice3

See also
CUpti_ActivityDevice4

See also
CUpti_ActivityDevice5

See also
CUpti_ActivityDeviceAttribute

See also
CUpti_ActivityEvent

See also
CUpti_ActivityEventInstance

See also
CUpti_ActivityKernel

See also
CUpti_ActivityKernel2

See also
CUpti_ActivityKernel3

See also
CUpti_ActivityKernel4

See also
CUpti_ActivityKernel5

See also
CUpti_ActivityKernel6

See also
CUpti_ActivityKernel7

See also
CUpti_ActivityKernel8

See also
CUpti_ActivityKernel9

See also
CUpti_ActivityKernel10

See also
CUpti_ActivityKernel11

See also
CUpti_ActivityCdpKernel

See also
CUpti_ActivityPreemption

See also
CUpti_ActivityMemcpy

See also
CUpti_ActivityMemcpy3

See also
CUpti_ActivityMemcpy4

See also
CUpti_ActivityMemcpy5

See also
CUpti_ActivityMemcpy6

See also
CUpti_ActivityMemcpyPtoP

See also
CUpti_ActivityMemcpyPtoP2

See also
CUpti_ActivityMemcpyPtoP3

See also
CUpti_ActivityMemcpyPtoP4

See also
CUpti_ActivityMemset

See also
CUpti_ActivityMemset2

See also
CUpti_ActivityMemset3

See also
CUpti_ActivityMemset4

See also
CUpti_ActivityMemory

See also
CUpti_ActivityMemory2

See also
CUpti_ActivityMemory3

See also
CUpti_ActivityMemory4

See also
CUpti_ActivityMemoryPool

See also
CUpti_ActivityMemoryPool2

See also
CUpti_ActivityMemoryPool3

See also
CUpti_ActivityMetric

See also
CUpti_ActivityMetricInstance

See also
CUpti_ActivityName

See also
CUpti_ActivityMarker

See also
CUpti_ActivityMarker2

See also
CUpti_ActivityMarkerData

See also
CUpti_ActivitySourceLocator

See also
CUpti_ActivityGlobalAccess

See also
CUpti_ActivityGlobalAccess2

See also
CUpti_ActivityGlobalAccess3

See also
CUpti_ActivityBranch

See also
CUpti_ActivityBranch2

See also
CUpti_ActivityOverhead3

See also
CUpti_ActivityEnvironment

See also
CUpti_ActivityInstructionExecution

See also
CUpti_ActivityUnifiedMemoryCounter

See also
CUpti_ActivityFunction

See also
CUpti_ActivityModule

See also
CUpti_ActivitySharedAccess

See also
CUpti_ActivityPCSampling

See also
CUpti_ActivityPCSampling2

See also
CUpti_ActivityPCSampling3

See also
CUpti_ActivityPCSamplingRecordInfo

See also
CUpti_ActivityCudaEvent2

See also
CUpti_ActivityStream

See also
CUpti_ActivitySynchronization2

See also
CUpti_ActivityInstructionCorrelation

See also
CUpti_ActivityExternalCorrelation

See also
CUpti_ActivityUnifiedMemoryCounter3

See also
CUpti_ActivityOpenAccData

See also
CUpti_ActivityOpenAccLaunch

See also
CUpti_ActivityOpenAccOther

See also
CUpti_ActivityOpenMp

See also
CUpti_ActivityNvLink

See also
CUpti_ActivityNvLink2

See also
CUpti_ActivityNvLink3

See also
CUpti_ActivityNvLink4

See also
CUpti_ActivityPcie

See also
CUpti_ActivityConfidentialComputeRotation

See also
CUpti_ActivityComputeEngineCtxSwitch

Values:

enumerator CUPTI_ACTIVITY_KIND_INVALID
The activity record is invalid.

enumerator CUPTI_ACTIVITY_KIND_MEMCPY
A host<->host, host<->device, or device<->device memory copy.
For peer to peer memory copy, use the kind CUPTI_ACTIVITY_KIND_MEMCPY2. The corresponding activity record structure is CUpti_ActivityMemcpy6.

enumerator CUPTI_ACTIVITY_KIND_MEMSET
A memory set executing on the GPU.
The corresponding activity record structure is CUpti_ActivityMemset4.

enumerator CUPTI_ACTIVITY_KIND_KERNEL
A kernel executing on the GPU.
This activity kind may significantly change the overall performance characteristics of the application because all kernel executions are serialized on the GPU. Other activity kind for kernel CUPTI_ACTIVITY_KIND_CONCURRENT_KERNEL doesn’t break kernel concurrency. The corresponding activity record structure is CUpti_ActivityKernel11.

enumerator CUPTI_ACTIVITY_KIND_DRIVER
A CUDA driver API function execution.
The corresponding activity record structure is CUpti_ActivityAPI.

enumerator CUPTI_ACTIVITY_KIND_RUNTIME
A CUDA runtime API function execution.
The corresponding activity record structure is CUpti_ActivityAPI.

enumerator CUPTI_ACTIVITY_KIND_EVENT
A performance counter (aka event) value.
The corresponding activity record structure is CUpti_ActivityEvent. This activity cannot be directly enabled or disabled. Information collected using the Event API. can be stored in the corresponding activity record. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used.

enumerator CUPTI_ACTIVITY_KIND_METRIC
A performance metric value.
The corresponding activity record structure is CUpti_ActivityMetric. This activity cannot be directly enabled or disabled. Information collected using the Metric API. can be stored in the corresponding activity record. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used.

enumerator CUPTI_ACTIVITY_KIND_DEVICE
Information about a CUDA device.
The corresponding activity record structure is CUpti_ActivityDevice5.

enumerator CUPTI_ACTIVITY_KIND_CONTEXT
Information about a CUDA context.
The corresponding activity record structure is CUpti_ActivityContext4.

enumerator CUPTI_ACTIVITY_KIND_CONCURRENT_KERNEL
A kernel executing on the GPU.
This activity kind doesn’t break kernel concurrency. The corresponding activity record structure is CUpti_ActivityKernel11.

enumerator CUPTI_ACTIVITY_KIND_NAME
Resource naming done via NVTX APIs for thread, device, context, etc.
The corresponding activity record structure is CUpti_ActivityName.

enumerator CUPTI_ACTIVITY_KIND_MARKER
Instantaneous, start, or end NVTX marker.
The corresponding activity record structure is CUpti_ActivityMarker2.

enumerator CUPTI_ACTIVITY_KIND_MARKER_DATA
Extended, optional, data about a NVTX marker.
User must enable CUPTI_ACTIVITY_KIND_MARKER as well to get records for marker data. The corresponding activity record structure is CUpti_ActivityMarkerData2.

enumerator CUPTI_ACTIVITY_KIND_SOURCE_LOCATOR
Source information about source level result.
The corresponding activity record structure is CUpti_ActivitySourceLocator. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used. Enabling it will return the error code CUPTI_ERROR_LEGACY_PROFILER_NOT_SUPPORTED. Instead, use the SASS Metric APIs from the cupti_sass_metrics.h header.

enumerator CUPTI_ACTIVITY_KIND_GLOBAL_ACCESS
Results for source-level global access.
The corresponding activity record structure is CUpti_ActivityGlobalAccess3. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used. Enabling it will return the error code CUPTI_ERROR_LEGACY_PROFILER_NOT_SUPPORTED. Instead, use the SASS Metric APIs from the cupti_sass_metrics.h header.

enumerator CUPTI_ACTIVITY_KIND_BRANCH
Results for source-level branch.
The corresponding activity record structure is CUpti_ActivityBranch2. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used. Enabling it will return the error code CUPTI_ERROR_LEGACY_PROFILER_NOT_SUPPORTED. Instead, use the SASS Metric APIs from the cupti_sass_metrics.h header.

enumerator CUPTI_ACTIVITY_KIND_OVERHEAD
Overhead added by CUPTI, Compiler, CUDA driver etc.
The corresponding activity record structure is CUpti_ActivityOverhead3.

enumerator CUPTI_ACTIVITY_KIND_CDP_KERNEL
A CDP (CUDA Dynamic Parallel) kernel executing on the GPU.
The corresponding activity record structure is CUpti_ActivityCdpKernel. This activity cannot be directly enabled or disabled. It is enabled and disabled through concurrent kernel activity i.e. _CONCURRENT_KERNEL.

enumerator CUPTI_ACTIVITY_KIND_PREEMPTION
Preemption activity record indicating a preemption of a CDP (CUDA Dynamic Parallel) kernel executing on the GPU.
The corresponding activity record structure is CUpti_ActivityPreemption.

enumerator CUPTI_ACTIVITY_KIND_ENVIRONMENT
Environment activity records indicating power, clock, thermal, etc.
levels of the GPU. The corresponding activity record structure is CUpti_ActivityEnvironment.

enumerator CUPTI_ACTIVITY_KIND_EVENT_INSTANCE
An performance counter value associated with a specific event domain instance.
The corresponding activity record structure is CUpti_ActivityEventInstance. This activity cannot be directly enabled or disabled. Information collected using the Event API. can be stored in the corresponding activity record. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used.

enumerator CUPTI_ACTIVITY_KIND_MEMCPY2
A peer to peer memory copy.
The corresponding activity record structure is CUpti_ActivityMemcpyPtoP4.

enumerator CUPTI_ACTIVITY_KIND_METRIC_INSTANCE
A performance metric value associated with a specific metric domain instance.
The corresponding activity record structure is CUpti_ActivityMetricInstance. This activity cannot be directly enabled or disabled. Information collected using the Metric API. can be stored in the corresponding activity record. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used.

enumerator CUPTI_ACTIVITY_KIND_INSTRUCTION_EXECUTION
Results for source-level instruction execution.
The corresponding activity record structure is CUpti_ActivityInstructionExecution. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used. Enabling it will return the error code CUPTI_ERROR_LEGACY_PROFILER_NOT_SUPPORTED. Instead, use the SASS Metric APIs from the cupti_sass_metrics.h header.

enumerator CUPTI_ACTIVITY_KIND_UNIFIED_MEMORY_COUNTER
Unified Memory counter record.
The corresponding activity record structure is CUpti_ActivityUnifiedMemoryCounter3.

enumerator CUPTI_ACTIVITY_KIND_FUNCTION
Device global/function record.
The corresponding activity record structure is CUpti_ActivityFunction.

enumerator CUPTI_ACTIVITY_KIND_MODULE
CUDA Module record.
The corresponding activity record structure is CUpti_ActivityModule. This activity cannot be directly enabled or disabled. Information collected using the module callback can be be stored in the corresponding activity record.

enumerator CUPTI_ACTIVITY_KIND_DEVICE_ATTRIBUTE
A device attribute value.
The corresponding activity record structure is CUpti_ActivityDeviceAttribute. This activity cannot be directly enabled or disabled. Information collected using attributes CUpti_DeviceAttribute or CUdevice_attribute can be stored in the corresponding activity record.

enumerator CUPTI_ACTIVITY_KIND_SHARED_ACCESS
Results for source-level shared access.
The corresponding activity record structure is CUpti_ActivitySharedAccess. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used. Enabling it will return the error code CUPTI_ERROR_LEGACY_PROFILER_NOT_SUPPORTED. Instead, use the SASS Metric APIs from the cupti_sass_metrics.h header.

enumerator CUPTI_ACTIVITY_KIND_PC_SAMPLING
PC sampling information for kernels.
This will serialize kernels. The corresponding activity record structure is CUpti_ActivityPCSampling3. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used. Enabling it will return the error code CUPTI_ERROR_LEGACY_PROFILER_NOT_SUPPORTED. Instead, use the PC Sampling API from the cupti_pcsampling.h header, which allows concurrent kernel execution.

enumerator CUPTI_ACTIVITY_KIND_PC_SAMPLING_RECORD_INFO
Summary information about PC sampling records.
The corresponding activity record structure is CUpti_ActivityPCSamplingRecordInfo. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used. Enabling it will return the error code CUPTI_ERROR_LEGACY_PROFILER_NOT_SUPPORTED. Instead, use the PC Sampling API from the cupti_pcsampling.h header.

enumerator CUPTI_ACTIVITY_KIND_INSTRUCTION_CORRELATION
SASS/Source line-by-line correlation record.
This will generate sass/source correlation for functions that have source level analysis or pc sampling results. The records will be generated only when either of source level analysis or pc sampling activity is enabled. The corresponding activity record structure is CUpti_ActivityInstructionCorrelation. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used. Enabling it will return the error code CUPTI_ERROR_LEGACY_PROFILER_NOT_SUPPORTED. Instead, use the SASS Metric APIs from the cupti_sass_metrics.h header.

enumerator CUPTI_ACTIVITY_KIND_OPENACC_DATA
OpenACC data events.
The corresponding activity record structure is CUpti_ActivityOpenAccData.

enumerator CUPTI_ACTIVITY_KIND_OPENACC_LAUNCH
OpenACC launch events.
The corresponding activity record structure is CUpti_ActivityOpenAccLaunch.

enumerator CUPTI_ACTIVITY_KIND_OPENACC_OTHER
OpenACC other events.
The corresponding activity record structure is CUpti_ActivityOpenAccOther.

enumerator CUPTI_ACTIVITY_KIND_CUDA_EVENT
Information about a CUDA event (cudaEvent).
The corresponding activity record structure is CUpti_ActivityCudaEvent2.

enumerator CUPTI_ACTIVITY_KIND_STREAM
Information about a CUDA stream.
The corresponding activity record structure is CUpti_ActivityStream.

enumerator CUPTI_ACTIVITY_KIND_SYNCHRONIZATION
Records for CUDA synchronization primitives.
The corresponding activity record structure is CUpti_ActivitySynchronization2.

enumerator CUPTI_ACTIVITY_KIND_EXTERNAL_CORRELATION
Records for correlation of different programming APIs.
The corresponding activity record structure is CUpti_ActivityExternalCorrelation.

enumerator CUPTI_ACTIVITY_KIND_NVLINK
NVLink topology information.
The corresponding activity record structure is CUpti_ActivityNvLink4.

enumerator CUPTI_ACTIVITY_KIND_INSTANTANEOUS_EVENT
Instantaneous Event information.
The corresponding activity record structure is CUpti_ActivityInstantaneousEvent. This activity can not be directly enabled or disabled. Information collected using the Event API can be stored in the corresponding activity record. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used.

enumerator CUPTI_ACTIVITY_KIND_INSTANTANEOUS_EVENT_INSTANCE
Instantaneous Event information for a specific event domain instance.
The corresponding activity record structure is CUpti_ActivityInstantaneousEventInstance. This activity can not be directly enabled or disabled. Information collected using the Event API can be stored in the corresponding activity record. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used.

enumerator CUPTI_ACTIVITY_KIND_INSTANTANEOUS_METRIC
Instantaneous Metric information The corresponding activity record structure is CUpti_ActivityInstantaneousMetric.
This activity cannot be directly enabled or disabled. Information collected using the Metric API can be stored in the corresponding activity record. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used.

enumerator CUPTI_ACTIVITY_KIND_INSTANTANEOUS_METRIC_INSTANCE
Instantaneous Metric information for a specific metric domain instance.
The corresponding activity record structure is CUpti_ActivityInstantaneousMetricInstance. This activity cannot be directly enabled or disabled. Information collected using the Metric API can be stored in the corresponding activity record. Starting with the CUDA 13.0 release, this enum is unsupported and should no longer be used.

enumerator CUPTI_ACTIVITY_KIND_MEMORY
Memory activity tracking allocation and freeing of the memory The corresponding activity record structure is CUpti_ActivityMemory.

enumerator CUPTI_ACTIVITY_KIND_PCIE
PCI devices information used for PCI topology.
The corresponding activity record structure is CUpti_ActivityPcie.

enumerator CUPTI_ACTIVITY_KIND_OPENMP
OpenMP parallel events.
The corresponding activity record structure is CUpti_ActivityOpenMp.

enumerator CUPTI_ACTIVITY_KIND_INTERNAL_LAUNCH_API
A CUDA driver kernel launch occurring outside of any public API function execution.
Tools can handle these like records for driver API launch functions, although the cbid field is not used here. The corresponding activity record structure is CUpti_ActivityAPI.

enumerator CUPTI_ACTIVITY_KIND_MEMORY2
Memory activity tracking allocation and freeing of the memory The corresponding activity record structure is CUpti_ActivityMemory4.

enumerator CUPTI_ACTIVITY_KIND_MEMORY_POOL
Memory pool activity tracking creation, destruction and trimming of the memory pool.
The corresponding activity record structure is CUpti_ActivityMemoryPool3.

enumerator CUPTI_ACTIVITY_KIND_GRAPH_TRACE
Activity record for graph-level information.
The corresponding activity record structure is CUpti_ActivityGraphTrace2.

enumerator CUPTI_ACTIVITY_KIND_JIT
JIT (Just-in-time) operation tracking.
The corresponding activity record structure is CUpti_ActivityJit2.

enumerator CUPTI_ACTIVITY_KIND_DEVICE_GRAPH_TRACE
This activity can not be directly enabled or disabled.
It is enabled when CUPTI_ACTIVITY_KIND_GRAPH_TRACE is enabled and device graph trace is enabled through API cuptiActivityEnableDeviceGraph(). The corresponding activity record structure is CUpti_ActivityDeviceGraphTrace.

enumerator CUPTI_ACTIVITY_KIND_MEM_DECOMPRESS
Tracing batches of copies that are to be decompressed.
The corresponding activity record structure is CUpti_ActivityMemDecompress.

enumerator CUPTI_ACTIVITY_KIND_CONFIDENTIAL_COMPUTE_ROTATION
Tracing new overheads introduced on some hardware due when confidential computing is enabled.
The corresponding activity record structure is CUpti_ActivityConfidentialComputeRotation.

enumerator CUPTI_ACTIVITY_KIND_GRAPH_HOST_NODE
Tracing of host execution nodes of the CUDA graph, i.e.
nodes of type CU_GRAPH_NODE_TYPE_HOST. The corresponding activity record structure is CUpti_ActivityGraphHostNode.

enumerator CUPTI_ACTIVITY_KIND_COMPUTE_ENGINE_CTX_SWITCH
An activity denoting the switching of Compute Engine contexts in/out of the GPU.
The corresponding activity record structure is CUpti_ActivityComputeEngineCtxSwitch.

enumerator CUPTI_ACTIVITY_KIND_HOST_LAUNCH
An activity kind denoting the launch of a host function through cu(da)LaunchHostFunc API.
The corresponding activity record structure is CUpti_ActivityHostLaunch.

enumerator CUPTI_ACTIVITY_KIND_COUNT
Count of supported activity kinds.

enumerator CUPTI_ACTIVITY_KIND_FORCE_INT


enum CUpti_ActivityLaunchType
The type of the CUDA kernel launch.
Values:

enumerator CUPTI_ACTIVITY_LAUNCH_TYPE_REGULAR
The kernel was launched via a regular kernel call.

enumerator CUPTI_ACTIVITY_LAUNCH_TYPE_COOPERATIVE_SINGLE_DEVICE
The kernel was launched via API cudaLaunchCooperativeKernel() or cuLaunchCooperativeKernel()

enumerator CUPTI_ACTIVITY_LAUNCH_TYPE_COOPERATIVE_MULTI_DEVICE
The kernel was launched via API cudaLaunchCooperativeKernelMultiDevice() or cuLaunchCooperativeKernelMultiDevice()

enumerator CUPTI_ACTIVITY_LAUNCH_TYPE_CBL_COMMANDLIST
The kernel was launched as a CBL commandlist.


enum CUpti_ActivityMemcpyKind
The kind of a memory copy, indicating the source and destination targets of the copy.
Each kind represents the source and destination targets of a memory copy. Targets are host, device, and array.
Values:

enumerator CUPTI_ACTIVITY_MEMCPY_KIND_UNKNOWN
The memory copy kind is not known.

enumerator CUPTI_ACTIVITY_MEMCPY_KIND_HTOD
A host to device memory copy.

enumerator CUPTI_ACTIVITY_MEMCPY_KIND_DTOH
A device to host memory copy.

enumerator CUPTI_ACTIVITY_MEMCPY_KIND_HTOA
A host to device array memory copy.

enumerator CUPTI_ACTIVITY_MEMCPY_KIND_ATOH
A device array to host memory copy.

enumerator CUPTI_ACTIVITY_MEMCPY_KIND_ATOA
A device array to device array memory copy.

enumerator CUPTI_ACTIVITY_MEMCPY_KIND_ATOD
A device array to device memory copy.

enumerator CUPTI_ACTIVITY_MEMCPY_KIND_DTOA
A device to device array memory copy.

enumerator CUPTI_ACTIVITY_MEMCPY_KIND_DTOD
A device to device memory copy on the same device.

enumerator CUPTI_ACTIVITY_MEMCPY_KIND_HTOH
A host to host memory copy.

enumerator CUPTI_ACTIVITY_MEMCPY_KIND_PTOP
A peer to peer memory copy across different devices.

enumerator CUPTI_ACTIVITY_MEMCPY_KIND_FORCE_INT


enum CUpti_ActivityMemoryKind
The kinds of memory accessed by a memory operation/copy.
Each kind represents the type of the memory accessed by a memory operation/copy.
Values:

enumerator CUPTI_ACTIVITY_MEMORY_KIND_UNKNOWN
The memory kind is unknown.

enumerator CUPTI_ACTIVITY_MEMORY_KIND_PAGEABLE
The memory is pageable.

enumerator CUPTI_ACTIVITY_MEMORY_KIND_PINNED
The memory is pinned.

enumerator CUPTI_ACTIVITY_MEMORY_KIND_DEVICE
The memory is on the device.

enumerator CUPTI_ACTIVITY_MEMORY_KIND_ARRAY
The memory is an array.

enumerator CUPTI_ACTIVITY_MEMORY_KIND_MANAGED
The memory is managed.

enumerator CUPTI_ACTIVITY_MEMORY_KIND_DEVICE_STATIC
The memory is device static.

enumerator CUPTI_ACTIVITY_MEMORY_KIND_MANAGED_STATIC
The memory is managed static.

enumerator CUPTI_ACTIVITY_MEMORY_KIND_FORCE_INT


enum CUpti_ActivityMemoryOperationType
Memory operation types.
Describes the type of memory operation, to be used with CUpti_ActivityMemory4.
Values:

enumerator CUPTI_ACTIVITY_MEMORY_OPERATION_TYPE_INVALID
The operation is invalid.

enumerator CUPTI_ACTIVITY_MEMORY_OPERATION_TYPE_ALLOCATION
Memory is allocated.

enumerator CUPTI_ACTIVITY_MEMORY_OPERATION_TYPE_RELEASE
Memory is released.

enumerator CUPTI_ACTIVITY_MEMORY_OPERATION_TYPE_FORCE_INT


enum CUpti_ActivityMemoryPoolOperationType
Memory pool operation types.
Describes the type of memory pool operation, to be used with CUpti_ActivityMemoryPool2.
Values:

enumerator CUPTI_ACTIVITY_MEMORY_POOL_OPERATION_TYPE_INVALID
The operation is invalid.

enumerator CUPTI_ACTIVITY_MEMORY_POOL_OPERATION_TYPE_CREATED
Memory pool is created.

enumerator CUPTI_ACTIVITY_MEMORY_POOL_OPERATION_TYPE_DESTROYED
Memory pool is destroyed.

enumerator CUPTI_ACTIVITY_MEMORY_POOL_OPERATION_TYPE_TRIMMED
Memory pool is trimmed.

enumerator CUPTI_ACTIVITY_MEMORY_POOL_OPERATION_TYPE_FORCE_INT


enum CUpti_ActivityMemoryPoolType
Memory pool types.
Describes the type of memory pool, to be used with CUpti_ActivityMemory4.
Values:

enumerator CUPTI_ACTIVITY_MEMORY_POOL_TYPE_INVALID
The operation is invalid.

enumerator CUPTI_ACTIVITY_MEMORY_POOL_TYPE_LOCAL
Memory pool is local to the process.

enumerator CUPTI_ACTIVITY_MEMORY_POOL_TYPE_IMPORTED
Memory pool is imported by the process.

enumerator CUPTI_ACTIVITY_MEMORY_POOL_TYPE_FORCE_INT


enum CUpti_ActivityObjectKind
The kinds of activity objects.

See also
CUpti_ActivityObjectKindId

Values:

enumerator CUPTI_ACTIVITY_OBJECT_UNKNOWN
The object kind is not known.

enumerator CUPTI_ACTIVITY_OBJECT_PROCESS
A process.

enumerator CUPTI_ACTIVITY_OBJECT_THREAD
A thread.

enumerator CUPTI_ACTIVITY_OBJECT_DEVICE
A device.

enumerator CUPTI_ACTIVITY_OBJECT_CONTEXT
A context.

enumerator CUPTI_ACTIVITY_OBJECT_STREAM
A stream.

enumerator CUPTI_ACTIVITY_OBJECT_FORCE_INT


enum CUpti_ActivityOverheadKind
The kinds of activity overhead.
Values:

enumerator CUPTI_ACTIVITY_OVERHEAD_UNKNOWN
The overhead kind is not known.

enumerator CUPTI_ACTIVITY_OVERHEAD_DRIVER_COMPILER
Compiler overhead.

enumerator CUPTI_ACTIVITY_OVERHEAD_CUPTI_BUFFER_FLUSH
Activity buffer flush overhead.

enumerator CUPTI_ACTIVITY_OVERHEAD_CUPTI_INSTRUMENTATION
CUPTI instrumentation overhead.

enumerator CUPTI_ACTIVITY_OVERHEAD_CUPTI_RESOURCE
CUPTI resource creation and destruction overhead.

enumerator CUPTI_ACTIVITY_OVERHEAD_RUNTIME_TRIGGERED_MODULE_LOADING
CUDA Runtime triggered module loading overhead.

enumerator CUPTI_ACTIVITY_OVERHEAD_LAZY_FUNCTION_LOADING
Lazy function loading overhead.

enumerator CUPTI_ACTIVITY_OVERHEAD_COMMAND_BUFFER_FULL
Overhead due to lack of command buffer space.
Refer CUpti_ActivityOverheadCommandBufferFullData for more details.

enumerator CUPTI_ACTIVITY_OVERHEAD_ACTIVITY_BUFFER_REQUEST
Overhead due to activity buffer request.

enumerator CUPTI_ACTIVITY_OVERHEAD_UVM_ACTIVITY_INIT
Overhead due to UVM activity initialization.

enumerator CUPTI_ACTIVITY_OVERHEAD_FORCE_INT


enum CUpti_ActivityPCSamplingPeriod
Sampling period for PC sampling method.
Sampling period can be set using cuptiActivityConfigurePCSampling
Values:

enumerator CUPTI_ACTIVITY_PC_SAMPLING_PERIOD_INVALID
The PC sampling period is not set.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_PERIOD_MIN
Minimum sampling period available on the device.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_PERIOD_LOW
Sampling period in lower range.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_PERIOD_MID
Medium sampling period.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_PERIOD_HIGH
Sampling period in higher range.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_PERIOD_MAX
Maximum sampling period available on the device.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_PERIOD_FORCE_INT


enum CUpti_ActivityPCSamplingStallReason
The stall reason for PC sampling activity.
Values:

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_INVALID
Invalid reason.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_NONE
No stall, instruction is selected for issue.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_INST_FETCH
Warp is blocked because next instruction is not yet available, because of instruction cache miss, or because of branching effects.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_EXEC_DEPENDENCY
Instruction is waiting on an arithmetic dependency.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_MEMORY_DEPENDENCY
Warp is blocked because it is waiting for a memory access to complete.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_TEXTURE
Texture sub-system is fully utilized or has too many outstanding requests.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_SYNC
Warp is blocked as it is waiting at __syncthreads() or at memory barrier.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_CONSTANT_MEMORY_DEPENDENCY
Warp is blocked waiting for constant memory and immediate memory access to complete.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_PIPE_BUSY
Compute operation cannot be performed due to the required resources not being available.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_MEMORY_THROTTLE
Warp is blocked because there are too many pending memory operations.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_NOT_SELECTED
Warp was ready to issue, but some other warp issued instead.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_OTHER
Miscellaneous reasons.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_SLEEPING
Sleeping.

enumerator CUPTI_ACTIVITY_PC_SAMPLING_STALL_FORCE_INT


enum CUpti_ActivityPartitionedGlobalCacheConfig
Partitioned global caching option.
Values:

enumerator CUPTI_ACTIVITY_PARTITIONED_GLOBAL_CACHE_CONFIG_UNKNOWN
Partitioned global cache config unknown.

enumerator CUPTI_ACTIVITY_PARTITIONED_GLOBAL_CACHE_CONFIG_NOT_SUPPORTED
Partitioned global cache not supported.

enumerator CUPTI_ACTIVITY_PARTITIONED_GLOBAL_CACHE_CONFIG_OFF
Partitioned global cache config off.

enumerator CUPTI_ACTIVITY_PARTITIONED_GLOBAL_CACHE_CONFIG_ON
Partitioned global cache config on.

enumerator CUPTI_ACTIVITY_PARTITIONED_GLOBAL_CACHE_CONFIG_FORCE_INT


enum CUpti_ActivityPreemptionKind
The kind of a preemption activity.
Values:

enumerator CUPTI_ACTIVITY_PREEMPTION_KIND_UNKNOWN
The preemption kind is not known.

enumerator CUPTI_ACTIVITY_PREEMPTION_KIND_SAVE
Preemption to save CDP block.

enumerator CUPTI_ACTIVITY_PREEMPTION_KIND_RESTORE
Preemption to restore CDP block.

enumerator CUPTI_ACTIVITY_PREEMPTION_KIND_FORCE_INT


enum CUpti_ActivityStreamFlag
stream type.
The types of stream to be used with CUpti_ActivityStream.
Values:

enumerator CUPTI_ACTIVITY_STREAM_CREATE_FLAG_UNKNOWN
Unknown data.

enumerator CUPTI_ACTIVITY_STREAM_CREATE_FLAG_DEFAULT
Default stream.

enumerator CUPTI_ACTIVITY_STREAM_CREATE_FLAG_NON_BLOCKING
Non-blocking stream.

enumerator CUPTI_ACTIVITY_STREAM_CREATE_FLAG_NULL
Null stream.

enumerator CUPTI_ACTIVITY_STREAM_CREATE_MASK
Stream create Mask.

enumerator CUPTI_ACTIVITY_STREAM_CREATE_FLAG_FORCE_INT


enum CUpti_ActivitySynchronizationType
Synchronization type.
The types of synchronization to be used with CUpti_ActivitySynchronization2.
Values:

enumerator CUPTI_ACTIVITY_SYNCHRONIZATION_TYPE_UNKNOWN
Unknown data.

enumerator CUPTI_ACTIVITY_SYNCHRONIZATION_TYPE_EVENT_SYNCHRONIZE
Event synchronize API.

enumerator CUPTI_ACTIVITY_SYNCHRONIZATION_TYPE_STREAM_WAIT_EVENT
Stream wait event API.

enumerator CUPTI_ACTIVITY_SYNCHRONIZATION_TYPE_STREAM_SYNCHRONIZE
Stream synchronize API.

enumerator CUPTI_ACTIVITY_SYNCHRONIZATION_TYPE_CONTEXT_SYNCHRONIZE
Context synchronize API.

enumerator CUPTI_ACTIVITY_SYNCHRONIZATION_TYPE_FORCE_INT


enum CUpti_ActivityThreadIdType
Thread-Id types.
CUPTI uses different methods to obtain the thread-id depending on the support and the underlying platform. This enum documents these methods for each type. APIs cuptiSetThreadIdType and cuptiGetThreadIdType can be used to set and get the thread-id type.
Values:

enumerator CUPTI_ACTIVITY_THREAD_ID_TYPE_DEFAULT
Default type Windows uses API GetCurrentThreadId() Linux/Mac/Android/QNX use POSIX pthread API pthread_self()

enumerator CUPTI_ACTIVITY_THREAD_ID_TYPE_SYSTEM
This type is based on the system API available on the underlying platform and thread-id obtained is supposed to be unique for the process lifetime.
Windows uses API GetCurrentThreadId() Linux uses syscall SYS_gettid Mac uses syscall SYS_thread_selfid Android/QNX use gettid()

enumerator CUPTI_ACTIVITY_THREAD_ID_TYPE_SIZE
Add new enums before this field.

enumerator CUPTI_ACTIVITY_THREAD_ID_TYPE_FORCE_INT


enum CUpti_ActivityUnifiedMemoryAccessType
Memory access type for unified memory page faults.
This is valid for CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_GPU_PAGE_FAULT and CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_CPU_PAGE_FAULT_COUNT
Values:

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_ACCESS_TYPE_UNKNOWN
The unified memory access type is not known.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_ACCESS_TYPE_READ
The page fault was triggered by read memory instruction.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_ACCESS_TYPE_WRITE
The page fault was triggered by write memory instruction.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_ACCESS_TYPE_ATOMIC
The page fault was triggered by atomic memory instruction.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_ACCESS_TYPE_PREFETCH
The page fault was triggered by memory prefetch operation.


enum CUpti_ActivityUnifiedMemoryCounterKind
Kind of the Unified Memory counter.
Many activities are associated with Unified Memory mechanism; among them are transfers from host to device, device to host, page fault at host side.
Values:

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_UNKNOWN
The unified memory counter kind is not known.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_HTOD
Number of bytes transferred from host to device.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_DTOH
Number of bytes transferred from device to host.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_CPU_PAGE_FAULT_COUNT
Number of CPU page faults, this is only supported on 64 bit Linux and Mac platforms.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_GPU_PAGE_FAULT
Number of GPU page faults, this is only supported on devices with compute capability 6.0 and higher and 64 bit Linux platforms.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THRASHING
Thrashing occurs when data is frequently accessed by multiple processors and has to be constantly migrated around to achieve data locality.
In this case the overhead of migration may exceed the benefits of locality. This is only supported on 64 bit Linux platforms.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THROTTLING
Throttling is a prevention technique used by the driver to avoid further thrashing.
Here, the driver doesn’t service the fault for one of the contending processors for a specific period of time, so that the other processor can run at full-speed. This is only supported on 64 bit Linux platforms.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_REMOTE_MAP
In case throttling does not help, the driver tries to pin the memory to a processor for a specific period of time.
One of the contending processors will have slow access to the memory, while the other will have fast access. This is only supported on 64 bit Linux platforms.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_DTOD
Number of bytes transferred from one device to another device.
This is only supported on 64 bit Linux platforms.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_COUNT

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_FORCE_INT


enum CUpti_ActivityUnifiedMemoryCounterScope
Scope of the unified memory counter (deprecated in CUDA 7.0)
Values:

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_SCOPE_UNKNOWN
The unified memory counter scope is not known.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_SCOPE_PROCESS_SINGLE_DEVICE
Collect unified memory counter for single process on one device.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_SCOPE_PROCESS_ALL_DEVICES
Collect unified memory counter for single process across all devices.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_SCOPE_COUNT

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_SCOPE_FORCE_INT


enum CUpti_ActivityUnifiedMemoryMigrationCause
Migration cause of the Unified Memory counter.
This is valid for CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_HTOD and CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_DTOH
Values:

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_MIGRATION_CAUSE_UNKNOWN
The unified memory migration cause is not known.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_MIGRATION_CAUSE_USER
The unified memory migrated due to an explicit call from the user e.g.
cudaMemPrefetchAsync

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_MIGRATION_CAUSE_COHERENCE
The unified memory migrated to guarantee data coherence e.g.
CPU/GPU faults on Pascal+ and kernel launch on pre-Pascal GPUs

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_MIGRATION_CAUSE_PREFETCH
The unified memory was speculatively migrated by the UVM driver before being accessed by the destination processor to improve performance.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_MIGRATION_CAUSE_EVICTION
The unified memory migrated to the CPU because it was evicted to make room for another block of memory on the GPU.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_MIGRATION_CAUSE_ACCESS_COUNTERS
The unified memory migrated to another processor because of access counter notifications.
Only frequently accessed pages are migrated between CPU and GPU, or between peer GPUs.


enum CUpti_ActivityUnifiedMemoryRemoteMapCause
Remote memory map cause of the Unified Memory counter.
This is valid for CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_REMOTE_MAP
Values:

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_REMOTE_MAP_CAUSE_UNKNOWN
The cause of mapping to remote memory was unknown.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_REMOTE_MAP_CAUSE_COHERENCE
Mapping to remote memory was added to maintain data coherence.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_REMOTE_MAP_CAUSE_THRASHING
Mapping to remote memory was added to prevent further thrashing.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_REMOTE_MAP_CAUSE_POLICY
Mapping to remote memory was added to enforce the hints specified by the programmer or by performance heuristics of the UVM driver.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_REMOTE_MAP_CAUSE_OUT_OF_MEMORY
Mapping to remote memory was added because there is no more memory available on the processor and eviction was not possible.

enumerator CUPTI_ACTIVITY_UNIFIED_MEMORY_REMOTE_MAP_CAUSE_EVICTION
Mapping to remote memory was added after the memory was evicted to make room for another block of memory on the GPU.


enum CUpti_ChannelType
Values:

enumerator CUPTI_CHANNEL_TYPE_INVALID

enumerator CUPTI_CHANNEL_TYPE_COMPUTE
Channel is used for standard work launch and tracking.

enumerator CUPTI_CHANNEL_TYPE_ASYNC_MEMCPY
Channel is used by an asynchronous copy engine For confidential compute configurations, work launch and completion are done using the copy engines.

enumerator CUPTI_CHANNEL_TYPE_DECOMP
Channel is used for memory decompression operations.

enumerator CUPTI_CHANNEL_TYPE_FORCE_INT


enum CUpti_ComputeEngineCtxSwitchOperationType
The operation type of CUDA context switch event records.
Values:

enumerator CUPTI_COMPUTE_ENGINE_CTX_SWITCH_OPERATION_INVALID

enumerator CUPTI_COMPUTE_ENGINE_CTX_SWITCH_OPERATION_START
The start of the CUDA context switch operation.

enumerator CUPTI_COMPUTE_ENGINE_CTX_SWITCH_OPERATION_END
The end of the CUDA context switch operation.

enumerator CUPTI_COMPUTE_ENGINE_CTX_SWITCH_OPERATION_COUNT


enum CUpti_ConfidentialComputeRotationEventType
Values:

enumerator CUPTI_CONFIDENTIAL_COMPUTE_INVALID_ROTATION_EVENT

enumerator CUPTI_CONFIDENTIAL_COMPUTE_KEY_ROTATION_CHANNEL_BLOCKED
This channel has been blocked from accepting new CUDA work so a key rotation can be done.

enumerator CUPTI_CONFIDENTIAL_COMPUTE_KEY_ROTATION_CHANNEL_DRAINED
This channel remains blocked and all queued CUDA work has completed.
Other clients or channels may cause delays in starting the key rotation.

enumerator CUPTI_CONFIDENTIAL_COMPUTE_KEY_ROTATION_CHANNEL_UNBLOCKED
Key rotations have completed and this channel is unblocked.

enumerator CUPTI_CONFIDENTIAL_COMPUTE_EVENT_TYPE_FORCE_INT


enum CUpti_ContextCigMode
CIG (CUDA in Graphics) Modes.
Describes the CIG modes associated with the CUDA context.
Values:

enumerator CUPTI_CONTEXT_CIG_MODE_NONE
Regular (non-CIG) mode.

enumerator CUPTI_CONTEXT_CIG_MODE_CIG
CIG mode.

enumerator CUPTI_CONTEXT_CIG_MODE_CIG_FALLBACK
CIG fallback mode.

enumerator CUPTI_CONTEXT_CIG_MODE_FORCE_INT


enum CUpti_DevType
The device type for device connected to NVLink.
Values:

enumerator CUPTI_DEV_TYPE_INVALID

enumerator CUPTI_DEV_TYPE_GPU
The device type is GPU.

enumerator CUPTI_DEV_TYPE_NPU
The device type is NVLink processing unit in CPU.

enumerator CUPTI_DEV_TYPE_FORCE_INT


enum CUpti_DeviceGraphLaunchMode
The launch mode for device graph execution.
Values:

enumerator CUPTI_DEVICE_GRAPH_LAUNCH_MODE_INVALID

enumerator CUPTI_DEVICE_GRAPH_LAUNCH_MODE_FIRE_AND_FORGET

enumerator CUPTI_DEVICE_GRAPH_LAUNCH_MODE_TAIL

enumerator CUPTI_DEVICE_GRAPH_LAUNCH_MODE_FIRE_AND_FORGET_AS_SIBLING


enum CUpti_DeviceVirtualizationMode
This indicates the virtualization mode in which CUDA device is running.
Values:

enumerator CUPTI_DEVICE_VIRTUALIZATION_MODE_NONE
No virtualization mode is associated with the device i.e.
it’s a baremetal GPU

enumerator CUPTI_DEVICE_VIRTUALIZATION_MODE_PASS_THROUGH
The device is associated with the pass-through GPU.
In this mode, an entire physical GPU is directly assigned to one virtual machine (VM).

enumerator CUPTI_DEVICE_VIRTUALIZATION_MODE_VIRTUAL_GPU
The device is associated with the virtual GPU (vGPU).
In this mode multiple virtual machines (VMs) have simultaneous, direct access to a single physical GPU.

enumerator CUPTI_DEVICE_VIRTUALIZATION_MODE_FORCE_INT


enum CUpti_EnvironmentClocksThrottleReason
Reasons for clock throttling.
The possible reasons that a clock can be throttled. There can be more than one reason that a clock is being throttled so these types can be combined by bitwise OR. These are used in the clocksThrottleReason field in the Environment Activity Record.
Values:

enumerator CUPTI_CLOCKS_THROTTLE_REASON_GPU_IDLE
Nothing is running on the GPU and the clocks are dropping to idle state.

enumerator CUPTI_CLOCKS_THROTTLE_REASON_USER_DEFINED_CLOCKS
The GPU clocks are limited by a user specified limit.

enumerator CUPTI_CLOCKS_THROTTLE_REASON_SW_POWER_CAP
A software power scaling algorithm is reducing the clocks below requested clocks.

enumerator CUPTI_CLOCKS_THROTTLE_REASON_HW_SLOWDOWN
Hardware slowdown to reduce the clock by a factor of two or more is engaged.
This is an indicator of one of the following: 1) Temperature is too high, 2) External power brake assertion is being triggered (e.g. by the system power supply), 3) Change in power state.

enumerator CUPTI_CLOCKS_THROTTLE_REASON_UNKNOWN
Some unspecified factor is reducing the clocks.

enumerator CUPTI_CLOCKS_THROTTLE_REASON_UNSUPPORTED
Throttle reason is not supported for this GPU.

enumerator CUPTI_CLOCKS_THROTTLE_REASON_NONE
No clock throttling.

enumerator CUPTI_CLOCKS_THROTTLE_REASON_FORCE_INT


enum CUpti_ExternalCorrelationKind
The kind of external APIs supported for correlation.
Custom correlation kinds are reserved for usage in external tools.

See also
CUpti_ActivityExternalCorrelation

Values:

enumerator CUPTI_EXTERNAL_CORRELATION_KIND_INVALID

enumerator CUPTI_EXTERNAL_CORRELATION_KIND_UNKNOWN
The external API is unknown to CUPTI.

enumerator CUPTI_EXTERNAL_CORRELATION_KIND_OPENACC
The external API is OpenACC.

enumerator CUPTI_EXTERNAL_CORRELATION_KIND_CUSTOM0
The external API is custom0.

enumerator CUPTI_EXTERNAL_CORRELATION_KIND_CUSTOM1
The external API is custom1.

enumerator CUPTI_EXTERNAL_CORRELATION_KIND_CUSTOM2
The external API is custom2.

enumerator CUPTI_EXTERNAL_CORRELATION_KIND_SIZE
Add new kinds before this line.

enumerator CUPTI_EXTERNAL_CORRELATION_KIND_FORCE_INT


enum CUpti_FuncShmemLimitConfig
The shared memory limit per block config for a kernel This should be used to set ‘cudaOccFuncShmemConfig’ field in occupancy calculator API.
Values:

enumerator CUPTI_FUNC_SHMEM_LIMIT_DEFAULT
The shared memory limit config is default.

enumerator CUPTI_FUNC_SHMEM_LIMIT_OPTIN
User has opted for a higher dynamic shared memory limit using function attribute ‘cudaFuncAttributeMaxDynamicSharedMemorySize’ for runtime API or CU_FUNC_ATTRIBUTE_MAX_DYNAMIC_SHARED_SIZE_BYTES for driver API.

enumerator CUPTI_FUNC_SHMEM_LIMIT_FORCE_INT


enum CUpti_LinkFlag
Link flags.
Describes link properties, to be used with CUpti_ActivityNvLink.
Values:

enumerator CUPTI_LINK_FLAG_INVALID
The flag is invalid.

enumerator CUPTI_LINK_FLAG_PEER_ACCESS
Is peer to peer access supported by this link.

enumerator CUPTI_LINK_FLAG_SYSMEM_ACCESS
Is system memory access supported by this link.

enumerator CUPTI_LINK_FLAG_PEER_ATOMICS
Is peer atomic access supported by this link.

enumerator CUPTI_LINK_FLAG_SYSMEM_ATOMICS
Is system memory atomic access supported by this link.

enumerator CUPTI_LINK_FLAG_FORCE_INT


enum CUpti_NvtxExtPayloadType
Values:

enumerator CUPTI_NVTX_EXT_PAYLOAD_TYPE_UNKNOWN
The payload type is not known.

enumerator CUPTI_NVTX_EXT_PAYLOAD_TYPE_SCHEMA
The payload type is a schema.

enumerator CUPTI_NVTX_EXT_PAYLOAD_TYPE_ENUM
The payload type is an enum.

enumerator CUPTI_NVTX_EXT_PAYLOAD_TYPE_FORCE_INT


enum CUpti_OpenAccConstructKind
The OpenAcc parent construct kind for OpenAcc activity records.
Values:

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_UNKNOWN

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_PARALLEL

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_KERNELS

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_LOOP

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_DATA

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_ENTER_DATA

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_EXIT_DATA

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_HOST_DATA

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_ATOMIC

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_DECLARE

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_INIT

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_SHUTDOWN

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_SET

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_UPDATE

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_ROUTINE

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_WAIT

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_RUNTIME_API

enumerator CUPTI_OPENACC_CONSTRUCT_KIND_FORCE_INT


enum CUpti_OpenAccEventKind
The OpenAcc event kind for OpenAcc activity records.

See also
CUpti_ActivityKindOpenAcc

Values:

enumerator CUPTI_OPENACC_EVENT_KIND_INVALID

enumerator CUPTI_OPENACC_EVENT_KIND_DEVICE_INIT

enumerator CUPTI_OPENACC_EVENT_KIND_DEVICE_SHUTDOWN

enumerator CUPTI_OPENACC_EVENT_KIND_RUNTIME_SHUTDOWN

enumerator CUPTI_OPENACC_EVENT_KIND_ENQUEUE_LAUNCH

enumerator CUPTI_OPENACC_EVENT_KIND_ENQUEUE_UPLOAD

enumerator CUPTI_OPENACC_EVENT_KIND_ENQUEUE_DOWNLOAD

enumerator CUPTI_OPENACC_EVENT_KIND_WAIT

enumerator CUPTI_OPENACC_EVENT_KIND_IMPLICIT_WAIT

enumerator CUPTI_OPENACC_EVENT_KIND_COMPUTE_CONSTRUCT

enumerator CUPTI_OPENACC_EVENT_KIND_UPDATE

enumerator CUPTI_OPENACC_EVENT_KIND_ENTER_DATA

enumerator CUPTI_OPENACC_EVENT_KIND_EXIT_DATA

enumerator CUPTI_OPENACC_EVENT_KIND_CREATE

enumerator CUPTI_OPENACC_EVENT_KIND_DELETE

enumerator CUPTI_OPENACC_EVENT_KIND_ALLOC

enumerator CUPTI_OPENACC_EVENT_KIND_FREE

enumerator CUPTI_OPENACC_EVENT_KIND_FORCE_INT


enum CUpti_OpenMpEventKind
Values:

enumerator CUPTI_OPENMP_EVENT_KIND_INVALID

enumerator CUPTI_OPENMP_EVENT_KIND_PARALLEL

enumerator CUPTI_OPENMP_EVENT_KIND_TASK

enumerator CUPTI_OPENMP_EVENT_KIND_THREAD

enumerator CUPTI_OPENMP_EVENT_KIND_IDLE

enumerator CUPTI_OPENMP_EVENT_KIND_WAIT_BARRIER

enumerator CUPTI_OPENMP_EVENT_KIND_WAIT_TASKWAIT

enumerator CUPTI_OPENMP_EVENT_KIND_FORCE_INT


enum CUpti_PcieDeviceType
Field to differentiate whether PCIE Activity record is of a GPU or a PCI Bridge.
Values:

enumerator CUPTI_PCIE_DEVICE_TYPE_GPU
PCIE GPU record.

enumerator CUPTI_PCIE_DEVICE_TYPE_BRIDGE
PCIE Bridge record.

enumerator CUPTI_PCIE_DEVICE_TYPE_FORCE_INT


enum CUpti_PcieGen
PCIE Generation.
Enumeration of PCIE Generation for pcie activity attribute pcieGeneration
Values:

enumerator CUPTI_PCIE_GEN_GEN1
PCIE Generation 1.

enumerator CUPTI_PCIE_GEN_GEN2
PCIE Generation 2.

enumerator CUPTI_PCIE_GEN_GEN3
PCIE Generation 3.

enumerator CUPTI_PCIE_GEN_GEN4
PCIE Generation 4.

enumerator CUPTI_PCIE_GEN_GEN5
PCIE Generation 5.

enumerator CUPTI_PCIE_GEN_GEN6
PCIE Generation 6.

enumerator CUPTI_PCIE_GEN_FORCE_INT


## 6.1.8. Functions


CUptiResult cuptiActivityConfigurePCSampling(

CUcontext ctx,
CUpti_ActivityPCSamplingConfig *config,

)
Set PC sampling configuration.
For Pascal and older GPU architectures this API must be called before enabling activity kind CUPTI_ACTIVITY_KIND_PC_SAMPLING. There is no such requirement for Volta and newer GPU architectures.
For Volta and newer GPU architectures if this API is called in the middle of execution, PC sampling configuration will be updated for subsequent kernel launches.
Starting with CUDA 13.0, this function is unsupported and should not be used. It always returns the error code CUPTI_ERROR_LEGACY_PROFILER_NOT_SUPPORTED.

Parameters:

ctx – The context
config – A pointer to CUpti_ActivityPCSamplingConfig structure containing PC sampling configuration.

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_OPERATION – if this api is called while some valid event collection method is set.
CUPTI_ERROR_INVALID_PARAMETER – if config is NULL or any parameter in the config structures is not a valid value
CUPTI_ERROR_NOT_SUPPORTED – Indicates that the system/device does not support the unified memory counters


CUptiResult cuptiActivityConfigureUnifiedMemoryCounter(

CUpti_ActivityUnifiedMemoryCounterConfig *config,
uint32_t count,

)
Set Unified Memory Counter configuration.
Set the configuration before enabling the corresponding activity kind CUPTI_ACTIVITY_KIND_UNIFIED_MEMORY_COUNTER. The API should be called after CUDA driver initialization.

Parameters:

config – A pointer to CUpti_ActivityUnifiedMemoryCounterConfig structures containing Unified Memory counter configuration.
count – Number of Unified Memory counter configuration structures

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_PARAMETER – if config is NULL or any parameter in the config structures is not a valid value
CUPTI_ERROR_UM_PROFILING_NOT_SUPPORTED – One potential reason is that platform (OS/arch) does not support the unified memory counters
CUPTI_ERROR_UM_PROFILING_NOT_SUPPORTED_ON_DEVICE – Indicates that the device does not support the unified memory counters
CUPTI_ERROR_UM_PROFILING_NOT_SUPPORTED_ON_NON_P2P_DEVICES – Indicates that multi-GPU configuration without P2P support between any pair of devices does not support the unified memory counters


CUptiResult cuptiActivityDisable(CUpti_ActivityKind kind)
Disable collection of a specific kind of activity record.
Disable collection of a specific kind of activity record. Multiple kinds can be disabled by calling this function multiple times. By default all activity kinds are disabled for collection.

Parameters:
kind – The kind of activity record to stop collecting

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_KIND – if the activity kind is not supported


CUptiResult cuptiActivityDisableContext(

CUcontext context,
CUpti_ActivityKind kind,

)
Disable collection of a specific kind of activity record for a context.
Disable collection of a specific kind of activity record for a context. This setting done by this API will supersede the global settings for activity records. Multiple kinds can be enabled by calling this function multiple times.

Parameters:

context – The context for which activity is to be disabled
kind – The kind of activity record to stop collecting

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_KIND – if the activity kind is not supported


CUptiResult cuptiActivityEnable(CUpti_ActivityKind kind)
Enable collection of a specific kind of activity record.
Enable collection of a specific kind of activity record. Multiple kinds can be enabled by calling this function multiple times. By default all activity kinds are disabled for collection.

Parameters:
kind – The kind of activity record to collect

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_NOT_COMPATIBLE – if the activity kind cannot be enabled
CUPTI_ERROR_INVALID_KIND – if the activity kind is not supported


CUptiResult cuptiActivityEnableAllSyncRecords(uint8_t enable)
Enables collecting records for all synchronization operations.
CUPTI provides CUDA event query and stream query records via CUPTI_ACTIVITY_KIND_SYNCHRONIZATION. Using this API, CUPTI client can disable to record CUDA event query and stream query records for queries for which the operations have not yet been completed on the CUDA event/stream.
By default, the record is generated for all CUDA events and stream irrespective of whether the operations have been completed on the CUDA event/stream.

Parameters:
enable – is a boolean, denoting whether to enable or disable the collection of all CUDA event query and stream query records

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –


CUptiResult cuptiActivityEnableAllocationSource(uint8_t enable)
Enables tracking the source library for memory allocation requests.
This API is used to control whether or not we track the source library of memory allocation requests. Default value is 0, i.e. it is not tracked. The activity kind CUPTI_ACTIVITY_KIND_MEMORY2 needs to be enabled, and if this flag is set, we get the full path of the shared object responsible for the GPU memory allocation request in the member source in the CUpti_ActivityMemory4 records. Also note that this feature adds runtime overhead.

Parameters:
enable – is a boolean, denoting whether the source library of the memory allocation request needs to be tracked

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –


CUptiResult cuptiActivityEnableAndDump(CUpti_ActivityKind kind)
Enable collection of a specific kind of activity record.
For certain activity kinds it dumps existing records.
In general, the behavior of this API is similar to the API cuptiActivityEnable i.e. it enables the collection of a specific kind of activity record. Additionally, this API can help in dumping the records for activities which happened in the past before enabling the corresponding activity kind. The API allows to get records for the current resource allocations done in CUDA For CUPTI_ACTIVITY_KIND_DEVICE, existing device records are dumped For CUPTI_ACTIVITY_KIND_CONTEXT, existing context records are dumped For CUPTI_ACTIVITY_KIND_STREAM, existing stream records are dumped For CUPTI_ACTIVITY_KIND_ NVLINK, existing NVLINK records are dumped For CUPTI_ACTIVITY_KIND_PCIE, existing PCIE records are dumped For other activities, the behavior is similar to the API cuptiActivityEnable
Device records are emitted in CUPTI on CUDA driver initialization. Those records can only be retrieved by the user if CUPTI is attached before CUDA initialization. Context and stream records are emitted on context and stream creation. The use case of the API is to provide the records for CUDA resources (contexts/streams/devices) that are currently active if user late attaches CUPTI.
Before calling this function, the user must register buffer callbacks to get the activity records by calling cuptiActivityRegisterCallbacks. If the user does not register the buffers and calls API cuptiActivityEnableAndDump, then CUPTI will enable the activity kind but not provide any records for that activity kind.

Parameters:
kind – The kind of activity record to collect

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_UNKNOWN – if buffer is not initialized.
CUPTI_ERROR_NOT_COMPATIBLE – if the activity kind cannot be enabled
CUPTI_ERROR_INVALID_KIND – if the activity kind is not supported


CUptiResult cuptiActivityEnableContext(

CUcontext context,
CUpti_ActivityKind kind,

)
Enable collection of a specific kind of activity record for a context.
Enable collection of a specific kind of activity record for a context. This setting done by this API will supersede the global settings for activity records enabled by cuptiActivityEnable. Multiple kinds can be enabled by calling this function multiple times.

Parameters:

context – The context for which activity is to be enabled
kind – The kind of activity record to collect

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_NOT_COMPATIBLE – if the activity kind cannot be enabled
CUPTI_ERROR_INVALID_KIND – if the activity kind is not supported


CUptiResult cuptiActivityEnableCudaEventDeviceTimestamps(

uint8_t enable,

)
Enable/Disable collecting device timestamp for CUPTI_ACTIVITY_KIND_CUDA_EVENT record.
CUPTI provides device timestamps via ‘deviceTimestamp’ field in CUPTI_ACTIVITY_KIND_CUDA_EVENT records. Using this API, CUPTI client can enable or disable the collection of CUDA event device timestamps. By default, the collection of CUDA event device timestamps is disabled.

Parameters:
enable – is a boolean, denoting whether to enable or disable the collection of CUDA event device timestamps

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –


CUptiResult cuptiActivityEnableDeviceGraph(uint8_t enable)
Controls the collection of records for device launched graphs.
This API is used to control the collection of records for device launched graphs. Default value is 0, i.e. these records are not collected. Default value is 1 if HW trace is enabled using API cuptiActivityEnableHWTrace. This API needs to be called before initialization of CUDA and this setting should not be changed during the profiling session.

Parameters:
enable – is a boolean, denoting whether these records should be collected

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –


CUptiResult cuptiActivityEnableDriverApi(

CUpti_CallbackId cbid,
uint8_t enable,

)
Controls the collection of activity records for specific CUDA Driver APIs.
Activity kind CUPTI_ACTIVITY_KIND_DRIVER controls the collection of either all CUDA Driver APIs or none. API cuptiActivityEnableDriverApi can be used for fine-grained control, it allows enabling/disabling tracing of a specific set of CUDA Driver APIs. To disable collection of a small set of CUDA Driver APIs, user can first enable the collection of all Driver APIs using the activity kind CUPTI_ACTIVITY_KIND_DRIVER and call this API to disable specific Driver APIs. And to enable the collection of a small set of CUDA Driver APIs, user can call this API without using the activity kind CUPTI_ACTIVITY_KIND_DRIVER.
Note: Activity kind CUPTI_ACTIVITY_KIND_DRIVER overrides the settings done by this API if it is called after the API.

Parameters:

cbid – callback id of the CUDA Driver API. This can be found in the header cupti_driver_cbid.h.
enable – is a boolean, denoting whether to enable or disable the collection

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –


CUptiResult cuptiActivityEnableHWTrace(uint8_t enable)
Enables the collection of CUDA kernel timestamps through Hardware Event System(HES).
This API enables the collection of CUDA kernel timestamps through HW events instead of the traditional SW instrumentation and semaphore based approach. This option is only available on Blackwell architecture. This API should be called after driver is initialized.

Parameters:
enable – is a boolean, denoting whether to enable or disable the collection through HW events

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED – if CUPTI is not initialized or the CUDA driver is not initialized
CUPTI_ERROR_NOT_SUPPORTED – if HW trace cannot be enabled on the current platform
CUPTI_ERROR_VIRTUALIZED_DEVICE_NOT_SUPPORTED –
CUPTI_ERROR_CONFIDENTIAL_COMPUTING_NOT_SUPPORTED –
CUPTI_ERROR_CMP_DEVICE_NOT_SUPPORTED –
CUPTI_ERROR_MIG_DEVICE_NOT_SUPPORTED –
CUPTI_ERROR_SLI_DEVICE_NOT_SUPPORTED –
CUPTI_ERROR_WSL_DEVICE_NOT_SUPPORTED –
CUPTI_ERROR_HES_TRACE_NOT_SUPPORTED_ON_MPS –


CUptiResult cuptiActivityEnableLatencyTimestamps(uint8_t enable)
Controls the collection of queued and submitted timestamps for kernels.
This API is used to control the collection of queued and submitted timestamps for kernels whose records are provided through the struct CUpti_ActivityKernel11. Default value is 0, i.e. these timestamps are not collected. This API needs to be called before initialization of CUDA and this setting should not be changed during the profiling session.
This API is not supported if the HW trace is enabled through the API cuptiActivityEnableHWTrace.

Parameters:
enable – is a boolean, denoting whether these timestamps should be collected

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –


CUptiResult cuptiActivityEnableLaunchAttributes(uint8_t enable)
Controls the collection of launch attributes for kernels.
This API is used to control the collection of launch attributes for kernels whose records are provided through the struct CUpti_ActivityKernel11. Default value is 0, i.e. these attributes are not collected.

Parameters:
enable – is a boolean denoting whether these launch attributes should be collected


CUptiResult cuptiActivityEnableRuntimeApi(

CUpti_CallbackId cbid,
uint8_t enable,

)
Controls the collection of activity records for specific CUDA Runtime APIs.
Activity kind CUPTI_ACTIVITY_KIND_RUNTIME controls the collection of either all CUDA Runtime APIs or none. API cuptiActivityEnableRuntimeApi can be used for fine-grained control, it allows enabling/disabling tracing of a specific set of CUDA Runtime APIs. To disable collection of a small set of CUDA Runtime APIs, user can first enable the collection of all Runtime APIs using the activity kind CUPTI_ACTIVITY_KIND_RUNTIME and call this API to disable specific Runtime APIs. And to enable the collection of a small set of CUDA Runtime APIs, user can call this API without using the activity kind CUPTI_ACTIVITY_KIND_RUNTIME.
Note: Activity kind CUPTI_ACTIVITY_KIND_RUNTIME overrides the settings done by this API if it is called after the API.

Parameters:

cbid – callback id of the CUDA Runtime API. This can be found in the header cupti_runtime_cbid.h.
enable – is a boolean, denoting whether to enable or disable the collection

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –


CUptiResult cuptiActivityFlush(

CUcontext context,
uint32_t streamId,
uint32_t flag,

)
Wait for all activity records to be delivered via the completion callback.
This function does not return until all activity records associated with the specified context/stream are returned to the CUPTI client using the callback registered in cuptiActivityRegisterCallbacks. To ensure that all activity records are complete, the requested stream(s), if any, are synchronized.
If context is NULL, the global activity records (i.e. those not associated with a particular stream) are flushed (in this case no streams are synchronized). If context is a valid CUcontext and streamId is 0, the buffers of all streams of this context are flushed. Otherwise, the buffers of the specified stream in this context is flushed.
Before calling this function, the buffer handling callback api must be activated by calling cuptiActivityRegisterCallbacks.
DEPRECATED This method is deprecated CONTEXT and STREAMID will be ignored. Use cuptiActivityFlushAll to flush all data.

Parameters:

context – A valid CUcontext or NULL.
streamId – The stream ID.
flag – The flag can be set to indicate a forced flush. See CUpti_ActivityFlag

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_CUPTI_ERROR_INVALID_OPERATION – if not preceded by a successful call to cuptiActivityRegisterCallbacks
CUPTI_ERROR_UNKNOWN – an internal error occurred


CUptiResult cuptiActivityFlushAll(uint32_t flag)
Request to deliver activity records via the buffer completion callback.
This function returns the activity records associated with all contexts/streams (and the global buffers not associated with any stream) to the CUPTI client using the callback registered in cuptiActivityRegisterCallbacks.
This is a blocking call but it doesn’t issue any CUDA synchronization calls implicitly thus it’s not guaranteed that all activities are completed on the underlying devices. Activity record is considered as completed if it has all the information filled up including the timestamps if any. It is the client’s responsibility to issue necessary CUDA synchronization calls before calling this function if all activity records with complete information are expected to be delivered.
Behavior of the function based on the input flag: (-) ::For default flush i.e. when flag is set as 0, it returns all the activity buffers which have all the activity records completed, buffers need not to be full though. It doesn’t return buffers which have one or more incomplete records. Default flush can be done at a regular interval in a separate thread. (-) ::For forced flush i.e. when flag CUPTI_ACTIVITY_FLAG_FLUSH_FORCED is passed to the function, it returns all the activity buffers including the ones which have one or more incomplete activity records. It’s suggested for clients to do the force flush before the termination of the profiling session to allow remaining buffers to be delivered. In general, it can be done in the at-exit handler.
Before calling this function, the buffer handling callback api must be activated by calling cuptiActivityRegisterCallbacks.

See also
cuptiActivityFlushPeriod

Parameters:
flag – The flag can be set to indicate a forced flush. See CUpti_ActivityFlag

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_OPERATION – if not preceded by a successful call to cuptiActivityRegisterCallbacks
CUPTI_ERROR_UNKNOWN – an internal error occurred


CUptiResult cuptiActivityFlushPeriod(uint32_t time)
Sets the flush period for the worker thread.
CUPTI creates a worker thread to minimize the perturbance for the application created threads. CUPTI offloads certain operations from the application threads to the worker thread, this includes synchronization of profiling resources between host and device, delivery of the activity buffers to the client using the callback registered in cuptiActivityRegisterCallbacks. For performance reasons, CUPTI wakes up the worker thread based on certain heuristics.
This API is used to control the flush period of the worker thread. This setting will override the CUPTI heuristics. Setting time to zero disables the periodic flush and restores the default behavior.
Periodic flush can return only those activity buffers which are full and have all the activity records completed.
It’s allowed to use the API cuptiActivityFlushAll to flush the data on-demand, even when client sets the periodic flush.

See also
cuptiActivityFlushAll

Parameters:
time – flush period in milliseconds (ms)

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –


CUptiResult cuptiActivityGetAttribute(

CUpti_ActivityAttribute attr,
size_t *valueSize,
void *value,

)
Read an activity API attribute.
Read an activity API attribute and return it in *value.

Parameters:

attr – The attribute to read
valueSize – Size of buffer pointed by the value, and returns the number of bytes written to value
value – Returns the value of the attribute

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_PARAMETER – if valueSize or value is NULL, or if attr is not an activity attribute
CUPTI_ERROR_PARAMETER_SIZE_NOT_SUFFICIENT – Indicates that the value buffer is too small to hold the attribute value.


CUptiResult cuptiActivityGetNextRecord(

uint8_t *buffer,
size_t validBufferSizeBytes,
CUpti_Activity record,

)
Iterate over the activity records in a buffer.
This is a helper function to iterate over the activity records in a buffer. A buffer of activity records is typically obtained by receiving a CUpti_BuffersCallbackCompleteFunc callback. Stop iterating the buffer when an error occurs.
An example of typical usage: CUpti_Activity *record = NULL;
CUptiResult status = CUPTI_SUCCESS;
  do {
     status = cuptiActivityGetNextRecord(buffer, validSize, &record);
     if(status == CUPTI_SUCCESS) {
          // Use record here...
     }
     else if (status == CUPTI_ERROR_MAX_LIMIT_REACHED)
         break;
     else if (status == CUPTI_ERROR_INVALID_KIND)
         break;
     else {
         goto Error;
     }
   } while (1);

Parameters:

buffer – The buffer containing activity records
record – Inputs the previous record returned by cuptiActivityGetNextRecord and returns the next activity record from the buffer. If input value is NULL, returns the first activity record in the buffer. Records of certain kinds like CUPTI_ACTIVITY_KIND_CONCURRENT_KERNEL may contain invalid (0) timestamps, indicating that no timing information could be collected for lack of device memory.
validBufferSizeBytes – The number of valid bytes in the buffer.

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_MAX_LIMIT_REACHED – if no more records in the buffer
CUPTI_ERROR_INVALID_PARAMETER – if buffer is NULL.
CUPTI_ERROR_INVALID_KIND – if activity record is either incomplete or invalid


CUptiResult cuptiActivityGetNumDroppedRecords(

CUcontext context,
uint32_t streamId,
size_t *dropped,

)
Get the number of activity records that were dropped of insufficient buffer space.
Get the number of records that were dropped because of insufficient buffer space. The dropped count includes records that could not be recorded because CUPTI did not have activity buffer space available for the record (because the CUpti_BuffersCallbackRequestFunc callback did not return an empty buffer of sufficient size) and also CDP records that could not be record because the device-size buffer was full (size is controlled by the CUPTI_ACTIVITY_ATTR_DEVICE_BUFFER_SIZE_CDP attribute). The dropped count maintained for the queue is reset to zero when this function is called.

Parameters:

context – The context, or NULL to get dropped count from global queue
streamId – The stream ID
dropped – The number of records that were dropped since the last call to this function.

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_PARAMETER – if dropped is NULL


CUptiResult cuptiActivityPopExternalCorrelationId(

CUpti_ExternalCorrelationKind kind,
uint64_t *lastId,

)
Pop an external correlation id for the calling thread.
This function notifies CUPTI that the calling thread is leaving an external API region.

Parameters:

kind – The kind of external API activities should be correlated with.
lastId – If the function returns successful, contains the last external correlation id for this kind, can be NULL.

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – The external API kind is invalid.
CUPTI_ERROR_QUEUE_EMPTY – No external id is currently associated with kind.


CUptiResult cuptiActivityPushExternalCorrelationId(

CUpti_ExternalCorrelationKind kind,
uint64_t id,

)
Push an external correlation id for the calling thread.
This function notifies CUPTI that the calling thread is entering an external API region. When a CUPTI activity API record is created while within an external API region and CUPTI_ACTIVITY_KIND_EXTERNAL_CORRELATION is enabled, the activity API record will be preceded by a CUpti_ActivityExternalCorrelation record for each CUpti_ExternalCorrelationKind.

Parameters:

kind – The kind of external API activities should be correlated with.
id – External correlation id.

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – The external API kind is invalid


CUptiResult cuptiActivityRegisterCallbacks(

CUpti_BuffersCallbackRequestFunc funcBufferRequested,
CUpti_BuffersCallbackCompleteFunc funcBufferCompleted,

)
Registers callback functions with CUPTI for activity buffer handling.
This function registers two callback functions to be used in asynchronous buffer handling. If registered, activity record buffers are handled using asynchronous requested/completed callbacks from CUPTI.
Registering these callbacks prevents the client from using CUPTI’s blocking enqueue/dequeue functions.

Parameters:

funcBufferRequested – callback which is invoked when an empty buffer is requested by CUPTI
funcBufferCompleted – callback which is invoked when a buffer containing activity records is available from CUPTI

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if either funcBufferRequested or funcBufferCompleted is NULL


CUptiResult cuptiActivityRegisterTimestampCallback(

CUpti_TimestampCallbackFunc funcTimestamp,

)
Registers callback function with CUPTI for providing timestamp.
This function registers a callback function to obtain timestamp of user’s choice instead of using CUPTI provided timestamp. By default CUPTI uses different methods, based on the underlying platform, to retrieve the timestamp Linux (x86_64, aarch64 sbsa, aarch64) uses clock_gettime(CLOCK_REALTIME) Windows uses QueryPerformanceCounter() WSL (Windows Subsystem for Linux) uses clock_gettime(CLOCK_MONOTONIC_RAW) as CLOCK_REALTIME can cause backward jumps. QNX uses ClockCycles() Timestamps retrieved using these methods are converted to nanosecond if needed before usage.
Timestamps for GPU activities such as kernels, memory copies and memset operations are recorded directly on the GPU. To provide a unified and normalized view of these timestamps in relation to CPU time, CUPTI performs a linear interpolation to convert GPU timestamps into CPU timestamps during post-processing. For activities where timestamps are captured on the GPU, the timestamp callback is invoked during the post-processing phase, while converting GPU timestamps into CPU timestamps. For activities for which timestamps are captured directly on the CPU, the timestamp callback is invoked immediately at the time of the activity.
The registration of timestamp callback should be done before any of the CUPTI activity kinds are enabled to make sure that all the records report the timestamp using the callback function registered through cuptiActivityRegisterTimestampCallback API.
Changing the timestamp callback function in CUPTI through cuptiActivityRegisterTimestampCallback API in the middle of the profiling session can cause records generated prior to the change to report timestamps through previous timestamp method.

Parameters:
funcTimestamp – callback which is invoked when a timestamp is needed by CUPTI

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if funcTimestamp is NULL
CUPTI_ERROR_NOT_INITIALIZED –


CUptiResult cuptiActivitySetAttribute(

CUpti_ActivityAttribute attr,
size_t *valueSize,
void *value,

)
Write an activity API attribute.
Write an activity API attribute.

Parameters:

attr – The attribute to write
valueSize – The size, in bytes, of the value
value – The attribute value to write

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_PARAMETER – if valueSize or value is NULL, or if attr is not an activity attribute
CUPTI_ERROR_PARAMETER_SIZE_NOT_SUFFICIENT – Indicates that the value buffer is too small to hold the attribute value.


CUptiResult cuptiComputeCapabilitySupported(

int major,
int minor,
int *support,

)
Check support for a compute capability.
This function is used to check the support for a device based on it’s compute capability. It sets the support when the compute capability is supported by the current version of CUPTI, and clears it otherwise. This version of CUPTI might not support all GPUs sharing the same compute capability. It is suggested to use API cuptiDeviceSupported which provides correct information.

See also
cuptiDeviceSupported

Parameters:

major – The major revision number of the compute capability
minor – The minor revision number of the compute capability
support – Pointer to an integer to return the support status

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if support is NULL


CUptiResult cuptiDeviceSupported(CUdevice dev, int *support)
Check support for a compute device.
This function is used to check the support for a compute device. It sets the support when the device is supported by the current version of CUPTI, and clears it otherwise.

See also
cuptiComputeCapabilitySupported

Parameters:

dev – The device handle returned by CUDA Driver API cuDeviceGet
support – Pointer to an integer to return the support status

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if support is NULL
CUPTI_ERROR_INVALID_DEVICE – if dev is not a valid device


CUptiResult cuptiDeviceVirtualizationMode(

CUdevice dev,
CUpti_DeviceVirtualizationMode *mode,

)
Query the virtualization mode of the device.
This function is used to query the virtualization mode of the CUDA device.

Parameters:

dev – The device handle returned by CUDA Driver API cuDeviceGet
mode – Pointer to an CUpti_DeviceVirtualizationMode to return the virtualization mode

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_DEVICE – if dev is not a valid device
CUPTI_ERROR_INVALID_PARAMETER – if mode is NULL


CUptiResult cuptiFinalize(void)
Detach CUPTI from the running process.
This API detaches the CUPTI from the running process. It destroys and cleans up all the resources associated with CUPTI in the current process. After CUPTI detaches from the process, the process will keep on running with no CUPTI attached to it. For safe operation of the API, it is recommended this API is invoked from the exit callsite of any of the CUDA Driver or Runtime API. Otherwise CUPTI client needs to make sure that required CUDA synchronization and CUPTI activity buffer flush is done before calling the API. Sample code showing the usage of the API in the cupti callback handler code: void CUPTIAPI
cuptiCallbackHandler(void *userdata, CUpti_CallbackDomain domain,
    CUpti_CallbackId cbid, void *cbdata)
{
  const CUpti_CallbackData *cbInfo = (CUpti_CallbackData *)cbdata;

  // Take this code path when CUPTI detach is requested
  if (detachCupti) {
    switch(domain)
    {
      case CUPTI_CB_DOMAIN_RUNTIME_API:
      case CUPTI_CB_DOMAIN_DRIVER_API:
        if (cbInfo->callbackSite == CUPTI_API_EXIT) {
            // call the CUPTI detach API
            cuptiFinalize();
        }
        break;
      default:
        break;
    }
  }
}


CUptiResult cuptiGetAutoBoostState(

CUcontext context,
CUpti_ActivityAutoBoostState *state,

)
Get auto boost state.
The profiling results can be inconsistent in case auto boost is enabled. CUPTI tries to disable auto boost while profiling. It can fail to disable in cases where user does not have the permissions or CUDA_AUTO_BOOST env variable is set. The function can be used to query whether auto boost is enabled.

Parameters:

context – A valid CUcontext.
state – A pointer to CUpti_ActivityAutoBoostState structure which contains the current state and the id of the process that has requested the current state

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if CUcontext or state is NULL
CUPTI_ERROR_NOT_SUPPORTED – Indicates that the device does not support auto boost
CUPTI_ERROR_UNKNOWN – an internal error occurred


CUptiResult cuptiGetContextId(CUcontext context, uint32_t *contextId)
Get the ID of a context.
Get the ID of a context.

Parameters:

context – The context
contextId – Returns a process-unique ID for the context

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_CONTEXT – The context is NULL or not valid.
CUPTI_ERROR_INVALID_PARAMETER – if contextId is NULL


CUptiResult cuptiGetDeviceId(CUcontext context, uint32_t *deviceId)
Get the ID of a device.
If context is NULL, returns the ID of the device that contains the currently active context. If context is non-NULL, returns the ID of the device which contains that context. Operates in a similar manner to cudaGetDevice() or cuCtxGetDevice() but may be called from within callback functions.

Parameters:

context – The context, or NULL to indicate the current context.
deviceId – Returns the ID of the device that is current for the calling thread.

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_DEVICE – if unable to get device ID
CUPTI_ERROR_INVALID_PARAMETER – if deviceId is NULL


CUptiResult cuptiGetGraphExecId(CUgraphExec graphExec, uint32_t *pId)
Get the unique ID of executable graph.
Returns the unique ID of executable CUDA graph.

Parameters:

graphExec – The executable graph.
pId – Returns the unique ID of the executable graph

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_PARAMETER – if graph is NULL


CUptiResult cuptiGetGraphId(CUgraph graph, uint32_t *pId)
Get the unique ID of graph.
Returns the unique ID of CUDA graph.

Parameters:

graph – The graph.
pId – Returns the unique ID of the graph

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_PARAMETER – if graph is NULL


CUptiResult cuptiGetGraphNodeId(CUgraphNode node, uint64_t *nodeId)
Get the unique ID of a graph node.
Returns the unique ID of the CUDA graph node.

Parameters:

node – The graph node.
nodeId – Returns the unique ID of the node

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_PARAMETER – if node is NULL


CUptiResult cuptiGetLastError(void)
Returns the last error from a cupti call or callback.
Returns the last error that has been produced by any of the cupti api calls or the callback in the same host thread and resets it to CUPTI_SUCCESS.


CUptiResult cuptiGetStreamId(

CUcontext context,
CUstream stream,
uint32_t *streamId,

)
Get the ID of a stream.
Get the ID of a stream. The stream ID is unique within a context (i.e. all streams within a context will have unique stream IDs).
DEPRECATED This method is deprecated as of CUDA 8.0. Use method cuptiGetStreamIdEx instead.

Parameters:

context – If non-NULL then the stream is checked to ensure that it belongs to this context. Typically this parameter should be null.
stream – The stream
streamId – Returns a context-unique ID for the stream

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_STREAM – if unable to get stream ID, or if context is non-NULL and stream does not belong to the context
CUPTI_ERROR_INVALID_PARAMETER – if streamId is NULL


CUptiResult cuptiGetStreamIdEx(

CUcontext context,
CUstream stream,
uint8_t perThreadStream,
uint32_t *streamId,

)
Get the ID of a stream.
Get the ID of a stream. The stream ID is unique within a context (i.e. all streams within a context will have unique stream IDs).

Parameters:

context – If non-NULL then the stream is checked to ensure that it belongs to this context. Typically this parameter should be null.
stream – The stream
perThreadStream – Flag to indicate if program is compiled for per-thread streams
streamId – Returns a context-unique ID for the stream

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_INITIALIZED –
CUPTI_ERROR_INVALID_STREAM – if unable to get stream ID, or if context is non-NULL and stream does not belong to the context
CUPTI_ERROR_INVALID_PARAMETER – if streamId is NULL


CUptiResult cuptiGetThreadIdType(CUpti_ActivityThreadIdType *type)
Get the thread-id type.
Returns the thread-id type used in CUPTI

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if type is NULL


CUptiResult cuptiGetTimestamp(uint64_t *timestamp)
Get the CUPTI timestamp.
Returns a timestamp normalized to correspond with the start and end timestamps reported in the CUPTI activity records. The timestamp is reported in nanoseconds.

Parameters:
timestamp – Returns the CUPTI timestamp

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if timestamp is NULL


CUptiResult cuptiSetThreadIdType(CUpti_ActivityThreadIdType type)
Set the thread-id type.
CUPTI uses the method corresponding to set type to generate the thread-id. See enum CUpti_ActivityThreadIdType for the list of methods. Activity records having thread-id field contain the same value. Thread id type must not be changed during the profiling session to avoid thread-id value mismatch across activity records.

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_NOT_SUPPORTED – if type is not supported on the platform


## 6.1.9. Typedefs


typedef void (*CUpti_BuffersCallbackCompleteFunc)(CUcontext context, uint32_t streamId, uint8_t *buffer, size_t size, size_t validSize)
Function type for callback used by CUPTI to return a buffer of activity records.
This callback function returns to the CUPTI client a buffer containing activity records. The buffer contains validSize bytes of activity records which should be read using cuptiActivityGetNextRecord. The number of dropped records can be read using cuptiActivityGetNumDroppedRecords. After this call CUPTI relinquished ownership of the buffer and will not use it anymore. The client may return the buffer to CUPTI using the CUpti_BuffersCallbackRequestFunc callback. Note: CUDA 6.0 onwards, all buffers returned by this callback are global buffers i.e. there is no context/stream specific buffer. User needs to parse the global buffer to extract the context/stream specific activity records.

Param context:
The context this buffer is associated with. If NULL, the buffer is associated with the global activities. This field is deprecated as of CUDA 6.0 and will always be NULL.

Param streamId:
The stream id this buffer is associated with. This field is deprecated as of CUDA 6.0 and will always be NULL.

Param buffer:
The activity record buffer.

Param size:
The total size of the buffer in bytes as set in CUpti_BuffersCallbackRequestFunc.

Param validSize:
The number of valid bytes in the buffer.


typedef void (*CUpti_BuffersCallbackRequestFunc)(uint8_t buffer, size_t *size, size_t *maxNumRecords)
Function type for callback used by CUPTI to request an empty buffer for storing activity records.
This callback function signals the CUPTI client that an activity buffer is needed by CUPTI. The activity buffer is used by CUPTI to store activity records. The callback function can decline the request by setting *buffer to NULL. In this case CUPTI may drop activity records.

Param buffer:
Returns the new buffer. If set to NULL then no buffer is returned.

Param size:
Returns the size of the returned buffer.

Param maxNumRecords:
Returns the maximum number of records that should be placed in the buffer. If 0 then the buffer is filled with as many records as possible. If > 0 the buffer is filled with at most that many records before it is returned.


typedef uint64_t (*CUpti_TimestampCallbackFunc)(void)
Function type for callback used by CUPTI to request a timestamp to be used in activity records.
This callback function signals the CUPTI client that a timestamp needs to be returned. This timestamp would be treated as normalized timestamp to be used for various purposes in CUPTI. For example to store start and end timestamps reported in the CUPTI activity records. The returned timestamp must be in nanoseconds.

See also
cuptiActivityRegisterTimestampCallback