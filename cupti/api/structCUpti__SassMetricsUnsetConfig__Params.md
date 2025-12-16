# 7.194. CUpti_SassMetricsUnsetConfig_Params


struct CUpti_SassMetricsUnsetConfig_Params
Params for cuptiSassMetricsUnsetConfig.

Public Members

size_t structSize
[in] equal to CUpti_SassMetricsUnsetConfig_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

uint32_t deviceIndex
[in] device index for which SASS metric data collection config will get reset, user need to call this API for all the devices on which the the SASS metric data collection have been configured.