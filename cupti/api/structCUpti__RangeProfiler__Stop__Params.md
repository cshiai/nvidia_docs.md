# 7.187. CUpti_RangeProfiler_Stop_Params


struct CUpti_RangeProfiler_Stop_Params
Params for cuptiRangeProfilerStop.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object *pRangeProfilerObject
[in] Range Profiler Object.

size_t passIndex
[out] pass index for the replay session.

size_t targetNestingLevel
[out] target nesting level for the replay session.

uint8_t isAllPassSubmitted
[out] 1 if all passes are submitted to GPU for collection, 0 otherwise.