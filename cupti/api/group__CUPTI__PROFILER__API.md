# 6.8. CUPTI Profiling API


Functions, types, and enums that implement the CUPTI Profiling API.


## 6.8.1. Data Structures


CUpti_Profiler_BeginPass_Params
Params for cuptiProfilerBeginPass.

CUpti_Profiler_BeginSession_Params
Params for cuptiProfilerBeginSession.

CUpti_Profiler_CounterDataImageOptions
Input parameter to define the counterDataImage.

CUpti_Profiler_CounterDataImage_CalculateScratchBufferSize_Params
Params for cuptiProfilerCounterDataImageCalculateScratchBufferSize.

CUpti_Profiler_CounterDataImage_CalculateSize_Params
Params for cuptiProfilerCounterDataImageCalculateSize.

CUpti_Profiler_CounterDataImage_InitializeScratchBuffer_Params
Params for cuptiProfilerCounterDataImageInitializeScratchBuffer.

CUpti_Profiler_CounterDataImage_Initialize_Params
Params for cuptiProfilerCounterDataImageInitialize.

CUpti_Profiler_DeInitialize_Params
Default parameter for cuptiProfilerDeInitialize.

CUpti_Profiler_DeviceSupported_Params
Params for cuptiProfilerDeviceSupported.

CUpti_Profiler_DisableProfiling_Params
Params for cuptiProfilerDisableProfiling.

CUpti_Profiler_EnableProfiling_Params
Params for cuptiProfilerEnableProfiling.

CUpti_Profiler_EndPass_Params
Params for cuptiProfilerEndPass.

CUpti_Profiler_EndSession_Params
Params for cuptiProfilerEndSession.

CUpti_Profiler_FlushCounterData_Params
Params for cuptiProfilerFlushCounterData.

CUpti_Profiler_GetCounterAvailability_Params
Params for cuptiProfilerGetCounterAvailability.

CUpti_Profiler_Initialize_Params
Default parameter for cuptiProfilerInitialize.

CUpti_Profiler_IsPassCollected_Params
Params for cuptiProfilerIsPassCollected.

CUpti_Profiler_PopRange_ParamsCUpti_Profiler_PushRange_ParamsCUpti_Profiler_SetConfig_Params
Params for cuptiProfilerSetConfig.

CUpti_Profiler_UnsetConfig_Params
Params for cuptiProfilerUnsetConfig.


## 6.8.2. Macros


CUpti_Profiler_BeginPass_Params_STRUCT_SIZECUpti_Profiler_BeginSession_Params_STRUCT_SIZECUpti_Profiler_CounterDataImageOptions_STRUCT_SIZECUpti_Profiler_CounterDataImage_CalculateScratchBufferSize_Params_STRUCT_SIZECUpti_Profiler_CounterDataImage_CalculateSize_Params_STRUCT_SIZECUpti_Profiler_CounterDataImage_InitializeScratchBuffer_Params_STRUCT_SIZECUpti_Profiler_CounterDataImage_Initialize_Params_STRUCT_SIZECUpti_Profiler_DeInitialize_Params_STRUCT_SIZECUpti_Profiler_DeviceSupported_Params_STRUCT_SIZECUpti_Profiler_DisableProfiling_Params_STRUCT_SIZECUpti_Profiler_EnableProfiling_Params_STRUCT_SIZECUpti_Profiler_EndPass_Params_STRUCT_SIZECUpti_Profiler_EndSession_Params_STRUCT_SIZECUpti_Profiler_FlushCounterData_Params_STRUCT_SIZECUpti_Profiler_GetCounterAvailability_Params_STRUCT_SIZECUpti_Profiler_Initialize_Params_STRUCT_SIZECUpti_Profiler_IsPassCollected_Params_STRUCT_SIZECUpti_Profiler_PopRange_Params_STRUCT_SIZECUpti_Profiler_PushRange_Params_STRUCT_SIZECUpti_Profiler_SetConfig_Params_STRUCT_SIZECUpti_Profiler_UnsetConfig_Params_STRUCT_SIZE

## 6.8.3. Enumerations


CUpti_ProfilerRange
Profiler range attribute.

CUpti_ProfilerReplayMode
Profiler replay attribute.

CUpti_Profiler_API
Profiler API types.

CUpti_Profiler_Support_Level
Generic support level enum for CUPTI.


