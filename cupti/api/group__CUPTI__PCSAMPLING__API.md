# 6.4. CUPTI PC Sampling API


Functions, types, and enums that implement the CUPTI PC Sampling API.


## 6.4.1. Data Structures


CUpti_GetCubinCrcParams
Params for cuptiGetCubinCrc.

CUpti_GetSassToSourceCorrelationParams
Params for cuptiGetSassToSourceCorrelation.

CUpti_PCSamplingConfigurationInfo
PC sampling configuration information structure.

CUpti_PCSamplingConfigurationInfoParams
PC sampling configuration structure.

CUpti_PCSamplingData
Collected PC Sampling data.

CUpti_PCSamplingDisableParams
Params for cuptiPCSamplingDisable.

CUpti_PCSamplingEnableParams
Params for cuptiPCSamplingEnable.

CUpti_PCSamplingGetDataParams
Params for cuptiPCSamplingEnable.

CUpti_PCSamplingGetNumStallReasonsParams
Params for cuptiPCSamplingGetNumStallReasons.

CUpti_PCSamplingGetStallReasonsParams
Params for cuptiPCSamplingGetStallReasons.

CUpti_PCSamplingPCData
PC Sampling data.

CUpti_PCSamplingStallReason
PC Sampling stall reasons.

CUpti_PCSamplingStartParams
Params for cuptiPCSamplingStart.

CUpti_PCSamplingStopParams
Params for cuptiPCSamplingStop.


## 6.4.2. Macros


CUPTI_STALL_REASON_STRING_SIZECUpti_GetCubinCrcParamsSizeCUpti_GetSassToSourceCorrelationParamsSizeCUpti_PCSamplingConfigurationInfoParamsSizeCUpti_PCSamplingDisableParamsSizeCUpti_PCSamplingEnableParamsSizeCUpti_PCSamplingGetDataParamsSizeCUpti_PCSamplingGetNumStallReasonsParamsSizeCUpti_PCSamplingGetStallReasonsParamsSizeCUpti_PCSamplingStartParamsSizeCUpti_PCSamplingStopParamsSize

## 6.4.3. Enumerations


CUpti_PCSamplingCollectionMode
PC Sampling collection mode.

CUpti_PCSamplingConfigurationAttributeType
PC Sampling configuration attributes.

CUpti_PCSamplingOutputDataFormat
PC Sampling output data format.


## 6.4.4. Functions


CUptiResult cuptiGetCubinCrc(CUpti_GetCubinCrcParams *pParams)
Get the CRC of cubin.

CUptiResult cuptiGetSassToSourceCorrelation(CUpti_GetSassToSourceCorrelationParams *pParams)
SASS to Source correlation.

CUptiResult cuptiPCSamplingDisable(CUpti_PCSamplingDisableParams *pParams)
Disable PC sampling.

CUptiResult cuptiPCSamplingEnable(CUpti_PCSamplingEnableParams *pParams)
Enable PC sampling.

CUptiResult cuptiPCSamplingGetConfigurationAttribute(CUpti_PCSamplingConfigurationInfoParams *pParams)
Read PC Sampling configuration attribute.

CUptiResult cuptiPCSamplingGetData(CUpti_PCSamplingGetDataParams *pParams)
Flush GPU PC sampling data periodically.

CUptiResult cuptiPCSamplingGetNumStallReasons(CUpti_PCSamplingGetNumStallReasonsParams *pParams)
Get PC sampling stall reason count.

CUptiResult cuptiPCSamplingGetStallReasons(CUpti_PCSamplingGetStallReasonsParams *pParams)
Get PC sampling stall reasons.

CUptiResult cuptiPCSamplingSetConfigurationAttribute(CUpti_PCSamplingConfigurationInfoParams *pParams)
Write PC Sampling configuration attribute.

CUptiResult cuptiPCSamplingStart(CUpti_PCSamplingStartParams *pParams)
Start PC sampling.

CUptiResult cuptiPCSamplingStop(CUpti_PCSamplingStopParams *pParams)
Stop PC sampling.

CUptiResult cuptiRegisterComputeCrcCallback(CUpti_ComputeCrcCallbackFunc funcComputeCubinCrc)
Register callback function with CUPTI to use your own algorithm to compute cubin crc.


