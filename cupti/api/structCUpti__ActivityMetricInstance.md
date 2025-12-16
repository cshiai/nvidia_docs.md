# 7.79. CUpti_ActivityMetricInstance


struct CUpti_ActivityMetricInstance
The activity record for a CUPTI metric with instance information.
This activity record represents a CUPTI metric value for a specific metric domain instance (CUPTI_ACTIVITY_KIND_METRIC_INSTANCE). This activity record kind is not produced by the activity API but is included for completeness and ease-of-use. Profile frameworks built on top of CUPTI that collect metric data may choose to use this type to store the collected metric data. This activity record should be used when metric domain instance information needs to be associated with the metric.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_METRIC_INSTANCE.

CUpti_MetricID id
The metric ID.

CUpti_MetricValue value
The metric value.

uint32_t instance
The metric domain instance.

uint32_t correlationId
The correlation ID of the metric.
Use of this ID is user-defined, but typically this ID value will equal the correlation ID of the kernel for which the metric was gathered.

uint8_t flags
The properties of this metric.

See also
CUpti_ActivityFlag

uint8_t pad[7]
Undefined.
Reserved for internal use.