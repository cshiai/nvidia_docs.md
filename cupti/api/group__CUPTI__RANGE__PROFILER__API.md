# 6.9. CUPTI Range Profiling API


Functions, types, and enums that implement the CUPTI Range Profiling API.


## 6.9.1. Data Structures


CUpti_RangeProfiler_CounterDataImage_Initialize_Params
Params for cuptiRangeProfilerCounterDataImageInitialize.

CUpti_RangeProfiler_CounterData_GetRangeInfo_Params
Params for cuptiRangeProfilerCounterDataGetRangeInfo.

CUpti_RangeProfiler_DecodeData_Params
Params for cuptiRangeProfilerDecodeData.

CUpti_RangeProfiler_Disable_Params
Params for cuptiRangeProfilerDisable.

CUpti_RangeProfiler_Enable_Params
Params for cuptiRangeProfilerEnable.

CUpti_RangeProfiler_GetCounterDataInfo_Params
Params for cuptiRangeProfilerGetCounterDataInfo.

CUpti_RangeProfiler_GetCounterDataSize_Params
Params for cuptiRangeProfilerGetCounterDataSize.

CUpti_RangeProfiler_PopRange_Params
Params for cuptiRangeProfilerPopRange.

CUpti_RangeProfiler_PushRange_Params
Params for cuptiRangeProfilerPushRange.

CUpti_RangeProfiler_SetConfig_Params
Params for cuptiRangeProfilerSetConfig.

CUpti_RangeProfiler_Start_Params
Params for cuptiRangeProfilerStart.

CUpti_RangeProfiler_Stop_Params
Params for cuptiRangeProfilerStop.


## 6.9.2. Macros


CUpti_RangeProfiler_CounterDataImage_Initialize_Params_STRUCT_SIZECUpti_RangeProfiler_CounterData_GetRangeInfo_Params_STRUCT_SIZECUpti_RangeProfiler_DecodeData_Params_STRUCT_SIZECUpti_RangeProfiler_Disable_Params_STRUCT_SIZECUpti_RangeProfiler_Enable_Params_STRUCT_SIZECUpti_RangeProfiler_GetCounterDataInfo_Params_STRUCT_SIZECUpti_RangeProfiler_GetCounterDataSize_Params_STRUCT_SIZECUpti_RangeProfiler_PopRange_Params_STRUCT_SIZECUpti_RangeProfiler_PushRange_Params_STRUCT_SIZECUpti_RangeProfiler_SetConfig_Params_STRUCT_SIZECUpti_RangeProfiler_Start_Params_STRUCT_SIZECUpti_RangeProfiler_Stop_Params_STRUCT_SIZE

## 6.9.3. Functions


CUptiResult cuptiRangeProfilerCounterDataGetRangeInfo(CUpti_RangeProfiler_CounterData_GetRangeInfo_Params *pParams)
Get the range name for the given range index.

CUptiResult cuptiRangeProfilerCounterDataImageInitialize(CUpti_RangeProfiler_CounterDataImage_Initialize_Params *pParams)
Initialize the counter data image with the profiling data for the ranges profiled.

CUptiResult cuptiRangeProfilerDecodeData(CUpti_RangeProfiler_DecodeData_Params *pParams)
Decode the profiling data stored in the hardware to the counter data image passed in the SetConfig API.

CUptiResult cuptiRangeProfilerDisable(CUpti_RangeProfiler_Disable_Params *pParams)
Disable the range profiler on the CUDA context and destroy the range profiler object.

CUptiResult cuptiRangeProfilerEnable(CUpti_RangeProfiler_Enable_Params *pParams)
Create a range profiler object and enable range profiling on the CUDA context.

CUptiResult cuptiRangeProfilerGetCounterDataInfo(CUpti_RangeProfiler_GetCounterDataInfo_Params *pParams)
Get the number of ranges stored in the counter data image.

CUptiResult cuptiRangeProfilerGetCounterDataSize(CUpti_RangeProfiler_GetCounterDataSize_Params *pParams)
Get the size of the counter data image required to store the profiling data for the ranges profiled.

CUptiResult cuptiRangeProfilerPopRange(CUpti_RangeProfiler_PopRange_Params *pParams)
pop the current range to the Range Profiler.

CUptiResult cuptiRangeProfilerPushRange(CUpti_RangeProfiler_PushRange_Params *pParams)
Add a new range to the Range Profiler with a given range name.

CUptiResult cuptiRangeProfilerSetConfig(CUpti_RangeProfiler_SetConfig_Params *pParams)
Set the configuration for range profiler like maximum number of ranges per pass, number of nesting levels, range and replay mode and the config image which has scheduling info for metric collection.

