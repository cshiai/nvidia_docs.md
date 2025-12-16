# 7.11. CUpti_ActivityContext3


struct CUpti_ActivityContext3
The activity record for a context.
This activity record represents information about a context (CUPTI_ACTIVITY_KIND_CONTEXT).

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

uint32_t parentContextId
The ID of the parent context.
It would be 0 if context does not have parent

uint8_t isGreenContext
This field indicates whether the context is a green context.

uint16_t numMultiprocessors
Number of multiprocessors assigned to the green context Invalid if the field ‘isGreenContext’ is 0.

CUpti_ContextCigMode cigMode
This field indicates the CIG mode.