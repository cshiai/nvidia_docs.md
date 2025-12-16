# 7.199. CUpti_SassMetrics_GetProperties_Params


struct CUpti_SassMetrics_GetProperties_Params
Params for cuptiSassMetricsGetProperties.

Public Members

size_t structSize
[in] should be equal to CUpti_SassMetrics_GetProperties_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

const char *pChipName
[in] chip name for which metric will be queried

const char *pMetricName
[in] metric name

CUpti_SassMetrics_MetricDetails metric
[out] returns the metric ID and the metric description