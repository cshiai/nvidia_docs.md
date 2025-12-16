# 7.197. CUpti_SassMetrics_GetMetrics_Params


struct CUpti_SassMetrics_GetMetrics_Params
Params for cuptiSassMetricsGetMetrics.

Public Members

size_t structSize
[in] should be equal to CUpti_SassMetrics_GetMetrics_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

const char *pChipName
[in] chip name for which metrics will be queried

size_t numOfMetrics
[in] number of metrics supported for the queried chip (can be queried using cuptiSassMetricsGetNumOfMetrics())

CUpti_SassMetrics_MetricDetails *pMetricsList
[out] list of metrics supported for queried chip