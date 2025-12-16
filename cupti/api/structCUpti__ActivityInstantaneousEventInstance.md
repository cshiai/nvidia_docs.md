# 7.35. CUpti_ActivityInstantaneousEventInstance


struct CUpti_ActivityInstantaneousEventInstance
The activity record for an instantaneous CUPTI event with event domain instance information.
This activity record represents the a CUPTI event value for a specific event domain instance (CUPTI_ACTIVITY_KIND_EVENT_INSTANCE) sampled at a particular instant. This activity record kind is not produced by the activity API but is included for completeness and ease-of-use. Profiler frameworks built on top of CUPTI that collect event data may choose to use this type to store the collected event data. This activity record should be used when event domain instance information needs to be associated with the event.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_INSTANTANEOUS_EVENT_INSTANCE.

CUpti_EventID id
The event ID.

uint64_t value
The event value.

uint64_t timestamp
The timestamp at which event is sampled.

uint32_t deviceId
The device id.

uint8_t instance
The event domain instance.

uint8_t pad[3]
Undefined.
reserved for internal use