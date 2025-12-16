# 7.154. CUpti_Profiler_EndSession_Params


struct CUpti_Profiler_EndSession_Params
Params for cuptiProfilerEndSession.

Public Members

size_t structSize
[in] CUpti_Profiler_EndSession_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUcontext ctx
[in] if NULL, the current CUcontext is used