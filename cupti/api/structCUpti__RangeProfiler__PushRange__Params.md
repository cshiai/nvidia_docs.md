# 7.184. CUpti_RangeProfiler_PushRange_Params


struct CUpti_RangeProfiler_PushRange_Params
Params for cuptiRangeProfilerPushRange.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object *pRangeProfilerObject
[in] Range Profiler Object.

const char *pRangeName
[in] Name of the range to be profiled (only valid for User range mode).