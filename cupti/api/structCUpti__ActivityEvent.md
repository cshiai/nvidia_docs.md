# 7.23. CUpti_ActivityEvent


struct CUpti_ActivityEvent
The activity record for a CUPTI event.
This activity record represents a CUPTI event value (CUPTI_ACTIVITY_KIND_EVENT). This activity record kind is not produced by the activity API but is included for completeness and ease-of-use. Profile frameworks built on top of CUPTI that collect event data may choose to use this type to store the collected event data.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_EVENT.

CUpti_EventID id
The event ID.

uint64_t value
The event value.

CUpti_EventDomainID domain
The event domain ID.

uint32_t correlationId
The correlation ID of the event.
Use of this ID is user-defined, but typically this ID value will equal the correlation ID of the kernel for which the event was gathered.