## 6.4.5. Typedefs


CUpti_ComputeCrcCallbackFunc
Function type for callback used by CUPTI to request crc of loaded module.


## 6.4.6. Macros


CUPTI_STALL_REASON_STRING_SIZECUpti_GetCubinCrcParamsSizeCUpti_GetSassToSourceCorrelationParamsSizeCUpti_PCSamplingConfigurationInfoParamsSizeCUpti_PCSamplingDisableParamsSizeCUpti_PCSamplingEnableParamsSizeCUpti_PCSamplingGetDataParamsSizeCUpti_PCSamplingGetNumStallReasonsParamsSizeCUpti_PCSamplingGetStallReasonsParamsSizeCUpti_PCSamplingStartParamsSizeCUpti_PCSamplingStopParamsSize

## 6.4.7. Enumerations


enum CUpti_PCSamplingCollectionMode
PC Sampling collection mode.
Values:

enumerator CUPTI_PC_SAMPLING_COLLECTION_MODE_INVALID
INVALID Value.

enumerator CUPTI_PC_SAMPLING_COLLECTION_MODE_CONTINUOUS
Continuous mode.
Kernels are not serialized in this mode.

enumerator CUPTI_PC_SAMPLING_COLLECTION_MODE_KERNEL_SERIALIZED
Serialized mode.
Kernels are serialized in this mode.


enum CUpti_PCSamplingConfigurationAttributeType
PC Sampling configuration attributes.
PC Sampling configuration attribute types. These attributes can be read using cuptiPCSamplingGetConfigurationAttribute and can be written using cuptiPCSamplingSetConfigurationAttribute. Attributes marked [r] can only be read using cuptiPCSamplingGetConfigurationAttribute [w] can only be written using cuptiPCSamplingSetConfigurationAttribute [rw] can be read using cuptiPCSamplingGetConfigurationAttribute and written using cuptiPCSamplingSetConfigurationAttribute
Values:

enumerator CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_INVALID

enumerator CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_SAMPLING_PERIOD
[rw] Sampling period for PC Sampling.
DEFAULT - CUPTI defined value based on number of SMs Valid values for the sampling periods are between 5 to 31 both inclusive. This will set the sampling period to (2^samplingPeriod) cycles. For e.g. for sampling period = 5 to 31, cycles = 32, 64, 128,…, 2^31 Value is a uint32_t

enumerator CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_STALL_REASON
[w] Number of stall reasons to collect.
DEFAULT - All stall reasons will be collected Value is a size_t [w] Stall reasons to collect DEFAULT - All stall reasons will be collected Input value should be a pointer pointing to array of stall reason indexes containing all the stall reason indexes to collect.

enumerator CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_SCRATCH_BUFFER_SIZE
[rw] Size of SW buffer for raw PC counter data downloaded from HW buffer DEFAULT - 1 MB, which can accommodate approximately 5500 PCs with all stall reasons Approximately it takes 16 Bytes (and some fixed size memory) to accommodate one PC with one stall reason For e.g.
1 PC with 1 stall reason = 32 Bytes 1 PC with 2 stall reason = 48 Bytes 1 PC with 4 stall reason = 96 Bytes Value is a size_t

enumerator CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_HARDWARE_BUFFER_SIZE
[rw] Size of HW buffer in bytes DEFAULT - 512 MB If sampling period is too less, HW buffer can overflow and drop PC data Value is a size_t

enumerator CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_COLLECTION_MODE
[rw] PC Sampling collection mode DEFAULT - CUPTI_PC_SAMPLING_COLLECTION_MODE_CONTINUOUS Input value should be of type CUpti_PCSamplingCollectionMode.

enumerator CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_ENABLE_START_STOP_CONTROL
[rw] Control over PC Sampling data collection range Default - 0 1 - Allows user to start and stop PC Sampling using APIs - cuptiPCSamplingStart() - Start PC Sampling cuptiPCSamplingStop() - Stop PC Sampling Value is a uint32_t

