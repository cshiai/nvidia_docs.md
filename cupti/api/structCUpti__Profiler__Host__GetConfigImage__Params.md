# 7.162. CUpti_Profiler_Host_GetConfigImage_Params


struct CUpti_Profiler_Host_GetConfigImage_Params
Params for cuptiProfilerHostGetConfigImage.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Assign to NULL

CUpti_Profiler_Host_Object *pHostObject
[in] reference to the profiler host object allocated by CUPTI in cuptiProfilerHostInitialize

size_t configImageSize
[in] Number of bytes allocated for pBuffer

uint8_t *pConfigImage
[out] Buffer receiving the config image