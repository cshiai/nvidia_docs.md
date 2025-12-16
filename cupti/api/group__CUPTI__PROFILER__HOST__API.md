# 6.7. CUPTI Profiler Host API


Functions, types, and enums that implement the CUPTI Profiler Host API.


## 6.7.1. Data Structures


CUpti_Profiler_Host_ConfigAddMetrics_Params
Params for cuptiProfilerHostConfigAddMetrics.

CUpti_Profiler_Host_Deinitialize_Params
Params for cuptiProfilerHostDeinitialize.

CUpti_Profiler_Host_EvaluateToGpuValues_Params
Params for cuptiProfilerHostEvaluateToGpuValues.

CUpti_Profiler_Host_GetBaseMetrics_Params
Params for cuptiProfilerHostGetSupportedMetrics.

CUpti_Profiler_Host_GetConfigImageSize_Params
Params for cuptiProfilerHostGetConfigImageSize.

CUpti_Profiler_Host_GetConfigImage_Params
Params for cuptiProfilerHostGetConfigImage.

CUpti_Profiler_Host_GetMaxNumHardwareMetricsPerPass_Params
Params for cuptiProfilerHostGetMaxNumHardwareMetricsPerPass.

CUpti_Profiler_Host_GetMetricProperties_Params
Params for cuptiProfilerHostGetMetricProperties.

CUpti_Profiler_Host_GetNumOfPasses_Params
Params for cuptiProfilerHostGetNumOfPasses.

CUpti_Profiler_Host_GetRangeName_Params
Params for cuptiProfilerHostGetRangeName.

CUpti_Profiler_Host_GetSubMetrics_Params
Params for cuptiProfilerHostGetSubMetrics.

CUpti_Profiler_Host_GetSupportedChips_Params
Params for cuptiProfilerHostGetSupportedChips.

CUpti_Profiler_Host_Initialize_Params
Params for cuptiProfilerHostInitialize.


## 6.7.2. Macros


CUpti_Profiler_Host_ConfigAddMetrics_Params_STRUCT_SIZECUpti_Profiler_Host_Deinitialize_Params_STRUCT_SIZECUpti_Profiler_Host_EvaluateToGpuValues_Params_STRUCT_SIZECUpti_Profiler_Host_GetBaseMetrics_Params_STRUCT_SIZECUpti_Profiler_Host_GetConfigImageSize_Params_STRUCT_SIZECUpti_Profiler_Host_GetConfigImage_Params_STRUCT_SIZECUpti_Profiler_Host_GetMaxNumHardwareMetricsPerPass_Params_STRUCT_SIZECUpti_Profiler_Host_GetMetricProperties_Params_STRUCT_SIZECUpti_Profiler_Host_GetNumOfPasses_Params_STRUCT_SIZECUpti_Profiler_Host_GetRangeName_Params_STRUCT_SIZECUpti_Profiler_Host_GetSubMetrics_Params_STRUCT_SIZECUpti_Profiler_Host_GetSupportedChips_Params_STRUCT_SIZECUpti_Profiler_Host_Initialize_Params_STRUCT_SIZE

## 6.7.3. Enumerations


CUpti_MetricCollectionScopeCUpti_MetricTypeCUpti_ProfilerType

## 6.7.4. Functions


CUptiResult cuptiProfilerHostConfigAddMetrics(CUpti_Profiler_Host_ConfigAddMetrics_Params *pParams)
Add the metrics to the profiler host object for generating the config image.

CUptiResult cuptiProfilerHostDeinitialize(CUpti_Profiler_Host_Deinitialize_Params *pParams)
Deinitialize and destroy the profiler host object (CUpti_Profiler_Host_Object).

CUptiResult cuptiProfilerHostEvaluateToGpuValues(CUpti_Profiler_Host_EvaluateToGpuValues_Params *pParams)
Evaluate the metric values for the range index stored in the counter data.

CUptiResult cuptiProfilerHostGetBaseMetrics(CUpti_Profiler_Host_GetBaseMetrics_Params *pParams)
Get the list of supported base metrics for the chip.

CUptiResult cuptiProfilerHostGetConfigImage(CUpti_Profiler_Host_GetConfigImage_Params *pParams)
Get the config image for the metrics added to the profiler host object.

