# 7.193. CUpti_SassMetricsSetConfig_Params


struct CUpti_SassMetricsSetConfig_Params
Params for cuptiSassMetricsSetConfig.

Public Members

size_t structSize
[in] equal to CUpti_SassMetricsSetConfig_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

size_t numOfMetricConfig
[in] num of metric configs, will be equal to number of metrics queried

CUpti_SassMetrics_Config *pConfigs
[in] list of metric config generated for given sass metrics

uint32_t deviceIndex
[in] device index for which config will be set, user can call this once for the device on which the the SASS metric data will be collected