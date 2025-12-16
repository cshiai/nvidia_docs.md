# 7.37. CUpti_ActivityInstantaneousMetricInstance


struct CUpti_ActivityInstantaneousMetricInstance
The instantaneous activity record for a CUPTI metric with instance information.
This activity record represents a CUPTI metric value for a specific metric domain instance (CUPTI_ACTIVITY_KIND_METRIC_INSTANCE) sampled at a particular time. This activity record kind is not produced by the activity API but is included for completeness and ease-of-use. Profiler frameworks built on top of CUPTI that collect metric data may choose to use this type to store the collected metric data. This activity record should be used when metric domain instance information needs to be associated with the metric.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_INSTANTANEOUS_METRIC_INSTANCE.

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

uint8_t instance
The metric domain instance.

uint8_t pad[2]
Undefined.
reserved for internal use