## 6.8.4. Functions


CUptiResult cuptiProfilerBeginPass(CUpti_Profiler_BeginPass_Params *pParams)
Replay API: used for multipass collection.

CUptiResult cuptiProfilerBeginSession(CUpti_Profiler_BeginSession_Params *pParams)
Begin profiling session sets up the profiling on the device.

CUptiResult cuptiProfilerCounterDataImageCalculateScratchBufferSize(CUpti_Profiler_CounterDataImage_CalculateScratchBufferSize_Params *pParams)
A temporary storage for CounterData image needed for internal operations.

CUptiResult cuptiProfilerCounterDataImageCalculateSize(CUpti_Profiler_CounterDataImage_CalculateSize_Params *pParams)
A CounterData image allocates space for values for each counter for each range.

CUptiResult cuptiProfilerCounterDataImageInitialize(CUpti_Profiler_CounterDataImage_Initialize_Params *pParams)CUptiResult cuptiProfilerCounterDataImageInitializeScratchBuffer(CUpti_Profiler_CounterDataImage_InitializeScratchBuffer_Params *pParams)CUptiResult cuptiProfilerDeInitialize(CUpti_Profiler_DeInitialize_Params *pParams)
DeInitializes the profiler interface.

CUptiResult cuptiProfilerDeviceSupported(CUpti_Profiler_DeviceSupported_Params *pParams)
Query device compatibility with Profiling API.

CUptiResult cuptiProfilerDisableProfiling(CUpti_Profiler_DisableProfiling_Params *pParams)
Disable Profiling.

CUptiResult cuptiProfilerEnableProfiling(CUpti_Profiler_EnableProfiling_Params *pParams)
Enables Profiling.

CUptiResult cuptiProfilerEndPass(CUpti_Profiler_EndPass_Params *pParams)
Replay API: used for multipass collection.

CUptiResult cuptiProfilerEndSession(CUpti_Profiler_EndSession_Params *pParams)
Ends profiling session.

CUptiResult cuptiProfilerFlushCounterData(CUpti_Profiler_FlushCounterData_Params *pParams)
Decode all the submitted passes.

CUptiResult cuptiProfilerGetCounterAvailability(CUpti_Profiler_GetCounterAvailability_Params *pParams)
Query counter availibility.

CUptiResult cuptiProfilerInitialize(CUpti_Profiler_Initialize_Params *pParams)
Initializes the profiler interface.

CUptiResult cuptiProfilerIsPassCollected(CUpti_Profiler_IsPassCollected_Params *pParams)
Asynchronous call to query if the submitted pass to GPU is collected.

CUptiResult cuptiProfilerPopRange(CUpti_Profiler_PopRange_Params *pParams)
Range API's : Pop user range.

CUptiResult cuptiProfilerPushRange(CUpti_Profiler_PushRange_Params *pParams)
Range API's : Push user range.

CUptiResult cuptiProfilerSetConfig(CUpti_Profiler_SetConfig_Params *pParams)
Set metrics configuration to be profiled.

CUptiResult cuptiProfilerUnsetConfig(CUpti_Profiler_UnsetConfig_Params *pParams)
Unset metrics configuration profiled.


## 6.8.5. Macros


CUpti_Profiler_BeginPass_Params_STRUCT_SIZECUpti_Profiler_BeginSession_Params_STRUCT_SIZECUpti_Profiler_CounterDataImageOptions_STRUCT_SIZECUpti_Profiler_CounterDataImage_CalculateScratchBufferSize_Params_STRUCT_SIZECUpti_Profiler_CounterDataImage_CalculateSize_Params_STRUCT_SIZECUpti_Profiler_CounterDataImage_InitializeScratchBuffer_Params_STRUCT_SIZECUpti_Profiler_CounterDataImage_Initialize_Params_STRUCT_SIZECUpti_Profiler_DeInitialize_Params_STRUCT_SIZECUpti_Profiler_DeviceSupported_Params_STRUCT_SIZECUpti_Profiler_DisableProfiling_Params_STRUCT_SIZECUpti_Profiler_EnableProfiling_Params_STRUCT_SIZECUpti_Profiler_EndPass_Params_STRUCT_SIZECUpti_Profiler_EndSession_Params_STRUCT_SIZECUpti_Profiler_FlushCounterData_Params_STRUCT_SIZECUpti_Profiler_GetCounterAvailability_Params_STRUCT_SIZECUpti_Profiler_Initialize_Params_STRUCT_SIZECUpti_Profiler_IsPassCollected_Params_STRUCT_SIZECUpti_Profiler_PopRange_Params_STRUCT_SIZECUpti_Profiler_PushRange_Params_STRUCT_SIZECUpti_Profiler_SetConfig_Params_STRUCT_SIZECUpti_Profiler_UnsetConfig_Params_STRUCT_SIZE

