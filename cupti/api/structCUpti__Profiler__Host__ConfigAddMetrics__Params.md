# 7.157. CUpti_Profiler_Host_ConfigAddMetrics_Params


struct CUpti_Profiler_Host_ConfigAddMetrics_Params
Params for cuptiProfilerHostConfigAddMetrics.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Assign to NULL

struct CUpti_Profiler_Host_Object *pHostObject
[in] reference to the profiler host object allocated by CUPTI in cuptiProfilerHostInitialize

const char ppMetricNames
[in] metric names for which config image will be generated

size_t numMetrics
[in] number of metrics