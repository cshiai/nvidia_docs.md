# 7.191. CUpti_SassMetricsFlushData_Params


struct CUpti_SassMetricsFlushData_Params
Params for cuptiSassMetricsFlushData.

Public Members

size_t structSize
[in] equal to CUpti_SassMetricsFlushData_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUcontext ctx
[in] CUDA context on which SASS metric data collection was enabled. If set NULL, default context will be consider for SASS metric data collection.

size_t numOfPatchedInstructionRecords
[in] number of patched instruction record will be retrived, user can call cuptiSassMetricsGetDataProperties() for getting total number of records available.

size_t numOfInstances
[in] number of patched instruction record instances for a metric, user can call cuptiSassMetricsGetDataProperties() for getting total number of instances for each record per metric available.

CUpti_SassMetrics_Data *pMetricsData
[out]