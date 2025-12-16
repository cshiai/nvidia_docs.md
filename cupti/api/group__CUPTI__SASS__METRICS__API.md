# 6.11. CUPTI SASS Metrics API


Functions, types, and enums that implement the CUPTI SASS Metrics API.


## 6.11.1. Data Structures


CUpti_SassMetricsDisable_Params
Params for cuptiSassMetricsDisable.

CUpti_SassMetricsEnable_Params
Params for cuptiSassMetricsEnable.

CUpti_SassMetricsFlushData_Params
Params for cuptiSassMetricsFlushData.

CUpti_SassMetricsGetDataProperties_Params
Params for cuptiSassMetricsGetDataProperties.

CUpti_SassMetricsSetConfig_Params
Params for cuptiSassMetricsSetConfig.

CUpti_SassMetricsUnsetConfig_Params
Params for cuptiSassMetricsUnsetConfig.

CUpti_SassMetrics_ConfigCUpti_SassMetrics_DataCUpti_SassMetrics_GetMetrics_Params
Params for cuptiSassMetricsGetMetrics.

CUpti_SassMetrics_GetNumOfMetrics_Params
Params for cuptiSassMetricsGetNumOfMetrics.

CUpti_SassMetrics_GetProperties_Params
Params for cuptiSassMetricsGetProperties.

CUpti_SassMetrics_InstanceValueCUpti_SassMetrics_MetricDetails

## 6.11.2. Macros


CUpti_SassMetricsDisable_Params_STRUCT_SIZECUpti_SassMetricsEnable_Params_STRUCT_SIZECUpti_SassMetricsFlushData_Params_STRUCT_SIZECUpti_SassMetricsGetDataProperties_Params_STRUCT_SIZECUpti_SassMetricsSetConfig_Params_STRUCT_SIZECUpti_SassMetricsUnsetConfig_Params_STRUCT_SIZECUpti_SassMetrics_GetMetrics_Params_STRUCT_SIZECUpti_SassMetrics_GetNumOfMetrics_Params_STRUCT_SIZECUpti_SassMetrics_GetProperties_Params_STRUCT_SIZECUpti_SassMetrics_InstanceValue_STRUCT_SIZE

## 6.11.3. Enumerations


CUpti_SassMetrics_OutputGranularity

## 6.11.4. Functions


CUptiResult cuptiSassMetricsDisable(CUpti_SassMetricsDisable_Params *pParams)
SASS metric data collection disable API will mark the end of a range, any kernel launched after this API call will not be profiled for the SASS metrics.

CUptiResult cuptiSassMetricsEnable(CUpti_SassMetricsEnable_Params *pParams)
Sass metric data collection enable API will mark the start of a range, between which kernel will be profiled for SASS metrics.

CUptiResult cuptiSassMetricsFlushData(CUpti_SassMetricsFlushData_Params *pParams)
Flush SASS metrics data from CUPTI internal buffer to the user buffer.

CUptiResult cuptiSassMetricsGetDataProperties(CUpti_SassMetricsGetDataProperties_Params *pParams)
SASS metric data properties API will give the data regarding number of instances of a metric value and number of SASS instruction data has been collected.

CUptiResult cuptiSassMetricsGetMetrics(CUpti_SassMetrics_GetMetrics_Params *pParams)
Get the list of all supported SASS metrics for the chip.

CUptiResult cuptiSassMetricsGetNumOfMetrics(CUpti_SassMetrics_GetNumOfMetrics_Params *pParams)
Get the number of supported SASS metrics for the chip.

CUptiResult cuptiSassMetricsGetProperties(CUpti_SassMetrics_GetProperties_Params *pParams)
Get metric properties for the queried metric.

CUptiResult cuptiSassMetricsSetConfig(CUpti_SassMetricsSetConfig_Params *pParams)
Set config for the SASS metric data collection for a device.

CUptiResult cuptiSassMetricsUnsetConfig(CUpti_SassMetricsUnsetConfig_Params *pParams)
Unset config API will reset the SASS metric data collection configuration for the device.


## 6.11.5. Macros


CUpti_SassMetricsDisable_Params_STRUCT_SIZECUpti_SassMetricsEnable_Params_STRUCT_SIZECUpti_SassMetricsFlushData_Params_STRUCT_SIZECUpti_SassMetricsGetDataProperties_Params_STRUCT_SIZECUpti_SassMetricsSetConfig_Params_STRUCT_SIZECUpti_SassMetricsUnsetConfig_Params_STRUCT_SIZECUpti_SassMetrics_GetMetrics_Params_STRUCT_SIZECUpti_SassMetrics_GetNumOfMetrics_Params_STRUCT_SIZECUpti_SassMetrics_GetProperties_Params_STRUCT_SIZECUpti_SassMetrics_InstanceValue_STRUCT_SIZE

## 6.11.6. Enumerations


enum CUpti_SassMetrics_OutputGranularity
Values:

enumerator CUPTI_SASS_METRICS_OUTPUT_GRANULARITY_GPU
SASS metric data will be collected at GPU level. In CUpti_SassMetricsGetDataProperties_Params struct the numOfInstances will be equal to 1.

enumerator CUPTI_SASS_METRICS_OUTPUT_GRANULARITY_SM
SASS metric data will be collected at SM level In CUpti_SassMetricsGetDataProperties_Params struct the numOfInstances will be equal to number of SMs in the GPU.

