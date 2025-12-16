# 7.182. CUpti_RangeProfiler_GetCounterDataSize_Params


struct CUpti_RangeProfiler_GetCounterDataSize_Params
Params for cuptiRangeProfilerGetCounterDataSize.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object *pRangeProfilerObject
[in] Periodic sampler object.

const char pMetricNames
[in] Names of the metrics to be collected.

size_t numMetrics
[in] Number of metrics to be collected.

size_t maxNumOfRanges
[in] Maximum number of ranges to be stored in the counter data image.

uint32_t maxNumRangeTreeNodes
[in] Maximum number of RangeTree nodes; must be >= maxNumOfRanges

size_t counterDataSize
[out] Size of the counter data image.