CUptiResult cuptiProfilerHostGetConfigImageSize(CUpti_Profiler_Host_GetConfigImageSize_Params *pParams)
Get the size of the config image for the metrics added to the profiler host object.

CUptiResult cuptiProfilerHostGetMaxNumHardwareMetricsPerPass(CUpti_Profiler_Host_GetMaxNumHardwareMetricsPerPass_Params *pParams)
Get the maximum number of hardware metrics (metric names which doesn't include sass keyword) that can be scheduled in a single pass for a chip.

CUptiResult cuptiProfilerHostGetMetricProperties(CUpti_Profiler_Host_GetMetricProperties_Params *pParams)
Get the properties of the metric.

CUptiResult cuptiProfilerHostGetNumOfPasses(CUpti_Profiler_Host_GetNumOfPasses_Params *pParams)
Get the number of passes required for profiling the scheduled metrics in the config image.

CUptiResult cuptiProfilerHostGetRangeName(CUpti_Profiler_Host_GetRangeName_Params *pParams)
Get the range name for the range index stored in the counter data.

CUptiResult cuptiProfilerHostGetSubMetrics(CUpti_Profiler_Host_GetSubMetrics_Params *pParams)
Get the list of supported sub-metrics for the metric.

CUptiResult cuptiProfilerHostGetSupportedChips(CUpti_Profiler_Host_GetSupportedChips_Params *pParams)
Get the list of supported chips.

CUptiResult cuptiProfilerHostInitialize(CUpti_Profiler_Host_Initialize_Params *pParams)
Create and initialize the profiler host object (CUpti_Profiler_Host_Object).


## 6.7.5. Typedefs


CUpti_Profiler_Host_Object

## 6.7.6. Macros


CUpti_Profiler_Host_ConfigAddMetrics_Params_STRUCT_SIZECUpti_Profiler_Host_Deinitialize_Params_STRUCT_SIZECUpti_Profiler_Host_EvaluateToGpuValues_Params_STRUCT_SIZECUpti_Profiler_Host_GetBaseMetrics_Params_STRUCT_SIZECUpti_Profiler_Host_GetConfigImageSize_Params_STRUCT_SIZECUpti_Profiler_Host_GetConfigImage_Params_STRUCT_SIZECUpti_Profiler_Host_GetMaxNumHardwareMetricsPerPass_Params_STRUCT_SIZECUpti_Profiler_Host_GetMetricProperties_Params_STRUCT_SIZECUpti_Profiler_Host_GetNumOfPasses_Params_STRUCT_SIZECUpti_Profiler_Host_GetRangeName_Params_STRUCT_SIZECUpti_Profiler_Host_GetSubMetrics_Params_STRUCT_SIZECUpti_Profiler_Host_GetSupportedChips_Params_STRUCT_SIZECUpti_Profiler_Host_Initialize_Params_STRUCT_SIZE

## 6.7.7. Enumerations


enum CUpti_MetricCollectionScope
Values:

enumerator CUPTI_METRIC_COLLECTION_SCOPE_CONTEXT

enumerator CUPTI_METRIC_COLLECTION_SCOPE_DEVICE

enumerator CUPTI_METRIC_COLLECTION_SCOPE_INVALID


enum CUpti_MetricType
Values:

enumerator CUPTI_METRIC_TYPE_COUNTER

enumerator CUPTI_METRIC_TYPE_RATIO

enumerator CUPTI_METRIC_TYPE_THROUGHPUT

enumerator CUPTI_METRIC_TYPE__COUNT


enum CUpti_ProfilerType
Values:

enumerator CUPTI_PROFILER_TYPE_RANGE_PROFILER

enumerator CUPTI_PROFILER_TYPE_PM_SAMPLING

enumerator CUPTI_PROFILER_TYPE_PROFILER_INVALID


## 6.7.8. Functions


CUptiResult cuptiProfilerHostConfigAddMetrics(

CUpti_Profiler_Host_ConfigAddMetrics_Params *pParams,

)
Add the metrics to the profiler host object for generating the config image.
The config image will have the required information to schedule the metrics for collecting the profiling data. Note: PM sampling only supports single pass config image.

Parameters:
pParams – A pointer to CUpti_Profiler_Host_ConfigAddMetrics_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_METRIC_NAME – if the metric name is not valid or not supported for the chip
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiProfilerHostDeinitialize(

CUpti_Profiler_Host_Deinitialize_Params *pParams,

)
Deinitialize and destroy the profiler host object (CUpti_Profiler_Host_Object).

Parameters:
pParams – A pointer to CUpti_Profiler_Host_Deinitialize_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiProfilerHostEvaluateToGpuValues(

CUpti_Profiler_Host_EvaluateToGpuValues_Params *pParams,

)
Evaluate the metric values for the range index stored in the counter data.

Parameters:
pParams – A pointer to CUpti_Profiler_Host_EvaluateToGpuValues_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_METRIC_NAME – if the metric name is not valid or not supported for the chip
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiProfilerHostGetBaseMetrics(

CUpti_Profiler_Host_GetBaseMetrics_Params *pParams,

)
Get the list of supported base metrics for the chip.

Parameters:
pParams – A pointer to CUpti_Profiler_Host_GetBaseMetrics_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiProfilerHostGetConfigImage(

CUpti_Profiler_Host_GetConfigImage_Params *pParams,

)
Get the config image for the metrics added to the profiler host object.
User will pass the allocated buffer to store the config image.

Parameters:
pParams – A pointer to CUpti_Profiler_Host_GetConfigImage_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiProfilerHostGetConfigImageSize(

CUpti_Profiler_Host_GetConfigImageSize_Params *pParams,

)
Get the size of the config image for the metrics added to the profiler host object.
Users need to allocate the buffer for storing the config image.

Parameters:
pParams – A pointer to CUpti_Profiler_Host_GetConfigImageSize_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiProfilerHostGetMaxNumHardwareMetricsPerPass(

CUpti_Profiler_Host_GetMaxNumHardwareMetricsPerPass_Params *pParams,

)
Get the maximum number of hardware metrics (metric names which doesn’t include sass keyword) that can be scheduled in a single pass for a chip.
While this represents a theoretical upper limit, practical constraints may prevent reaching this threshold for a specific set of metrics. Furthermore, the maximum achievable value is contingent upon the characteristics and architecture of the chip in question.
Use cuptiProfilerHostGetNumOfPasses API for getting the actual number of passes required for the for collecting the profiling data for the scheduled metrics in a config image.

Parameters:
pParams – A pointer to CUpti_Profiler_Host_GetMaxNumHardwareMetricsPerPass_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiProfilerHostGetMetricProperties(

CUpti_Profiler_Host_GetMetricProperties_Params *pParams,

)
Get the properties of the metric.

Parameters:
pParams – A pointer to CUpti_Profiler_Host_GetMetricProperties_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_METRIC_NAME – if the metric name is not valid or not supported for the chip
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiProfilerHostGetNumOfPasses(

CUpti_Profiler_Host_GetNumOfPasses_Params *pParams,

)
Get the number of passes required for profiling the scheduled metrics in the config image.

Parameters:
pParams – A pointer to CUpti_Profiler_Host_GetNumOfPasses_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiProfilerHostGetRangeName(

CUpti_Profiler_Host_GetRangeName_Params *pParams,

)
Get the range name for the range index stored in the counter data.
In Range profiler, for Auto range mode the range name will be numeric value assigned to the kernel based on execution order. For user range mode, the name of range will be based on the range name provided by the user using Push range API.

Parameters:
pParams – A pointer to CUpti_Profiler_Host_GetRangeName_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiProfilerHostGetSubMetrics(

CUpti_Profiler_Host_GetSubMetrics_Params *pParams,

)
Get the list of supported sub-metrics for the metric.

Parameters:
pParams – A pointer to CUpti_Profiler_Host_GetSubMetrics_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_METRIC_NAME – if the metric name is not valid or not supported for the chip
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiProfilerHostGetSupportedChips(

CUpti_Profiler_Host_GetSupportedChips_Params *pParams,

)
Get the list of supported chips.

Parameters:
pParams – A pointer to CUpti_Profiler_Host_GetSupportedChips_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


CUptiResult cuptiProfilerHostInitialize(

CUpti_Profiler_Host_Initialize_Params *pParams,

)
Create and initialize the profiler host object (CUpti_Profiler_Host_Object).

Parameters:
pParams – A pointer to CUpti_Profiler_Host_Initialize_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_UNKNOWN – for any internal error


## 6.7.9. Typedefs


typedef struct CUpti_Profiler_Host_Object CUpti_Profiler_Host_Object