## 6.8.6. Enumerations


enum CUpti_ProfilerRange
Profiler range attribute.
A metric enabled in the session’s configuration is collected separately per unique range-stack in the pass. This is an attribute to collect metrics around each kernel in a profiling session or in an user defined range.
Values:

enumerator CUPTI_Range_INVALID
Invalid value.

enumerator CUPTI_AutoRange
Ranges are auto defined around each kernel in a profiling session.

enumerator CUPTI_UserRange
A range in which metric data to be collected is defined by the user.

enumerator CUPTI_Range_COUNT
Range count.


enum CUpti_ProfilerReplayMode
Profiler replay attribute.
For metrics which require multipass collection, a replay of the GPU kernel(s) is required. This is an attribute which specify how the replay of the kernel(s) to be measured is done.
Values:

enumerator CUPTI_Replay_INVALID
Invalid Value.

enumerator CUPTI_ApplicationReplay
Replay is done by CUPTI user around the process.

enumerator CUPTI_KernelReplay
Replay is done around kernel implicitly by CUPTI.

enumerator CUPTI_UserReplay
Replay is done by CUPTI user within a process.

enumerator CUPTI_Replay_COUNT
Replay count.


enum CUpti_Profiler_API
Profiler API types.
Values:

enumerator CUPTI_PROFILER_RANGE_PROFILING
CUPTI APIs for range based profiling (cuptiProfiler*)

enumerator CUPTI_PROFILER_PC_SAMPLING
CUPTI APIs collecting pc sampling data (cuptiPcSampling*)

enumerator CUPTI_PROFILER_SASS_METRICS
CUPTI APIs collecting SASS metrics data (cuptiSassMetrics*)

enumerator CUPTI_PROFILER_PM_SAMPLING
CUPTI APIs collecting PM Sampling data (cuptiPmSampling*)

enumerator CUPTI_PROFILER_UNKNOWN


enum CUpti_Profiler_Support_Level
Generic support level enum for CUPTI.
Values:

enumerator CUPTI_PROFILER_CONFIGURATION_UNKNOWN
Configuration support level unknown - either detection code errored out before setting this value, or unable to determine it.

enumerator CUPTI_PROFILER_CONFIGURATION_UNSUPPORTED
Profiling is unavailable. For specific feature fields, this means that the current configuration of this feature does not work with profiling. For instance, SLI-enabled devices do not support profiling, and this value would be returned for SLI on an SLI-enabled device.

enumerator CUPTI_PROFILER_CONFIGURATION_DISABLED
Profiling would be available for this configuration, but was disabled by the system.

enumerator CUPTI_PROFILER_CONFIGURATION_SUPPORTED
Profiling is supported. For specific feature fields, this means that the current configuration of this feature works with profiling. For instance, SLI-enabled devices do not support profiling, and this value would only be returned for devices which are not SLI-enabled.


## 6.8.7. Functions


CUptiResult cuptiProfilerBeginPass(

CUpti_Profiler_BeginPass_Params *pParams,

)
Replay API: used for multipass collection.
These APIs are used if user chooses to replay by itself CUPTI_UserReplay or CUPTI_ApplicationReplay for multipass collection of the metrics configurations. It’s a no-op in case of CUPTI_KernelReplay.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerBeginSession(

CUpti_Profiler_BeginSession_Params *pParams,

)
Begin profiling session sets up the profiling on the device.
Although, it doesn’t start the profiling but GPU resources needed for profiling are allocated. Outside of a session, the GPU will return to its normal operating state.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerCounterDataImageCalculateScratchBufferSize(

CUpti_Profiler_CounterDataImage_CalculateScratchBufferSize_Params *pParams,

)
A temporary storage for CounterData image needed for internal operations.
Use these APIs to calculate the allocation size and initialize counterData image scratch buffer.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerCounterDataImageCalculateSize(

CUpti_Profiler_CounterDataImage_CalculateSize_Params *pParams,

)
A CounterData image allocates space for values for each counter for each range.
User borne the resposibility of managing the counterDataImage allocations. CounterDataPrefix contains meta data about the metrics that will be stored in counterDataImage. Use these APIs to calculate the allocation size and initialize counterData image.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerCounterDataImageInitialize(

CUpti_Profiler_CounterDataImage_Initialize_Params *pParams,

)CUptiResult cuptiProfilerCounterDataImageInitializeScratchBuffer(

CUpti_Profiler_CounterDataImage_InitializeScratchBuffer_Params *pParams,

)CUptiResult cuptiProfilerDeInitialize(

CUpti_Profiler_DeInitialize_Params *pParams,

)
DeInitializes the profiler interface.


