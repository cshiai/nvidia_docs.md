# 7.81. CUpti_ActivityName


struct CUpti_ActivityName
The activity record providing a name.
This activity record provides a name for a device, context, thread, etc. and other resource naming done via NVTX APIs (CUPTI_ACTIVITY_KIND_NAME).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_NAME.

CUpti_ActivityObjectKind objectKind
The kind of activity object being named.

CUpti_ActivityObjectKindId objectId
The identifier for the activity object.
‘objectKind’ indicates which ID is valid for this record.

uint32_t pad
Undefined.
Reserved for internal use.

const char *name
The name.