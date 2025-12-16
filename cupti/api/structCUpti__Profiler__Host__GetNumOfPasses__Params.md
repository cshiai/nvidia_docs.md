# 7.165. CUpti_Profiler_Host_GetNumOfPasses_Params


struct CUpti_Profiler_Host_GetNumOfPasses_Params
Params for cuptiProfilerHostGetNumOfPasses.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Assign to NULL

size_t configImageSize
[in] Number of bytes allocated for pConfigImage

uint8_t *pConfigImage
[in] the config image buffer

size_t numOfPasses
[out] number of passes required for profiling scheduled metrics in the config image