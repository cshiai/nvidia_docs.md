# 7.168. CUpti_Profiler_Host_GetSupportedChips_Params


struct CUpti_Profiler_Host_GetSupportedChips_Params
Params for cuptiProfilerHostGetSupportedChips.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Assign to NULL

size_t numChips
[out] number of supported chips

const char *const *ppChipNames
[out] list of supported chips