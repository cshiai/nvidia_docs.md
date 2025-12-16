# 7.36. CUpti_ActivityInstantaneousMetric


struct CUpti_ActivityInstantaneousMetric
The activity record for an instantaneous CUPTI metric.
This activity record represents the collection of a CUPTI metric value (CUPTI_ACTIVITY_KIND_METRIC) at a particular instance. This activity record kind is not produced by the activity API but is included for completeness and ease-of-use. Profiler frameworks built on top of CUPTI that collect metric data may choose to use this type to store the collected metric data.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_INSTANTANEOUS_METRIC.

CUpti_MetricID id
The metric ID.

CUpti_MetricValue value
The metric value.

uint64_t timestamp
The timestamp at which metric is sampled.

uint32_t deviceId
The device id.

uint8_t flags
The properties of this metric.

See also
CUpti_ActivityFlag

uint8_t pad[3]
Undefined.
reserved for internal use