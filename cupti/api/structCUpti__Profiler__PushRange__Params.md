# 7.173. CUpti_Profiler_PushRange_Params


struct CUpti_Profiler_PushRange_Params
Public Members

size_t structSize
[in] CUpti_Profiler_PushRange_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUcontext ctx
[in] if NULL, the current CUcontext is used

const char *pRangeName
[in] specifies the range for subsequent launches; must not be NULL

size_t rangeNameLength
[in] assign to strlen(pRangeName) if known; if set to zero, the library will call strlen()