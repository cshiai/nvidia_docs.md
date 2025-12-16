# 7.139. CUpti_PmSampling_SetConfig_Params


struct CUpti_PmSampling_SetConfig_Params
Params for cuptiPmSamplingSetConfig.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

CUpti_PmSampling_Object *pPmSamplingObject
[in] PM sampling object.

size_t configSize
[in] Size of the config image.

const uint8_t *pConfig
[in] Config image.

size_t hardwareBufferSize
[in] The hardware buffer size in which raw PM sampling data will be stored. These samples will be decoded to counter data image with cuptiPmSamplingDecodeData call.

uint64_t samplingInterval
[in] For the trigger mode CUPTI_PM_SAMPLING_TRIGGER_MODE_GPU_SYSCLK_INTERVAL, sampling interval is the number of sys clock cycles. For the trigger mode CUPTI_PM_SAMPLING_TRIGGER_MODE_GPU_TIME_INTERVAL, sampling interval is in nanoseconds.

CUpti_PmSampling_TriggerMode triggerMode
[in] Trigger mode. Note: CUPTI_PM_SAMPLING_TRIGGER_MODE_GPU_TIME_INTERVAL is not supported in Turing and GA100. Supported from GA10x onwards.

CUpti_PmSampling_HardwareBuffer_AppendMode hwBufferAppendMode
[in] Append mode for the records in hardware buffer. For KEEP_OLDEST mode, all the records will be kept in the buffer and in case hardware buffer is getting filled up. overflow will be set to 1 in CUpti_PmSampling_DecodeData_Params. For KEEP_LATEST mode, the new records will overwrite the oldest records in the buffer in case of filled buffer.