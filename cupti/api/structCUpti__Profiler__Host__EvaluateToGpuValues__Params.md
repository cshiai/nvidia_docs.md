# 7.159. CUpti_Profiler_Host_EvaluateToGpuValues_Params


struct CUpti_Profiler_Host_EvaluateToGpuValues_Params
Params for cuptiProfilerHostEvaluateToGpuValues.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Assign to NULL

CUpti_Profiler_Host_Object *pHostObject
[in] reference to the profiler host object allocated by CUPTI in cuptiProfilerHostInitialize

const uint8_t *pCounterDataImage
[in] the counter data image where profiling data has been decoded

size_t counterDataImageSize
[in] size of counter data image

size_t rangeIndex
[in] range index for which the range name will be queried

const char ppMetricNames
[in] the metrics for which GPU values will be evaluated for the range

size_t numMetrics
[in] number of metrics

double *pMetricValues
[out] output value for given metric and range index