CUptiResult cuptiRangeProfilerStart(CUpti_RangeProfiler_Start_Params *pParams)
Start the range profiler.

CUptiResult cuptiRangeProfilerStop(CUpti_RangeProfiler_Stop_Params *pParams)
Stop the range profiler.


## 6.9.4. Typedefs


CUpti_RangeProfiler_Object

## 6.9.5. Variables


size_t CUpti_RangeProfiler_CounterDataImage_Initialize_Params::counterDataSize
[in] Size of the counter data image.

uint8_t * CUpti_RangeProfiler_CounterDataImage_Initialize_Params::pCounterData
[in] Counter data image.

void * CUpti_RangeProfiler_CounterDataImage_Initialize_Params::pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object * CUpti_RangeProfiler_CounterDataImage_Initialize_Params::pRangeProfilerObject
[in] Periodic sampler object.

size_t CUpti_RangeProfiler_CounterDataImage_Initialize_Params::structSize
[in] Size of the data structure.

size_t CUpti_RangeProfiler_CounterData_GetRangeInfo_Params::counterDataImageSize
[in] Size of the counter data image.

const uint8_t * CUpti_RangeProfiler_CounterData_GetRangeInfo_Params::pCounterDataImage
[in] Counter data image.

void * CUpti_RangeProfiler_CounterData_GetRangeInfo_Params::pPriv
[in] Set to NULL.

const char * CUpti_RangeProfiler_CounterData_GetRangeInfo_Params::rangeDelimiter
[in] range delimiter.

size_t CUpti_RangeProfiler_CounterData_GetRangeInfo_Params::rangeIndex
[in] Index of the sample.

const char * CUpti_RangeProfiler_CounterData_GetRangeInfo_Params::rangeName
[out] RangeName;

size_t CUpti_RangeProfiler_CounterData_GetRangeInfo_Params::structSize
[in] Size of the data structure.

size_t CUpti_RangeProfiler_DecodeData_Params::numOfRangeDropped
[out] Number of ranges dropped in the processed passes.

void * CUpti_RangeProfiler_DecodeData_Params::pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object * CUpti_RangeProfiler_DecodeData_Params::pRangeProfilerObject
[in] Range Profiler Object.

size_t CUpti_RangeProfiler_DecodeData_Params::structSize
[in] Size of the data structure.

void * CUpti_RangeProfiler_Disable_Params::pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object * CUpti_RangeProfiler_Disable_Params::pRangeProfilerObject
[in] Range Profiler Object.

size_t CUpti_RangeProfiler_Disable_Params::structSize
[in] Size of the data structure.

CUcontext CUpti_RangeProfiler_Enable_Params::ctx
[in] Context to be used for profiling.

void * CUpti_RangeProfiler_Enable_Params::pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object * CUpti_RangeProfiler_Enable_Params::pRangeProfilerObject
[out] Range Profiler Object.

size_t CUpti_RangeProfiler_Enable_Params::structSize
[in] Size of the data structure.

size_t CUpti_RangeProfiler_GetCounterDataInfo_Params::counterDataImageSize
[in] Size of the counter data image.

size_t CUpti_RangeProfiler_GetCounterDataInfo_Params::numTotalRanges
[out] Number of ranges in the counter data image.

const uint8_t * CUpti_RangeProfiler_GetCounterDataInfo_Params::pCounterDataImage
[in] Counter data image.

void * CUpti_RangeProfiler_GetCounterDataInfo_Params::pPriv
[in] Set to NULL.

size_t CUpti_RangeProfiler_GetCounterDataInfo_Params::structSize
[in] Size of the data structure.

size_t CUpti_RangeProfiler_GetCounterDataSize_Params::counterDataSize
[out] Size of the counter data image.

size_t CUpti_RangeProfiler_GetCounterDataSize_Params::maxNumOfRanges
[in] Maximum number of ranges to be stored in the counter data image.

uint32_t CUpti_RangeProfiler_GetCounterDataSize_Params::maxNumRangeTreeNodes
[in] Maximum number of RangeTree nodes; must be >= maxNumOfRanges

size_t CUpti_RangeProfiler_GetCounterDataSize_Params::numMetrics
[in] Number of metrics to be collected.

const char  CUpti_RangeProfiler_GetCounterDataSize_Params::pMetricNames
[in] Names of the metrics to be collected.

void * CUpti_RangeProfiler_GetCounterDataSize_Params::pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object * CUpti_RangeProfiler_GetCounterDataSize_Params::pRangeProfilerObject
[in] Periodic sampler object.

