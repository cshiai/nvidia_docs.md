# 7.161. CUpti_Profiler_Host_GetConfigImageSize_Params


struct CUpti_Profiler_Host_GetConfigImageSize_Params
Params for cuptiProfilerHostGetConfigImageSize.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Assign to NULL

CUpti_Profiler_Host_Object *pHostObject
[in] reference to the profiler host object allocated by CUPTI in cuptiProfilerHostInitialize

size_t configImageSize
[out] the size of config image, users need to allocate the buffer for storing