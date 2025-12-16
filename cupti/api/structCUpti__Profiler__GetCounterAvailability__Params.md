# 7.156. CUpti_Profiler_GetCounterAvailability_Params


struct CUpti_Profiler_GetCounterAvailability_Params
Params for cuptiProfilerGetCounterAvailability.

Public Members

size_t structSize
[in] CUpti_Profiler_GetCounterAvailability_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUcontext ctx
[in] if NULL, the current CUcontext is used

size_t counterAvailabilityImageSize
[in/out] If pCounterAvailabilityImage is NULL, then the required size is returned in counterAvailabilityImageSize, otherwise counterAvailabilityImageSize should be set to the size of pCounterAvailabilityImage, and on return it would be overwritten with number of actual bytes copied

uint8_t *pCounterAvailabilityImage
[in] buffer receiving counter availability image, may be NULL

bool bAllowDeviceLevelCounters
[in] if true, device level counters are included in the counter availability image