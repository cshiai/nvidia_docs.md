# 7.166. CUpti_Profiler_Host_GetRangeName_Params


struct CUpti_Profiler_Host_GetRangeName_Params
Params for cuptiProfilerHostGetRangeName.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Assign to NULL

const uint8_t *pCounterDataImage
[in] the counter data image where profiling data has been decoded

size_t counterDataImageSize
[in] size of counter data image

size_t rangeIndex
[in] range index for which the range name will be queried

const char *delimiter
[in] used in case of nested ranges, default=”/”. Range1<delimiter>Range2

const char *pRangeName
[out] the range name. Note: that the CUPTI allocate the memory internal and its user responsibility to free up the allocated memory