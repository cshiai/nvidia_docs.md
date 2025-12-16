# 7.132. CUpti_PmSampling_CounterData_GetSampleInfo_Params


struct CUpti_PmSampling_CounterData_GetSampleInfo_Params
Params for cuptiPmSamplingCounterDataGetSampleInfo.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

CUpti_PmSampling_Object *pPmSamplingObject
[in] PM sampling object.

const uint8_t *pCounterDataImage
[in] Counter data image.

size_t counterDataImageSize
[in] Size of the counter data image.

size_t sampleIndex
[in] Index of the sample.

uint64_t startTimestamp
[out] Start time of the sample.

uint64_t endTimestamp
[out] End time of the sample.