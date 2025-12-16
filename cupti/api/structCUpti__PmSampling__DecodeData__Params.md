# 7.133. CUpti_PmSampling_DecodeData_Params


struct CUpti_PmSampling_DecodeData_Params
Params for cuptiPmSamplingDecodeData.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

CUpti_PmSampling_Object *pPmSamplingObject
[in] PM sampling object.

uint8_t *pCounterDataImage
[in] Counter data image.

size_t counterDataImageSize
[in] Size of the counter data image.

CUpti_PmSampling_DecodeStopReason decodeStopReason
[out] decode stop reason

uint8_t overflow
[out] overflow status for hardware buffer. To avoid overflow, either increase the maxSamples values in CUpti_PmSampling_SetConfig_Params or reduce the sampling interval.