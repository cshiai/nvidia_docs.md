# 7.160. CUpti_Profiler_Host_GetBaseMetrics_Params


struct CUpti_Profiler_Host_GetBaseMetrics_Params
Params for cuptiProfilerHostGetSupportedMetrics.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Assign to NULL

struct CUpti_Profiler_Host_Object *pHostObject
[in] reference to the profiler host object allocated by CUPTI in cuptiProfilerHostInitialize

CUpti_MetricType metricType
[in] metric type (counter, ratio, throughput)

const char ppMetricNames
[out] list of base metrics supported of queried metric type for the chip

size_t numMetrics
[out] number of metrics