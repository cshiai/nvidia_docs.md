# 7.78. CUpti_ActivityMetric


struct CUpti_ActivityMetric
The activity record for a CUPTI metric.
This activity record represents the collection of a CUPTI metric value (CUPTI_ACTIVITY_KIND_METRIC). This activity record kind is not produced by the activity API but is included for completeness and ease-of-use. Profile frameworks built on top of CUPTI that collect metric data may choose to use this type to store the collected metric data.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_METRIC.

CUpti_MetricID id
The metric ID.

CUpti_MetricValue value
The metric value.

uint32_t correlationId
The correlation ID of the metric.
Use of this ID is user-defined, but typically this ID value will equal the correlation ID of the kernel for which the metric was gathered.

uint8_t flags
The properties of this metric.

See also
CUpti_ActivityFlag

uint8_t pad[3]
Undefined.
Reserved for internal use.