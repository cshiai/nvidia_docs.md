# 7.55. CUpti_ActivityMarkerData


struct CUpti_ActivityMarkerData
The activity record providing detailed information for a marker.
User must enable CUPTI_ACTIVITY_KIND_MARKER as well to get records for marker data. The marker data contains color, payload, and category. (CUPTI_ACTIVITY_KIND_MARKER_DATA).
Structure deprecated in CUDA 13.1: Refer to CUpti_ActivityMarkerData2 for the latest structure.

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