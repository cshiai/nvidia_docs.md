# 6.6. CUPTI PM Sampling API


Functions to enable, disable, start, stop, and decode PM sampling.


## 6.6.1. Data Structures


CUpti_PmSampling_CounterDataImage_Initialize_Params
Params for cuptiPmSamplingCounterDataImageInitialize.

CUpti_PmSampling_CounterData_GetSampleInfo_Params
Params for cuptiPmSamplingCounterDataGetSampleInfo.

CUpti_PmSampling_DecodeData_Params
Params for cuptiPmSamplingDecodeData.

CUpti_PmSampling_Disable_Params
Params for cuptiPmSamplingDisable.

CUpti_PmSampling_Enable_Params
Params for cuptiPmSamplingEnable.

CUpti_PmSampling_GetCounterAvailability_Params
Params for cuptiPmSamplingGetCounterData.

CUpti_PmSampling_GetCounterDataInfo_Params
Params for cuptiPmSamplingGetCounterDataInfo.

CUpti_PmSampling_GetCounterDataSize_Params
Params for cuptiPmSamplingGetCounterDataSize.

CUpti_PmSampling_SetConfig_Params
Params for cuptiPmSamplingSetConfig.

CUpti_PmSampling_Start_Params
Params for cuptiPmSamplingStart.

CUpti_PmSampling_Stop_Params
Params for cuptiPmSamplingStop.


## 6.6.2. Macros


CUpti_PmSampling_CounterDataImage_Initialize_Params_STRUCT_SIZECUpti_PmSampling_CounterData_GetSampleInfo_Params_STRUCT_SIZECUpti_PmSampling_DecodeData_Params_STRUCT_SIZECUpti_PmSampling_Disable_Params_STRUCT_SIZECUpti_PmSampling_Enable_Params_STRUCT_SIZECUpti_PmSampling_GetCounterAvailability_Params_STRUCT_SIZECUpti_PmSampling_GetCounterDataInfo_Params_STRUCT_SIZECUpti_PmSampling_GetCounterDataSize_Params_STRUCT_SIZECUpti_PmSampling_SetConfig_Params_STRUCT_SIZECUpti_PmSampling_Start_Params_STRUCT_SIZECUpti_PmSampling_Stop_Params_STRUCT_SIZE

## 6.6.3. Enumerations


CUpti_PmSampling_DecodeStopReasonCUpti_PmSampling_HardwareBuffer_AppendModeCUpti_PmSampling_TriggerMode

## 6.6.4. Functions


CUptiResult cuptiPmSamplingCounterDataGetSampleInfo(CUpti_PmSampling_CounterData_GetSampleInfo_Params *pParams)
Get the sample info (start and end time stamp) for the given sample index.

CUptiResult cuptiPmSamplingCounterDataImageInitialize(CUpti_PmSampling_CounterDataImage_Initialize_Params *pParams)
Initialize the counter data to CUPTI record format for storing the metric data.

CUptiResult cuptiPmSamplingDecodeData(CUpti_PmSampling_DecodeData_Params *pParams)
Decode the metrics data stored in the hardware buffer to the counter data image.

CUptiResult cuptiPmSamplingDisable(CUpti_PmSampling_Disable_Params *pParams)
Disable PM sampling on the CUDA device and destroy the PM sampling object.

CUptiResult cuptiPmSamplingEnable(CUpti_PmSampling_Enable_Params *pParams)
Create a PM sampling object and enable PM sampling on the CUDA device.

CUptiResult cuptiPmSamplingGetCounterAvailability(CUpti_PmSampling_GetCounterAvailability_Params *pParams)
Query counter availibility information in a buffer which can be used to filter unavailable raw metrics on host.

CUptiResult cuptiPmSamplingGetCounterDataInfo(CUpti_PmSampling_GetCounterDataInfo_Params *pParams)
Get the counter data info like number of samples, number of populated samples and number of completed samples in a counter data image.

CUptiResult cuptiPmSamplingGetCounterDataSize(CUpti_PmSampling_GetCounterDataSize_Params *pParams)
Query the size of the counter data image which will be used to store the metrics data.

