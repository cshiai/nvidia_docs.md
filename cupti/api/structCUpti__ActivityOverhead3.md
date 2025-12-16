# 7.94. CUpti_ActivityOverhead3


struct CUpti_ActivityOverhead3
The activity record for CUPTI and driver overheads.
This activity record provides CUPTI and driver overhead information (CUPTI_ACTIVITY_KIND_OVERHEAD).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_OVERHEAD.

CUpti_ActivityOverheadKind overheadKind
The kind of overhead, CUPTI, DRIVER, COMPILER etc.

CUpti_ActivityObjectKind objectKind
The kind of activity object that the overhead is associated with.

CUpti_ActivityObjectKindId objectId
The identifier for the activity object.
‘objectKind’ indicates which ID is valid for this record.

uint64_t start
The start timestamp for the overhead, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the overhead.

uint64_t end
The end timestamp for the overhead, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the overhead.

uint32_t correlationId
The correlation ID of the overhead operation to which records belong to.
This ID is identical to the correlation ID in the driver or runtime API activity record that launched the overhead operation. In some cases, it can be zero, such as for CUPTI_ACTIVITY_OVERHEAD_CUPTI_BUFFER_FLUSH records.

uint32_t reserved0
Reserved for internal use.

void *overheadData
Pointer to the struct with additional details about the overhead.
Refer CUpti_ActivityOverheadKind enum and the corresponding structure to typecast and access additional overhead data. Client is responsible for freeing this memory using the free function when done.