CUptiResult cuptiProfilerDeviceSupported(

CUpti_Profiler_DeviceSupported_Params *pParams,

)
Query device compatibility with Profiling API.
Use this call to determine whether a compute device and configuration are compatible with the Profiling API. If the configuration does not support profiling, one of several flags will indicate why.


CUptiResult cuptiProfilerDisableProfiling(

CUpti_Profiler_DisableProfiling_Params *pParams,

)
Disable Profiling.
In CUPTI_AutoRange, these APIs are used to enable/disable profiling for the kernels to be executed in a profiling session.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerEnableProfiling(

CUpti_Profiler_EnableProfiling_Params *pParams,

)
Enables Profiling.
In CUPTI_AutoRange, these APIs are used to enable/disable profiling for the kernels to be executed in a profiling session.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerEndPass(

CUpti_Profiler_EndPass_Params *pParams,

)
Replay API: used for multipass collection.
These APIs are used if user chooses to replay by itself CUPTI_UserReplay or CUPTI_ApplicationReplay for multipass collection of the metrics configurations. Its a no-op in case of CUPTI_KernelReplay. Returns information for next pass.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerEndSession(

CUpti_Profiler_EndSession_Params *pParams,

)
Ends profiling session.
Frees up the GPU resources acquired for profiling. Outside of a session, the GPU will return to it’s normal operating state.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerFlushCounterData(

CUpti_Profiler_FlushCounterData_Params *pParams,

)
Decode all the submitted passes.
Flush Counter data API to ensure every pass is decoded into the counterDataImage passed at beginSession. This will cause the CPU/GPU sync to collect all the undecoded pass.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerGetCounterAvailability(

CUpti_Profiler_GetCounterAvailability_Params *pParams,

)
Query counter availibility.
Use this API to query counter availability information in a buffer which can be used to filter unavailable raw metrics on host. Note: This API may fail, if any profiling or sampling session is active on the specified context or its device.


CUptiResult cuptiProfilerInitialize(

CUpti_Profiler_Initialize_Params *pParams,

)
Initializes the profiler interface.
Loads the required libraries in the process address space. Sets up the hooks with the CUDA driver.


CUptiResult cuptiProfilerIsPassCollected(

CUpti_Profiler_IsPassCollected_Params *pParams,

)
Asynchronous call to query if the submitted pass to GPU is collected.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerPopRange(

CUpti_Profiler_PopRange_Params *pParams,

)
Range API’s : Pop user range.
Counter data is collected per unique range-stack. Identified by a string label passsed by the user. It’s an invalid operation in case of CUPTI_AutoRange.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerPushRange(

CUpti_Profiler_PushRange_Params *pParams,

)
Range API’s : Push user range.
Counter data is collected per unique range-stack. Identified by a string label passsed by the user. It’s an invalid operation in case of CUPTI_AutoRange.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerSetConfig(

CUpti_Profiler_SetConfig_Params *pParams,

)
Set metrics configuration to be profiled.
Use these APIs to set the config to profile in a session. It can be used for advanced cases such as where multiple configurations are collected into a single CounterData Image on the need basis, without restarting the session.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.


CUptiResult cuptiProfilerUnsetConfig(

CUpti_Profiler_UnsetConfig_Params *pParams,

)
Unset metrics configuration profiled.
DEPRECATED This function is deprecated as of CUDA 13.0 and will be removed in the future. It is recommended to use the Range Profiling API from the header cupti_range_profiler.h.