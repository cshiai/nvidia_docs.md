# 7.64. CUpti_ActivityMemcpyPtoP2


struct CUpti_ActivityMemcpyPtoP2
The activity record for peer-to-peer memory copies.
(deprecated in CUDA 11.1)
This activity record represents a peer-to-peer memory copy (CUPTI_ACTIVITY_KIND_MEMCPY2).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_MEMCPY2.

uint8_t copyKind
The kind of the memory copy, stored as a byte to reduce record size.

See also
CUpti_ActivityMemcpyKind

uint8_t srcKind
The source memory kind read by the memory copy, stored as a byte to reduce record size.

See also
CUpti_ActivityMemoryKind

uint8_t dstKind
The destination memory kind read by the memory copy, stored as a byte to reduce record size.

See also
CUpti_ActivityMemoryKind

uint8_t flags
The flags associated with the memory copy.

See also
CUpti_ActivityFlag

uint64_t bytes
The number of bytes transferred by the memory copy.

uint64_t start
The start timestamp for the memory copy, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the memory copy.

uint64_t end
The end timestamp for the memory copy, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the memory copy.

uint32_t deviceId
The ID of the device where the memory copy is occurring.

uint32_t contextId
The ID of the context where the memory copy is occurring.

uint32_t streamId
The ID of the stream where the memory copy is occurring.

uint32_t srcDeviceId
The ID of the device where memory is being copied from.

uint32_t srcContextId
The ID of the context owning the memory being copied from.

uint32_t dstDeviceId
The ID of the device where memory is being copied to.

uint32_t dstContextId
The ID of the context owning the memory being copied to.

uint32_t correlationId
The correlation ID of the memory copy.
Each memory copy is assigned a unique correlation ID that is identical to the correlation ID in the driver and runtime API activity record that launched the memory copy.

void *reserved0
Undefined.
Reserved for internal use.

uint64_t graphNodeId
The unique ID of the graph node that executed the memcpy through graph launch.
This field will be 0 if memcpy is not done using graph launch.