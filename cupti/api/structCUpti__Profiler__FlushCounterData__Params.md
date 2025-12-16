# 7.155. CUpti_Profiler_FlushCounterData_Params


struct CUpti_Profiler_FlushCounterData_Params
Params for cuptiProfilerFlushCounterData.

Public Members

size_t structSize
[in] CUpti_Profiler_FlushCounterData_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUcontext ctx
[in] if NULL, the current CUcontext is used

size_t numRangesDropped
[out] number of ranges whose data was dropped in the processed passes

size_t numTraceBytesDropped
[out] number of bytes not written to TraceBuffer due to buffer full