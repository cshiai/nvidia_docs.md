# 7.136. CUpti_PmSampling_GetCounterAvailability_Params


struct CUpti_PmSampling_GetCounterAvailability_Params
Params for cuptiPmSamplingGetCounterData.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

size_t deviceIndex
[in] Device index.

size_t counterAvailabilityImageSize
[inout] Size of the counter availability image. When pCounterAvailabilityImage is NULL, this field is used to return the size of the counter availability image.

uint8_t *pCounterAvailabilityImage
[out] Counter availability image.