# 7.167. CUpti_Profiler_Host_GetSubMetrics_Params


struct CUpti_Profiler_Host_GetSubMetrics_Params
Params for cuptiProfilerHostGetSubMetrics.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Assign to NULL

CUpti_Profiler_Host_Object *pHostObject
[in] reference to the profiler host object allocated by CUPTI in cuptiProfilerHostInitialize

CUpti_MetricType metricType
[in] the metric type for queried metric

const char *pMetricName
[in] metric name for which sub-metric will be listed. Metric name can be with or without extension (rollup or submetric)

size_t numOfSubmetrics
[out] number of submetrics supported

const char ppSubMetrics
[out] list of submetrics supported for the metric.