enumerator CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_OUTPUT_DATA_FORMAT
[w] Value for output data format Default - CUPTI_PC_SAMPLING_OUTPUT_DATA_FORMAT_PARSED Input value should be of type CUpti_PCSamplingOutputDataFormat.

enumerator CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_SAMPLING_DATA_BUFFER
[w] Data buffer to hold collected PC Sampling data PARSED_DATA Default - none.
Buffer type is void * which can point to PARSED_DATA Refer CUpti_PCSamplingData for buffer format for PARSED_DATA

enumerator CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_WORKER_THREAD_PERIODIC_SLEEP_SPAN
[rw] Control sleep time of the worker threads created by CUPTI for various PC sampling operations.
CUPTI creates multiple worker threads to offload certain operations to these threads. This includes decoding of HW data to the CUPTI PC sampling data and correlating PC data to SASS instructions. CUPTI wakes up these threads periodically. Default - 100 milliseconds. Value is a uint32_t

enumerator CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_FORCE_INT


enum CUpti_PCSamplingOutputDataFormat
PC Sampling output data format.
Values:

enumerator CUPTI_PC_SAMPLING_OUTPUT_DATA_FORMAT_INVALID

enumerator CUPTI_PC_SAMPLING_OUTPUT_DATA_FORMAT_PARSED
HW buffer data will be parsed during collection of data.


## 6.4.8. Functions


CUptiResult cuptiGetCubinCrc(CUpti_GetCubinCrcParams *pParams)
Get the CRC of cubin.
This function returns the CRC of provided cubin binary.

Parameters:
pParams – A pointer to CUpti_GetCubinCrcParams

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if parameter cubin is NULL or provided cubinSize is zero or size field is not set.


CUptiResult cuptiGetSassToSourceCorrelation(

CUpti_GetSassToSourceCorrelationParams *pParams,

)
SASS to Source correlation.

It is expected from user to free allocated memory for fileName and dirName after use.

Parameters:
pParams – A pointer to CUpti_GetSassToSourceCorrelationParams

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if either of the parameters cubin or functionName is NULL or cubinSize is zero or size field is not set correctly.
CUPTI_ERROR_INVALID_MODULE – provided cubin is invalid.
CUPTI_ERROR_UNKNOWN – an internal error occurred. This error code is also used for cases when the function is not present in the module. A better error code will be returned in the future release.


CUptiResult cuptiPCSamplingDisable(

CUpti_PCSamplingDisableParams *pParams,

)
Disable PC sampling.
For application which doesn’t destroy the CUDA context explicitly, this API does the PC Sampling tear-down, joins threads and copies PC records in the buffer provided during the PC sampling configuration. PC records which can’t be accommodated in the buffer are discarded.

Parameters:
pParams – A pointer to CUpti_PCSamplingDisableParams

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device does not support the API


CUptiResult cuptiPCSamplingEnable(

CUpti_PCSamplingEnableParams *pParams,

)
Enable PC sampling.

Parameters:
pParams – A pointer to CUpti_PCSamplingEnableParams

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device does not support the API


CUptiResult cuptiPCSamplingGetConfigurationAttribute(

CUpti_PCSamplingConfigurationInfoParams *pParams,

)
Read PC Sampling configuration attribute.

Parameters:
pParams – A pointer to CUpti_PCSamplingConfigurationInfoParams containing PC sampling configuration.

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_OPERATION – if this API is called with some invalid attribute.
CUPTI_ERROR_INVALID_PARAMETER – if attrib is not valid or any pParams is not valid
CUPTI_ERROR_PARAMETER_SIZE_NOT_SUFFICIENT – indicates that the value buffer is too small to hold the attribute value
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device does not support the API


