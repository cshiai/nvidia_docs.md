# 7.57. CUpti_ActivityMemDecompress


struct CUpti_ActivityMemDecompress
The activity record for trace of decompression operations.
This activity record represents execution for a batch of decompression operatios. The activity kind is CUPTI_ACTIVITY_KIND_MEM_DECOMPRESS

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_MEM_DECOMPRESS.

uint32_t deviceId
The ID of the device.

uint32_t contextId
The ID of the context.

uint32_t streamId
The ID of the stream.

uint32_t channelID
The ID of the HW channel on which the memory copy is occurring.

CUpti_ChannelType channelType
The type of the channel.

uint32_t correlationId
The correlation ID of the decompression operations.
Each operation is assigned a unique correlation ID that is identical to the correlation ID in the driver API activity record that launched the operation.

uint32_t numberOfOperations
The number of operations in the batch.

uint64_t sourceBytes
The number of bytes to be read and decompressed in the batch operation.

void *reserved0
This field is reserved for internal use.

uint64_t start
The start timestamp.
A value of CUPTI_TIMESTAMP_UNKNOWN indicates that the start time is unknown.

uint64_t end
The end timestamp.
A value of CUPTI_TIMESTAMP_UNKNOWN indicates that the start time is unknown.