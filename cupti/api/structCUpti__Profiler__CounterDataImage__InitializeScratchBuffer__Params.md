# 7.147. CUpti_Profiler_CounterDataImage_InitializeScratchBuffer_Params


struct CUpti_Profiler_CounterDataImage_InitializeScratchBuffer_Params
Params for cuptiProfilerCounterDataImageInitializeScratchBuffer.

Public Members

size_t structSize
[in] CUpti_Profiler_CounterDataImage_InitializeScratchBuffer_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

size_t counterDataImageSize
[in] size calculated from cuptiProfilerCounterDataImageCalculateSize

uint8_t *pCounterDataImage
[in]

size_t counterDataScratchBufferSize
[in] size calculated using cuptiProfilerCounterDataImageCalculateScratchBufferSize

uint8_t *pCounterDataScratchBuffer
[in] the scratch buffer to be initialized.