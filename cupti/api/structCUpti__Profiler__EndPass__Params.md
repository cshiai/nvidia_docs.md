# 7.153. CUpti_Profiler_EndPass_Params


struct CUpti_Profiler_EndPass_Params
Params for cuptiProfilerEndPass.

Public Members

size_t structSize
[in] CUpti_Profiler_EndPass_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUcontext ctx
[in] if NULL, the current CUcontext is used

size_t passIndex
[out] The targetNestingLevel that will be collected by the next BeginPass.
[out] The passIndex that will be collected by the next BeginPass

uint8_t allPassesSubmitted
[out] becomes true when the last pass has been queued to the GPU