size_t CUpti_RangeProfiler_GetCounterDataSize_Params::structSize
[in] Size of the data structure.

void * CUpti_RangeProfiler_PopRange_Params::pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object * CUpti_RangeProfiler_PopRange_Params::pRangeProfilerObject
[in] Range Profiler Object.

size_t CUpti_RangeProfiler_PopRange_Params::structSize
[in] Size of the data structure.

void * CUpti_RangeProfiler_PushRange_Params::pPriv
[in] Set to NULL.

const char * CUpti_RangeProfiler_PushRange_Params::pRangeName
[in] Name of the range to be profiled (only valid for User range mode).

CUpti_RangeProfiler_Object * CUpti_RangeProfiler_PushRange_Params::pRangeProfilerObject
[in] Range Profiler Object.

size_t CUpti_RangeProfiler_PushRange_Params::structSize
[in] Size of the data structure.

size_t CUpti_RangeProfiler_SetConfig_Params::configSize
[in] Size of the config image.

size_t CUpti_RangeProfiler_SetConfig_Params::counterDataImageSize
[in] Size of the counter data image.

size_t CUpti_RangeProfiler_SetConfig_Params::maxRangesPerPass
[in] Maximum number of ranges that can be profiled in a pass.

uint16_t CUpti_RangeProfiler_SetConfig_Params::minNestingLevel
[in] minimum nesting level to be profiled.

uint16_t CUpti_RangeProfiler_SetConfig_Params::numNestingLevels
[in] number of nesting level to be profiled. For Auto range mode, this should be set to 1.

const uint8_t * CUpti_RangeProfiler_SetConfig_Params::pConfig
[in] Config image.

uint8_t * CUpti_RangeProfiler_SetConfig_Params::pCounterDataImage
[in] Counter data image.

void * CUpti_RangeProfiler_SetConfig_Params::pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object * CUpti_RangeProfiler_SetConfig_Params::pRangeProfilerObject
[in] Range Profiler Object.

size_t CUpti_RangeProfiler_SetConfig_Params::passIndex
[in] Pass index for the replay session.

CUpti_ProfilerRange CUpti_RangeProfiler_SetConfig_Params::range
[in] Profiling Range mode.

CUpti_ProfilerReplayMode CUpti_RangeProfiler_SetConfig_Params::replayMode
[in] Replay mode.

size_t CUpti_RangeProfiler_SetConfig_Params::structSize
[in] Size of the data structure.

uint16_t CUpti_RangeProfiler_SetConfig_Params::targetNestingLevel
[in] Target nesting level for the replay session.

void * CUpti_RangeProfiler_Start_Params::pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object * CUpti_RangeProfiler_Start_Params::pRangeProfilerObject
[in] Range Profiler Object.

size_t CUpti_RangeProfiler_Start_Params::structSize
[in] Size of the data structure.

uint8_t CUpti_RangeProfiler_Stop_Params::isAllPassSubmitted
[out] 1 if all passes are submitted to GPU for collection, 0 otherwise.

void * CUpti_RangeProfiler_Stop_Params::pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object * CUpti_RangeProfiler_Stop_Params::pRangeProfilerObject
[in] Range Profiler Object.

size_t CUpti_RangeProfiler_Stop_Params::passIndex
[out] pass index for the replay session.

size_t CUpti_RangeProfiler_Stop_Params::structSize
[in] Size of the data structure.

size_t CUpti_RangeProfiler_Stop_Params::targetNestingLevel
[out] target nesting level for the replay session.


## 6.9.6. Macros


CUpti_RangeProfiler_CounterDataImage_Initialize_Params_STRUCT_SIZECUpti_RangeProfiler_CounterData_GetRangeInfo_Params_STRUCT_SIZECUpti_RangeProfiler_DecodeData_Params_STRUCT_SIZECUpti_RangeProfiler_Disable_Params_STRUCT_SIZECUpti_RangeProfiler_Enable_Params_STRUCT_SIZECUpti_RangeProfiler_GetCounterDataInfo_Params_STRUCT_SIZECUpti_RangeProfiler_GetCounterDataSize_Params_STRUCT_SIZECUpti_RangeProfiler_PopRange_Params_STRUCT_SIZECUpti_RangeProfiler_PushRange_Params_STRUCT_SIZECUpti_RangeProfiler_SetConfig_Params_STRUCT_SIZECUpti_RangeProfiler_Start_Params_STRUCT_SIZECUpti_RangeProfiler_Stop_Params_STRUCT_SIZE

## 6.9.7. Functions


