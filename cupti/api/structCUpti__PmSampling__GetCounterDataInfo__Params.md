# 7.137. CUpti_PmSampling_GetCounterDataInfo_Params


struct CUpti_PmSampling_GetCounterDataInfo_Params
Params for cuptiPmSamplingGetCounterDataInfo.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

const uint8_t *pCounterDataImage
[in] Counter data image.

size_t counterDataImageSize
[in] Size of the counter data image.

size_t numTotalSamples
[out] Number of samples in the counter data image.

size_t numPopulatedSamples
[out] Number of populated samples.

size_t numCompletedSamples
[out] Number of samples that have been completed.