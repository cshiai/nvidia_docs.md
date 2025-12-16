# 7.181. CUpti_RangeProfiler_GetCounterDataInfo_Params


struct CUpti_RangeProfiler_GetCounterDataInfo_Params
Params for cuptiRangeProfilerGetCounterDataInfo.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

const uint8_t *pCounterDataImage
[in] Counter data image.

size_t counterDataImageSize
[in] Size of the counter data image.

size_t numTotalRanges
[out] Number of ranges in the counter data image.