CUptiResult cuptiRangeProfilerCounterDataGetRangeInfo(

CUpti_RangeProfiler_CounterData_GetRangeInfo_Params *pParams,

)
Get the range name for the given range index.

Parameters:
pParams – A pointer to CUpti_RangeProfiler_CounterData_GetRangeInfo_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiRangeProfilerCounterDataImageInitialize(

CUpti_RangeProfiler_CounterDataImage_Initialize_Params *pParams,

)
Initialize the counter data image with the profiling data for the ranges profiled.

Parameters:
pParams – A pointer to CUpti_RangeProfiler_CounterDataImage_Initialize_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_OPERATION – if range profiler CounterDataImageInitialize is called without enabling range profiler
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiRangeProfilerDecodeData(

CUpti_RangeProfiler_DecodeData_Params *pParams,

)
Decode the profiling data stored in the hardware to the counter data image passed in the SetConfig API.
This API should be called after cuptiRangeProfilerStop. The counter data image will be updated with the profiling data for the ranges profiled.
For the cases where the number of ranges counter data image can store is less than the number of ranges profiled (= maxRangesPerPass in SetConfig API), the counter data image will report dropped ranges.

Parameters:
pParams – A pointer to CUpti_RangeProfiler_DecodeData_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_OPERATION – if range profiler DecodeData is called without enabling range profiler
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiRangeProfilerDisable(

CUpti_RangeProfiler_Disable_Params *pParams,

)
Disable the range profiler on the CUDA context and destroy the range profiler object.

Parameters:
pParams – A pointer to CUpti_RangeProfiler_Disable_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid


CUptiResult cuptiRangeProfilerEnable(

CUpti_RangeProfiler_Enable_Params *pParams,

)
Create a range profiler object and enable range profiling on the CUDA context.

Parameters:
pParams – A pointer to CUpti_RangeProfiler_Enable_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_OUT_OF_MEMORY – if memory allocation fails while creating the PM sampling object
CUPTI_ERROR_INSUFFICIENT_PRIVILEGES – if the user does not have sufficient privileges to perform the operation
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiRangeProfilerGetCounterDataInfo(

CUpti_RangeProfiler_GetCounterDataInfo_Params *pParams,

)
Get the number of ranges stored in the counter data image.

Parameters:
pParams – A pointer to CUpti_RangeProfiler_GetCounterDataInfo_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiRangeProfilerGetCounterDataSize(

CUpti_RangeProfiler_GetCounterDataSize_Params *pParams,

)
Get the size of the counter data image required to store the profiling data for the ranges profiled.

Parameters:
pParams – A pointer to CUpti_RangeProfiler_GetCounterDataSize_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_OPERATION – if range profiler GetCounterDataSize is called without enabling range profiler
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiRangeProfilerPopRange(

CUpti_RangeProfiler_PopRange_Params *pParams,

)
pop the current range to the Range Profiler.
The number of pop range API call should be same as number of push ranges in the same order.

Parameters:
pParams – A pointer to CUpti_RangeProfiler_PopRange_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_OPERATION – if range profiler PopRange is called without enabling range profiler
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiRangeProfilerPushRange(

CUpti_RangeProfiler_PushRange_Params *pParams,

)
Add a new range to the Range Profiler with a given range name.
For nested ranges, this API should be called again for the innermost range. For profiling the nested range, users need to set the values for minNestingLevel and numNestingLevels in the SetConfig API.

Parameters:
pParams – A pointer to CUpti_RangeProfiler_PushRange_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_OPERATION – if range profiler PushRange is called without enabling range profiler
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiRangeProfilerSetConfig(

CUpti_RangeProfiler_SetConfig_Params *pParams,

)
Set the configuration for range profiler like maximum number of ranges per pass, number of nesting levels, range and replay mode and the config image which has scheduling info for metric collection.

Parameters:
pParams – A pointer to CUpti_RangeProfiler_SetConfig_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid


CUptiResult cuptiRangeProfilerStart(

CUpti_RangeProfiler_Start_Params *pParams,

)
Start the range profiler.

Parameters:
pParams – A pointer to CUpti_RangeProfiler_Start_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_OPERATION – if range profiler Start is called without enabling range profiler
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiRangeProfilerStop(

CUpti_RangeProfiler_Stop_Params *pParams,

)
Stop the range profiler.

Parameters:
pParams – A pointer to CUpti_RangeProfiler_Stop_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_OPERATION – if range profiler Stop is called without enabling range profiler
CUPTI_ERROR_UNKNOWN – for any internal error


## 6.9.8. Typedefs


typedef struct CUpti_RangeProfiler_Object CUpti_RangeProfiler_Object