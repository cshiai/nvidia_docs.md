# 7.41. CUpti_ActivityJit2


struct CUpti_ActivityJit2
The activity record for JIT operations.
This activity represents the JIT operations (compile, load, store) of a CUmodule from the Compute Cache. Gives the exact hashed path of where the cached module is loaded from, or where the module will be stored after Just-In-Time (JIT) compilation.

Public Members

CUpti_ActivityKind kind
The activity record kind must be CUPTI_ACTIVITY_KIND_JIT.

CUpti_ActivityJitEntryType jitEntryType
The JIT entry type.

CUpti_ActivityJitOperationType jitOperationType
The JIT operation type.

uint32_t deviceId
The device ID.

uint64_t start
The start timestamp for the JIT operation, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the JIT operation.

uint64_t end
The end timestamp for the JIT operation, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the JIT operation.

uint32_t correlationId
The correlation ID of the JIT operation to which records belong to.
Each JIT operation is assigned a unique correlation ID that is identical to the correlation ID in the driver or runtime API activity record that launched the JIT operation.

uint32_t padding
Internal use.

uint64_t jitOperationCorrelationId
The correlation ID to correlate JIT compilation, load and store operations.
Each JIT compilation unit is assigned a unique correlation ID at the time of the JIT compilation. This correlation id can be used to find the matching JIT cache load/store records.

uint64_t cacheSize
The size of compute cache.

const char *cachePath
The path where the fat binary is cached.

uint32_t processId
The ID of the process where the JIT operation is executing.

uint32_t threadId
The ID of the thread where the JIT operation is executing.