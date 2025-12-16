# 7.24. CUpti_ActivityEventInstance


struct CUpti_ActivityEventInstance
The activity record for a CUPTI event with instance information.
This activity record represents the a CUPTI event value for a specific event domain instance (CUPTI_ACTIVITY_KIND_EVENT_INSTANCE). This activity record kind is not produced by the activity API but is included for completeness and ease-of-use. Profile frameworks built on top of CUPTI that collect event data may choose to use this type to store the collected event data. This activity record should be used when event domain instance information needs to be associated with the event.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_EVENT_INSTANCE.

CUpti_EventID id
The event ID.

CUpti_EventDomainID domain
The event domain ID.

uint32_t instance
The event domain instance.

uint64_t value
The event value.

uint32_t correlationId
The correlation ID of the event.
Use of this ID is user-defined, but typically this ID value will equal the correlation ID of the kernel for which the event was gathered.

uint32_t pad
Undefined.
Reserved for internal use.