CUptiResult cuptiPCSamplingGetData(

CUpti_PCSamplingGetDataParams *pParams,

)
Flush GPU PC sampling data periodically.
Flushing of GPU PC Sampling data is required at following point to maintain uniqueness of PCs: For CUPTI_PC_SAMPLING_COLLECTION_MODE_CONTINUOUS, after every module load-unload-load For CUPTI_PC_SAMPLING_COLLECTION_MODE_KERNEL_SERIALIZED, after every kernel ends If configuration option CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_ENABLE_START_STOP_CONTROL is enabled, then after every range end i.e. cuptiPCSamplingStop()
If application is profiled in CUPTI_PC_SAMPLING_COLLECTION_MODE_CONTINUOUS, with disabled
CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_ENABLE_START_STOP_CONTROL, and there is no module unload, user can collect data in two ways: Use cuptiPCSamplingGetData() API periodically Use cuptiPCSamplingDisable() on application exit and read GPU PC sampling data from sampling data buffer passed during configuration. Note: In case, cuptiPCSamplingGetData() API is not called periodically, then sampling data buffer passed during configuration should be large enough to hold all PCs data.
cuptiPCSamplingGetData() API never does device synchronization. It is possible that when the API is called there is some unconsumed data from the HW buffer. In this case CUPTI provides only the data available with it at that moment.

Parameters:
pParams – A pointer to CUpti_PCSamplingGetDataParams

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_OPERATION – if this API is called without enabling PC sampling.
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device
CUPTI_ERROR_OUT_OF_MEMORY – indicates that the HW buffer is full does not support the API


CUptiResult cuptiPCSamplingGetNumStallReasons(

CUpti_PCSamplingGetNumStallReasonsParams *pParams,

)
Get PC sampling stall reason count.

Parameters:
pParams – A pointer to CUpti_PCSamplingGetNumStallReasonsParams

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device does not support the API


CUptiResult cuptiPCSamplingGetStallReasons(

CUpti_PCSamplingGetStallReasonsParams *pParams,

)
Get PC sampling stall reasons.

Parameters:
pParams – A pointer to CUpti_PCSamplingGetStallReasonsParams

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device does not support the API


CUptiResult cuptiPCSamplingSetConfigurationAttribute(

CUpti_PCSamplingConfigurationInfoParams *pParams,

)
Write PC Sampling configuration attribute.

Parameters:
pParams – A pointer to CUpti_PCSamplingConfigurationInfoParams containing PC sampling configuration.

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_OPERATION – if this API is called with some invalid attrib.
CUPTI_ERROR_INVALID_PARAMETER – if attribute value is not valid or any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device does not support the API


CUptiResult cuptiPCSamplingStart(

CUpti_PCSamplingStartParams *pParams,

)
Start PC sampling.
User can collect PC Sampling data for user-defined range specified by Start/Stop APIs. This API can be used to mark starting of range. Set configuration option
CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_ENABLE_START_STOP_CONTROL to use this API.

Parameters:
pParams – A pointer to CUpti_PCSamplingStartParams

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_OPERATION – if this API is called with incorrect PC Sampling configuration.
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device does not support the API


CUptiResult cuptiPCSamplingStop(CUpti_PCSamplingStopParams *pParams)
Stop PC sampling.
User can collect PC Sampling data for user-defined range specified by Start/Stop APIs. This API can be used to mark end of range. Set configuration option
CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_ENABLE_START_STOP_CONTROL to use this API.

Parameters:
pParams – A pointer to CUpti_PCSamplingStopParams

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_OPERATION – if this API is called with incorrect PC Sampling configuration.
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device does not support the API


CUptiResult cuptiRegisterComputeCrcCallback(

CUpti_ComputeCrcCallbackFunc funcComputeCubinCrc,

)
Register callback function with CUPTI to use your own algorithm to compute cubin crc.
This function registers a callback function and it gets called from CUPTI when a CUDA module is loaded.

Parameters:
funcComputeCubinCrc – callback is invoked when a CUDA module is loaded.

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if funcComputeCubinCrc is NULL.


## 6.4.9. Typedefs


typedef void (*CUpti_ComputeCrcCallbackFunc)(const void *cubin, size_t cubinSize, uint64_t *cubinCrc)
Function type for callback used by CUPTI to request crc of loaded module.
This callback function ask for crc of provided module in function. The provided crc will be stored in PC sampling records i.e. in the field ‘cubinCrc’ of the PC sampling struct CUpti_PCSamplingPCData. The CRC is uses during the offline source correlation to uniquely identify the module.

Param cubin:
The pointer to cubin binary

Param cubinSize:
The size of cubin binary.

Param cubinCrc:
Returns the computed crc of cubin.