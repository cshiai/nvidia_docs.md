# 7.106. CUpti_ActivitySynchronization


struct CUpti_ActivitySynchronization
The activity record for synchronization management.
This activity is used to track various CUDA synchronization APIs. (CUPTI_ACTIVITY_KIND_SYNCHRONIZATION).
Structure deprecated in CUDA 12.8: Refer to CUpti_ActivitySynchronization2 for the latest structure.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_SYNCHRONIZATION.

CUpti_ActivitySynchronizationType type
The type of record.

uint64_t start
The start timestamp for the function, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the function.

uint64_t end
The end timestamp for the function, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the function.

uint32_t correlationId
The correlation ID of the API to which this result is associated.

uint32_t contextId
The ID of the context for which the synchronization API is called.
In case of context synchronization API it is the context id for which the API is called. In case of stream/event synchronization it is the ID of the context where the stream/event was created.

uint32_t streamId
The compute stream for which the synchronization API is called.
A CUPTI_SYNCHRONIZATION_INVALID_VALUE value indicate the field is not applicable for this record. Not valid for cuCtxSynchronize, cuEventSynchronize.

uint32_t cudaEventId
The event ID for which the synchronization API is called.
A CUPTI_SYNCHRONIZATION_INVALID_VALUE value indicate the field is not applicable for this record. Not valid for cuCtxSynchronize, cuStreamSynchronize.