# 7.33. CUpti_ActivityHostLaunch


struct CUpti_ActivityHostLaunch
The activity record for host launch functions.
The corresponding activity kind is CUPTI_ACTIVITY_KIND_HOST_LAUNCH.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_HOST_LAUNCH.

uint32_t streamId
The ID of the CUDA context to which the waiting CUDA stream belongs.

uint32_t contextId
The ID of the CUDA context to which the waiting CUDA stream belongs.

uint32_t deviceId
The ID of the CUDA device to which the CUDA context and stream belong.
The host function is executing on the CPU, but it is associated with the CUDA device through the CUDA context and stream.

uint32_t correlationId
The correlation ID of the host launch operation.
Each operation is assigned a unique correlation ID that is identical to the correlation ID in the driver API activity record that launched the operation.

uint32_t processId
The ID of the process where the host function is executing.

uint32_t threadId
The ID of the thread where the host function is executing.

uint64_t start
The start timestamp.
A value of CUPTI_TIMESTAMP_UNKNOWN indicates that the start time is unknown.

uint64_t end
The end timestamp.
A value of CUPTI_TIMESTAMP_UNKNOWN indicates that the start time is unknown.