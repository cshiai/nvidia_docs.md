# 7.56. CUpti_ActivityMarkerData2


struct CUpti_ActivityMarkerData2
The activity record providing detailed information for a marker.
User must enable CUPTI_ACTIVITY_KIND_MARKER as well to get records for marker data. The marker data contains color, payload, and category. (CUPTI_ACTIVITY_KIND_MARKER_DATA).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_MARKER_DATA.

CUpti_ActivityFlag flags
The flags associated with the marker.

See also
CUpti_ActivityFlag

uint32_t id
The marker ID.

CUpti_MetricValueKind payloadKind
Defines the payload format for the value associated with the marker.

CUpti_MetricValue payload
The payload value.

uint32_t color
The color for the marker.

uint32_t category
The category for the marker.

uint32_t cuptiDomainId
CUPTI maintained domain id required for NVTX extended payloads.
To parse the payload correctly, the domain id must be used to identify the payload attributes as they are domain specific.

uint32_t padding
Reserved for internal use.