# 7.53. CUpti_ActivityMarker


struct CUpti_ActivityMarker
The activity record providing a marker which is an instantaneous point in time.
(deprecated in CUDA 8.0)
The marker is specified with a descriptive name and unique id (CUPTI_ACTIVITY_KIND_MARKER). Marker activity is now reported using the CUpti_ActivityMarker2 activity record.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_MARKER.

CUpti_ActivityFlag flags
The flags associated with the marker.

See also
CUpti_ActivityFlag

uint64_t timestamp
The timestamp for the marker, in ns.
A value of 0 indicates that timestamp information could not be collected for the marker.

uint32_t id
The marker ID.

CUpti_ActivityObjectKind objectKind
The kind of activity object associated with this marker.

CUpti_ActivityObjectKindId objectId
The identifier for the activity object associated with this marker.
‘objectKind’ indicates which ID is valid for this record.

uint32_t pad
Undefined.
Reserved for internal use.

const char *name
The marker name for an instantaneous or start marker.
This will be NULL for an end marker.