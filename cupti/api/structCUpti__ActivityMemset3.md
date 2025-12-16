# 7.76. CUpti_ActivityMemset3


struct CUpti_ActivityMemset3
The activity record for memset.
(deprecated in CUDA 11.6)
This activity record represents a memory set operation (CUPTI_ACTIVITY_KIND_MEMSET).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_MEMSET.

uint32_t value
The value being assigned to memory by the memory set.

uint64_t bytes
The number of bytes being set by the memory set.

uint64_t start
The start timestamp for the memory set, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the memory set.

uint64_t end
The end timestamp for the memory set, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the memory set.

uint32_t deviceId
The ID of the device where the memory set is occurring.

uint32_t contextId
The ID of the context where the memory set is occurring.

uint32_t streamId
The ID of the stream where the memory set is occurring.

uint32_t correlationId
The correlation ID of the memory set.
Each memory set is assigned a unique correlation ID that is identical to the correlation ID in the driver API activity record that launched the memory set.

uint16_t flags
The flags associated with the memset.

See also
CUpti_ActivityFlag

uint16_t memoryKind
The memory kind of the memory set.

See also
CUpti_ActivityMemoryKind

uint32_t pad
Undefined.
Reserved for internal use.

void *reserved0
Undefined.
Reserved for internal use.

uint64_t graphNodeId
The unique ID of the graph node that executed this memset through graph launch.
This field will be 0 if the memset is not executed through graph launch.

uint32_t graphId
The unique ID of the graph that executed this memset through graph launch.
This field will be 0 if the memset is not executed through graph launch.

uint32_t padding
Undefined.
Reserved for internal use.