# 7.148. CUpti_Profiler_CounterDataImage_Initialize_Params


struct CUpti_Profiler_CounterDataImage_Initialize_Params
Params for cuptiProfilerCounterDataImageInitialize.

Public Members

size_t structSize
[in] CUpti_Profiler_CounterDataImage_Initialize_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

size_t sizeofCounterDataImageOptions
[in] CUpti_Profiler_CounterDataImageOptions_STRUCT_SIZE

const CUpti_Profiler_CounterDataImageOptions *pOptions
[in] Pointer to Counter Data Image Options

size_t counterDataImageSize
[in] Size calculated from cuptiProfilerCounterDataImageCalculateSize

uint8_t *pCounterDataImage
[in] The buffer to be initialized.