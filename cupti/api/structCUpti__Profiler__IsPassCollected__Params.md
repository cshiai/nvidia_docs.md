# 7.171. CUpti_Profiler_IsPassCollected_Params


struct CUpti_Profiler_IsPassCollected_Params
Params for cuptiProfilerIsPassCollected.

Public Members

size_t structSize
[in] CUpti_Profiler_IsPassCollected_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUcontext ctx
[in] if NULL, the current CUcontext is used

size_t numRangesDropped
[out] number of ranges whose data was dropped in the processed pass

size_t numTraceBytesDropped
[out] number of bytes not written to TraceBuffer due to buffer full

uint8_t onePassCollected
[out] true if a pass was successfully decoded

uint8_t allPassesCollected
[out] becomes true when the last pass has been decoded