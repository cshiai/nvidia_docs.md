# 7.178. CUpti_RangeProfiler_DecodeData_Params


struct CUpti_RangeProfiler_DecodeData_Params
Params for cuptiRangeProfilerDecodeData.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object *pRangeProfilerObject
[in] Range Profiler Object.

size_t numOfRangeDropped
[out] Number of ranges dropped in the processed passes.