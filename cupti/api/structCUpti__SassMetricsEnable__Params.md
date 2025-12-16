# 7.190. CUpti_SassMetricsEnable_Params


struct CUpti_SassMetricsEnable_Params
Params for cuptiSassMetricsEnable.

Public Members

size_t structSize
[in] equal to CUpti_SassMetricsEnable_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUcontext ctx
[in] CUDA context on which SASS metric data collection will be enabled. If set NULL, default context will be consider for SASS metric data collection.

uint8_t enableLazyPatching
[in] if false, all the functions will patched regardless of their execution with cuptiSassMetricsEnable() API call. when this parameter is set to true, metric data collection for the function will be done at the very first execution in the enable/disble range.