# 7.198. CUpti_SassMetrics_GetNumOfMetrics_Params


struct CUpti_SassMetrics_GetNumOfMetrics_Params
Params for cuptiSassMetricsGetNumOfMetrics.

Public Members

size_t structSize
[in] should be equal to CUpti_SassMetrics_GetNumOfMetrics_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

const char *pChipName
[in] chip name for which metrics will be queried

size_t numOfMetrics
[out] number of metrics supported for the queried chip