CUptiResult cuptiPmSamplingSetConfig(CUpti_PmSampling_SetConfig_Params *pParams)
Set the configuration for PM sampling like sampling interval, maximum number of samples filled in HW buffer, trigger mode and the config image which has scheduling info for metric collection.

CUptiResult cuptiPmSamplingStart(CUpti_PmSampling_Start_Params *pParams)
Start the PM sampling.

CUptiResult cuptiPmSamplingStop(CUpti_PmSampling_Stop_Params *pParams)
Stop the PM sampling.


## 6.6.5. Typedefs


CUpti_PmSampling_Object

## 6.6.6. Macros


CUpti_PmSampling_CounterDataImage_Initialize_Params_STRUCT_SIZECUpti_PmSampling_CounterData_GetSampleInfo_Params_STRUCT_SIZECUpti_PmSampling_DecodeData_Params_STRUCT_SIZECUpti_PmSampling_Disable_Params_STRUCT_SIZECUpti_PmSampling_Enable_Params_STRUCT_SIZECUpti_PmSampling_GetCounterAvailability_Params_STRUCT_SIZECUpti_PmSampling_GetCounterDataInfo_Params_STRUCT_SIZECUpti_PmSampling_GetCounterDataSize_Params_STRUCT_SIZECUpti_PmSampling_SetConfig_Params_STRUCT_SIZECUpti_PmSampling_Start_Params_STRUCT_SIZECUpti_PmSampling_Stop_Params_STRUCT_SIZE

## 6.6.7. Enumerations


enum CUpti_PmSampling_DecodeStopReason
Values:

enumerator CUPTI_PM_SAMPLING_DECODE_STOP_REASON_OTHER

enumerator CUPTI_PM_SAMPLING_DECODE_STOP_REASON_COUNTER_DATA_FULL
Counter data image is full.

enumerator CUPTI_PM_SAMPLING_DECODE_STOP_REASON_END_OF_RECORDS
All the records in the hardware buffer is decoded.

enumerator CUPTI_PM_SAMPLING_DECODE_STOP_REASON_COUNT


enum CUpti_PmSampling_HardwareBuffer_AppendMode
Values:

enumerator CUPTI_PM_SAMPLING_HARDWARE_BUFFER_APPEND_MODE_KEEP_OLDEST
Keep the oldest records in the hardware buffer. CUPTI will report error for overflow in case hardware buffer is getting filled up.

enumerator CUPTI_PM_SAMPLING_HARDWARE_BUFFER_APPEND_MODE_KEEP_LATEST
Keep the latest records in the hardware buffer. Note: This mode is not supported on Turing GPU architecture. It is supported on Ampere and later GPU architectures.


enum CUpti_PmSampling_TriggerMode
Values:

enumerator CUPTI_PM_SAMPLING_TRIGGER_MODE_GPU_SYSCLK_INTERVAL
The trigger is based off of the SYSCLK frequency, note SYS frequency by default is variable. the sample interval (set in the struct CUpti_PmSampling_SetConfig_Params) is in terms of clocks.

enumerator CUPTI_PM_SAMPLING_TRIGGER_MODE_GPU_TIME_INTERVAL
The trigger is based off of a fixed frequency source. The sample interval (set in the struct CUpti_PmSampling_SetConfig_Params) is in terms of nanoseconds. Note: This trigger mode is not supported on Turing GPU architecture and GA100 GPU. It is supported on Ampere GA10x and later GPU architectures.

enumerator CUPTI_PM_SAMPLING_TRIGGER_MODE_COUNT


## 6.6.8. Functions


CUptiResult cuptiPmSamplingCounterDataGetSampleInfo(

CUpti_PmSampling_CounterData_GetSampleInfo_Params *pParams,

)
Get the sample info (start and end time stamp) for the given sample index.
Each sample is distinguished by the start and end time stamp.

Parameters:
pParams – A pointer to CUpti_PmSampling_CounterData_GetSampleInfo_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiPmSamplingCounterDataImageInitialize(

CUpti_PmSampling_CounterDataImage_Initialize_Params *pParams,

)
Initialize the counter data to CUPTI record format for storing the metric data.

