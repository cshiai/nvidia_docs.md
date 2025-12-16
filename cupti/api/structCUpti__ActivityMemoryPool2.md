# 7.72. CUpti_ActivityMemoryPool2


struct CUpti_ActivityMemoryPool2
The activity record for memory pool.
This activity record represents a memory pool creation, destruction and trimming (CUPTI_ACTIVITY_KIND_MEMORY_POOL). This activity record provides separate records for memory pool creation, destruction and trimming operations. This allows to correlate the corresponding driver and runtime API activity record with the memory pool operation.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_MEMORY_POOL.

CUpti_ActivityMemoryPoolOperationType memoryPoolOperationType
The memory operation requested by the user, CUpti_ActivityMemoryPoolOperationType.

CUpti_ActivityMemoryPoolType memoryPoolType
The type of the memory pool, CUpti_ActivityMemoryPoolType.

uint32_t correlationId
The correlation ID of the memory pool operation.
Each memory pool operation is assigned a unique correlation ID that is identical to the correlation ID in the driver and runtime API activity record that launched the memory operation.

uint32_t processId
The ID of the process to which this record belongs to.

uint32_t deviceId
The ID of the device where the memory pool is created.

size_t minBytesToKeep
The minimum bytes to keep of the memory pool.
minBytesToKeep is valid for CUPTI_ACTIVITY_MEMORY_POOL_OPERATION_TYPE_TRIMMED, CUpti_ActivityMemoryPoolOperationType

uint64_t address
The virtual address of the allocation.

uint64_t size
The size of the memory pool operation in bytes.
size is valid for CUPTI_ACTIVITY_MEMORY_POOL_TYPE_LOCAL, CUpti_ActivityMemoryPoolType.

uint64_t releaseThreshold
The release threshold of the memory pool.
releaseThreshold is valid for CUPTI_ACTIVITY_MEMORY_POOL_TYPE_LOCAL, CUpti_ActivityMemoryPoolType.

uint64_t timestamp
The start timestamp for the memory operation, in ns.

uint64_t utilizedSize
The utilized size of the memory pool.
utilizedSize is valid for CUPTI_ACTIVITY_MEMORY_POOL_TYPE_LOCAL, CUpti_ActivityMemoryPoolType.