enumerator CUPTI_SASS_METRICS_OUTPUT_GRANULARITY_SMSP
SASS metric data will be collected at SM sub-partition level In CUpti_SassMetricsGetDataProperties_Params struct the numOfInstances will be equal to number of SM sub-partitions in the GPU.

enumerator CUPTI_SASS_METRICS_OUTPUT_GRANULARITY_INVALID


## 6.11.7. Functions


CUptiResult cuptiSassMetricsDisable(

CUpti_SassMetricsDisable_Params *pParams,

)
SASS metric data collection disable API will mark the end of a range, any kernel launched after this API call will not be profiled for the SASS metrics.

Parameters:
pParams – A pointer to CUpti_SassMetricsDisable_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device doesn’t support SASS metric data collection
CUPTI_ERROR_INVALID_CONTEXT – if any cuda context has not been created prior to this API call
CUPTI_ERROR_INVALID_OPERATION – if this API is called multiple times for a cuda context without calling cuptiSassMetricsEnable() API or called before cuptiSassMetricsSetConfig() API call.


CUptiResult cuptiSassMetricsEnable(

CUpti_SassMetricsEnable_Params *pParams,

)
Sass metric data collection enable API will mark the start of a range, between which kernel will be profiled for SASS metrics.

Parameters:
pParams – A pointer to CUpti_SassMetricsEnable_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device doesn’t support SASS metric data collection
CUPTI_ERROR_INVALID_CONTEXT – if any cuda context has not been created prior to this API call
CUPTI_ERROR_INVALID_OPERATION – if this API is called multiple times for a cuda context without calling cuptiSassMetricsDisable() API or called before cuptiSassMetricsSetConfig() API call.


CUptiResult cuptiSassMetricsFlushData(

CUpti_SassMetricsFlushData_Params *pParams,

)
Flush SASS metrics data from CUPTI internal buffer to the user buffer.
User needs to allocate the buffer for retrieving the data. The number of records collected can be queried using the API cuptiSassMetricsGetDataProperties().

Parameters:
pParams – A pointer to CUpti_SassMetricsFlushData_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device doesn’t support SASS metric data collection.
CUPTI_ERROR_INVALID_OPERATION – if this API is called outside the enable/disable range.


CUptiResult cuptiSassMetricsGetDataProperties(

CUpti_SassMetricsGetDataProperties_Params *pParams,

)
SASS metric data properties API will give the data regarding number of instances of a metric value and number of SASS instruction data has been collected.
The number of instances of a metric will vary as per user set the output granularity level with CUpti_SassMetrics_OutputGranularity value. User need to allocate memory for retriving the SASS data using cuptiSassMetricsFlushData() API.

Parameters:
pParams – A pointer to CUpti_SassMetricsGetDataProperties_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device doesn’t support SASS metric data collection
CUPTI_ERROR_INVALID_OPERATION – if this API is called outside the enable/disable range.


CUptiResult cuptiSassMetricsGetMetrics(

CUpti_SassMetrics_GetMetrics_Params *pParams,

)
Get the list of all supported SASS metrics for the chip.

Parameters:
pParams – A pointer to CUpti_SassMetrics_GetMetrics_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device doesn’t support SASS metric collection


CUptiResult cuptiSassMetricsGetNumOfMetrics(

CUpti_SassMetrics_GetNumOfMetrics_Params *pParams,

)
Get the number of supported SASS metrics for the chip.

Parameters:
pParams – A pointer to CUpti_SassMetrics_GetNumOfMetrics_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device doesn’t support SASS metric collection


CUptiResult cuptiSassMetricsGetProperties(

CUpti_SassMetrics_GetProperties_Params *pParams,

)
Get metric properties for the queried metric.
For a given metric the results will be put in CUpti_SassMetrics_MetricDetails which stores metric ID, description of the metric.

Parameters:
pParams – A pointer to CUpti_SassMetrics_GetProperties_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device doesn’t support SASS metric data collection


CUptiResult cuptiSassMetricsSetConfig(

CUpti_SassMetricsSetConfig_Params *pParams,

)
Set config for the SASS metric data collection for a device.
User need to call this API before calling any of the SASS metric data collection APIs. Each set config API call need to be followed by cuptiSassPatchingUnSetConfig API before calling the cuptiSassMetricsSetConfig() API again for the same device.

Parameters:
pParams – A pointer to CUpti_SassMetricsSetConfig_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_CONTEXT – if any cuda context has not been created prior to this API call
CUPTI_ERROR_INVALID_OPERATION – if this is called multiple times for the device without calling unset config API
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device doesn’t support SASS metric data collection


CUptiResult cuptiSassMetricsUnsetConfig(

CUpti_SassMetricsUnsetConfig_Params *pParams,

)
Unset config API will reset the SASS metric data collection configuration for the device.
Once this API called CUPTI will deallocate all the memory allocated and remove all the configuration for SASS metric data collection. User can only call this API for a device where cuptiSassMetricsSetConfig() API has been called earlier for the device.

Parameters:
pParams – A pointer to CUpti_SassMetricsSetConfig_Params

Return values:

CUPTI_SUCCESS –
CUPTI_ERROR_INVALID_PARAMETER – if any pParams is not valid
CUPTI_ERROR_INVALID_CONTEXT – if any cuda context has not been created prior to this API call
CUPTI_ERROR_INVALID_OPERATION – if this is called multiple times for the device without calling set config API
CUPTI_ERROR_NOT_SUPPORTED – indicates that the system/device doesn’t support SASS metric data collection