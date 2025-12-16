# 7.9. CUpti_ActivityContext


struct CUpti_ActivityContext
The activity record for a context.
This activity record represents information about a context (CUPTI_ACTIVITY_KIND_CONTEXT). Context activity is now reported using CUpti_ActivityContext3 record

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_CONTEXT.

uint32_t contextId
The context ID.

uint32_t deviceId
The device ID.

uint16_t computeApiKind
The compute API kind.

See also
CUpti_ActivityComputeApiKind

uint16_t nullStreamId
The ID for the NULL stream in this context.