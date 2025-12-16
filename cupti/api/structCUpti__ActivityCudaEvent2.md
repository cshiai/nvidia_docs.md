# 7.14. CUpti_ActivityCudaEvent2


struct CUpti_ActivityCudaEvent2
The activity record for CUDA event.
This activity is used to track recorded events. (CUPTI_ACTIVITY_KIND_CUDA_EVENT).

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

uint32_t deviceId
The ID of the device where the event was recorded.

uint32_t pad2
Undefined.
Reserved for internal use.

void *reserved0
Undefined.
Reserved for internal use.

uint64_t deviceTimestamp
The device-side timestamp on CUDA event record.
Timestamp is in nanoseconds. Collection of this field is disabled by default. It can be enabled by calling CUPTI API cuptiActivityEnableCudaEventDeviceTimestamps

uint64_t cudaEventSyncId
A unique ID to associate event synchronization records with the latest CUDA Event record.
Similar field is added in CUpti_ActivitySynchronization2 to associate CUDA Event record to the synchronization record.
The same CUDA event can be used multiple times, so the event id will not be unique to correlate the synchronization record with the latest CUDA Event record. This field will be unique and can be used to do the required correlation.