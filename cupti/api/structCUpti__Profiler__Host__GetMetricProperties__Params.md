# 7.164. CUpti_Profiler_Host_GetMetricProperties_Params


struct CUpti_Profiler_Host_GetMetricProperties_Params
Params for cuptiProfilerHostGetMetricProperties.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Assign to NULL

CUpti_Profiler_Host_Object *pHostObject
[in] reference to the profiler host object allocated by CUPTI in cuptiProfilerHostInitialize

const char *pMetricName
[in] metric name for which its properties will be listed. Metric name can be with or without extension (rollup or submetric)

const char *pDescription
[out] a short description about the metric

const char *pHwUnit
[out] associated hw unit for the metric

const char *pDimUnit
[out] the dimension of the metric values

CUpti_MetricType metricType
[out] the metric type (counter, ratio or throughput)

CUpti_MetricCollectionScope metricCollectionScope
[out] the metric collection scope (context, device)