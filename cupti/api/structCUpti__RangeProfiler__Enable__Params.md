# 7.180. CUpti_RangeProfiler_Enable_Params


struct CUpti_RangeProfiler_Enable_Params
Params for cuptiRangeProfilerEnable.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

CUcontext ctx
[in] Context to be used for profiling.

CUpti_RangeProfiler_Object *pRangeProfilerObject
[out] Range Profiler Object.