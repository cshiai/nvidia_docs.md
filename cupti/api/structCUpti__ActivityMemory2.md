# 7.68. CUpti_ActivityMemory2


struct CUpti_ActivityMemory2
The activity record for memory.
This activity record represents a memory allocation and free operation (CUPTI_ACTIVITY_KIND_MEMORY2). This activity record provides separate records for memory allocation and memory release operations. This allows to correlate the corresponding driver and runtime API activity record with the memory operation.
Note: This activity record is an upgrade over CUpti_ActivityMemory enabled using the kind CUPTI_ACTIVITY_KIND_MEMORY. CUpti_ActivityMemory provides a single record for the memory allocation and memory release operations.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_MEMORY2.

CUpti_ActivityMemoryOperationType memoryOperationType
The memory operation requested by the user, CUpti_ActivityMemoryOperationType.

CUpti_ActivityMemoryKind memoryKind
The memory kind requested by the user, CUpti_ActivityMemoryKind.

uint32_t correlationId
The correlation ID of the memory operation.
Each memory operation is assigned a unique correlation ID that is identical to the correlation ID in the driver and runtime API activity record that launched the memory operation.

uint64_t address
The virtual address of the allocation.
The base address of the memory pool.

uint64_t bytes
The number of bytes of memory allocated.

uint64_t timestamp
The start timestamp for the memory operation, in ns.

uint64_t PC
The program counter of the memory operation.

uint32_t processId
The ID of the process to which this record belongs to.

uint32_t deviceId
The ID of the device where the memory operation is taking place.

uint32_t contextId
The ID of the context.
If context is NULL, contextId is set to CUPTI_INVALID_CONTEXT_ID.

uint32_t streamId
The ID of the stream.
If memory operation is not async, streamId is set to CUPTI_INVALID_STREAM_ID.

const char *name
Variable name.
This name is shared across all activity records representing the same symbol, and so should not be modified.

uint32_t isAsync
isAsync is set if memory operation happens through async memory APIs.

uint32_t pad1
Undefined.
Reserved for internal use.

CUpti_ActivityMemoryPoolType memoryPoolType
The type of the memory pool, CUpti_ActivityMemoryPoolType.

uint32_t pad2
Undefined.
Reserved for internal use.

uint64_t releaseThreshold
The release threshold of the memory pool in bytes.
releaseThreshold is valid for CUPTI_ACTIVITY_MEMORY_POOL_TYPE_LOCAL, CUpti_ActivityMemoryPoolType.

union CUpti_ActivityMemory2::[anonymous]::[anonymous] pool
The size of the memory pool in bytes and the processID of the memory pool.
size is valid if memoryPoolType is CUPTI_ACTIVITY_MEMORY_POOL_TYPE_LOCAL, CUpti_ActivityMemoryPoolType. processId is valid if memoryPoolType is CUPTI_ACTIVITY_MEMORY_POOL_TYPE_IMPORTED, CUpti_ActivityMemoryPoolType.

struct CUpti_ActivityMemory2::[anonymous] memoryPoolConfig
The memory pool configuration used for the memory operations.