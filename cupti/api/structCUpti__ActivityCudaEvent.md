# 7.13. CUpti_ActivityCudaEvent


struct CUpti_ActivityCudaEvent
The activity record for CUDA event.
This activity is used to track recorded events. (CUPTI_ACTIVITY_KIND_CUDA_EVENT).
Structure deprecated in CUDA 12.8: Refer to CUpti_ActivityCudaEvent2 for the latest structure.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_CUDA_EVENT.

uint32_t correlationId
The correlation ID of the API to which this result is associated.

uint32_t contextId
The ID of the context where the event was recorded.

uint32_t streamId
The compute stream where the event was recorded.

uint32_t eventId
A unique event ID to identify the event record.

uint32_t pad
Undefined.
Reserved for internal use.