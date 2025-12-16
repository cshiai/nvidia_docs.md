# 7.174. CUpti_Profiler_SetConfig_Params


struct CUpti_Profiler_SetConfig_Params
Params for cuptiProfilerSetConfig.

Public Members

size_t structSize
[in] CUpti_Profiler_SetConfig_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUcontext ctx
[in] if NULL, the current CUcontext is used

const uint8_t *pConfig
[in] Config created by NVPW_RawMetricsConfig_GetConfigImage(). Must be align(8).

size_t configSize
[in] size of config

uint16_t minNestingLevel
[in] the lowest nesting level to be profiled; must be >= 1

uint16_t numNestingLevels
[in] the number of nesting levels to profile; must be >= 1

size_t passIndex
[in] Set this to zero for in-app replay; set this to the output of EndPass() for application replay

uint16_t targetNestingLevel
[in] Set this to minNestingLevel for in-app replay; set this to the output of EndPass() for application