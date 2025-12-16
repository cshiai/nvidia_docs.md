# 7.34. CUpti_ActivityInstantaneousEvent


struct CUpti_ActivityInstantaneousEvent
The activity record for an instantaneous CUPTI event.
This activity record represents a CUPTI event value (CUPTI_ACTIVITY_KIND_EVENT) sampled at a particular instant. This activity record kind is not produced by the activity API but is included for completeness and ease-of-use. Profiler frameworks built on top of CUPTI that collect event data at a particular time may choose to use this type to store the collected event data.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_INSTANTANEOUS_EVENT.

CUpti_EventID id
The event ID.

uint64_t value
The event value.

uint64_t timestamp
The timestamp at which event is sampled.

uint32_t deviceId
The device id.

uint32_t reserved
Undefined.
reserved for internal use