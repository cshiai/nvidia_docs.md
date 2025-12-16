# 7.177. CUpti_RangeProfiler_CounterData_GetRangeInfo_Params


struct CUpti_RangeProfiler_CounterData_GetRangeInfo_Params
Params for cuptiRangeProfilerCounterDataGetRangeInfo.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

const uint8_t *pCounterDataImage
[in] Counter data image.

size_t counterDataImageSize
[in] Size of the counter data image.

size_t rangeIndex
[in] Index of the sample.

const char *rangeDelimiter
[in] range delimiter.

const char *rangeName
[out] RangeName;