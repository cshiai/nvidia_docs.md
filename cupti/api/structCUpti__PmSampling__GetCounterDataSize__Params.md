# 7.138. CUpti_PmSampling_GetCounterDataSize_Params


struct CUpti_PmSampling_GetCounterDataSize_Params
Params for cuptiPmSamplingGetCounterDataSize.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

CUpti_PmSampling_Object *pPmSamplingObject
[in] PM sampling object.

const char pMetricNames
[in] Names of the metrics to be collected.

size_t numMetrics
[in] Number of metrics to be collected.

uint32_t maxSamples
[in] Maximum number of samples to be stored in the counter data image.

size_t counterDataSize
[out] Size of the counter data image.