Parameters:
pParams – A pointer to CUpti_PmSampling_CounterDataImage_Initialize_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_OPERATION – if PM sampling CounterDataInitialize is called without enabling PM sampling
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiPmSamplingDecodeData(

CUpti_PmSampling_DecodeData_Params *pParams,

)
Decode the metrics data stored in the hardware buffer to the counter data image.

Parameters:
pParams – A pointer to CUpti_PmSampling_DecodeData_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_OPERATION – if PM sampling DecodeData is called without enabling PM sampling
CUPTI_ERROR_OUT_OF_MEMORY – if there is record overflow in the hardware buffer
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiPmSamplingDisable(

CUpti_PmSampling_Disable_Params *pParams,

)
Disable PM sampling on the CUDA device and destroy the PM sampling object.

Parameters:
pParams – A pointer to CUpti_PmSampling_Disable_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiPmSamplingEnable(

CUpti_PmSampling_Enable_Params *pParams,

)
Create a PM sampling object and enable PM sampling on the CUDA device.

Parameters:
pParams – A pointer to CUpti_PmSampling_Enable_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_OUT_OF_MEMORY – if memory allocation fails while creating the PM sampling object
CUPTI_ERROR_INVALID_OPERATION – if PM sampling is already enabled on the device
CUPTI_ERROR_INSUFFICIENT_PRIVILEGES – if the user does not have sufficient privileges to perform the operation
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiPmSamplingGetCounterAvailability(

CUpti_PmSampling_GetCounterAvailability_Params *pParams,

)
Query counter availibility information in a buffer which can be used to filter unavailable raw metrics on host.
Note: This API may fail, if any profiling or sampling session is active on the specified device.

Parameters:
pParams – A pointer to CUpti_PmSampling_GetCounterAvailability_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INSUFFICIENT_PRIVILEGES – if the user does not have sufficient privileges to perform the operation
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiPmSamplingGetCounterDataInfo(

CUpti_PmSampling_GetCounterDataInfo_Params *pParams,

)
Get the counter data info like number of samples, number of populated samples and number of completed samples in a counter data image.

Parameters:
pParams – A pointer to CUpti_PmSampling_GetCounterDataInfo_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiPmSamplingGetCounterDataSize(

CUpti_PmSampling_GetCounterDataSize_Params *pParams,

)
Query the size of the counter data image which will be used to store the metrics data.
User need to allocate the memory for the counter data image based on the size returned by this API.

Parameters:
pParams – A pointer to CUpti_PmSampling_GetCounterDataSize_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_OPERATION – if PM sampling GetCounterDataSize is called without enabling PM sampling
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiPmSamplingSetConfig(

CUpti_PmSampling_SetConfig_Params *pParams,

)
Set the configuration for PM sampling like sampling interval, maximum number of samples filled in HW buffer, trigger mode and the config image which has scheduling info for metric collection.

Parameters:
pParams – A pointer to CUpti_PmSampling_SetConfig_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – for config image which require multiple passes for data collection


CUptiResult cuptiPmSamplingStart(

CUpti_PmSampling_Start_Params *pParams,

)
Start the PM sampling.
The GPU will start collecting the metrics data periodically based on trigger type and sampling interval passed in CUpti_PmSampling_SetConfig_Params. The collected data will be stored in the hardware buffer.

Parameters:
pParams – A pointer to CUpti_PmSampling_Start_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_OPERATION – if PM sampling Start is called without enabling PM sampling, and PM sampling is already started
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiPmSamplingStop(

CUpti_PmSampling_Stop_Params *pParams,

)
Stop the PM sampling.
The GPU will stop collecting the metrics data.

Parameters:
pParams – A pointer to CUpti_PmSampling_Stop_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_OPERATION – if PM sampling Stop is called without enabling PM sampling, and PM sampling is already stopped
CUPTI_ERROR_UNKNOWN – for any internal error


## 6.6.9. Typedefs


typedef struct CUpti_PmSampling_Object CUpti_PmSampling_Object