# 7.67. CUpti_ActivityMemory


struct CUpti_ActivityMemory
The activity record for memory.
This activity record represents a memory allocation and free operation (CUPTI_ACTIVITY_KIND_MEMORY). This activity record provides a single record for the memory allocation and memory release operations.
Note: It is recommended to move to the new activity record CUpti_ActivityMemory4 enabled using the kind CUPTI_ACTIVITY_KIND_MEMORY2. CUpti_ActivityMemory4 provides separate records for memory allocation and memory release operations. This allows to correlate the corresponding driver and runtime API activity record with the memory operation.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_MEMORY.

CUpti_ActivityMemoryKind memoryKind
The memory kind requested by the user.

uint64_t address
The virtual address of the allocation.

uint64_t bytes
The number of bytes of memory allocated.

uint64_t start
The start timestamp for the memory operation, i.e.
the time when memory was allocated, in ns.

uint64_t end
The end timestamp for the memory operation, i.e.
the time when memory was freed, in ns. This will be 0 if memory is not freed in the application

uint64_t allocPC
The program counter of the allocation of memory.

uint64_t freePC
The program counter of the freeing of memory.
This will be 0 if memory is not freed in the application

uint32_t processId
The ID of the process to which this record belongs to.

uint32_t deviceId
The ID of the device where the memory allocation is taking place.

uint32_t contextId
The ID of the context.
If context is NULL, contextId is set to CUPTI_INVALID_CONTEXT_ID.

uint32_t pad
Undefined.
Reserved for internal use.

const char *name
Variable name.
This name is shared across all activity records representing the same symbol, and so should not be modified.