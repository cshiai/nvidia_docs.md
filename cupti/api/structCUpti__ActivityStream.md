# 7.105. CUpti_ActivityStream


struct CUpti_ActivityStream
The activity record for CUDA stream.
This activity is used to track created streams. (CUPTI_ACTIVITY_KIND_STREAM).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_STREAM.

uint32_t contextId
The ID of the context where the stream was created.

uint32_t streamId
A unique stream ID to identify the stream.

uint32_t priority
The clamped priority for the stream.

CUpti_ActivityStreamFlag flag
Flags associated with the stream.

uint32_t correlationId
The correlation ID of the API to which this result is associated.