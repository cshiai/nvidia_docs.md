# 7.189. CUpti_SassMetricsDisable_Params


struct CUpti_SassMetricsDisable_Params
Params for cuptiSassMetricsDisable.

Public Members

size_t structSize
[in] equal to CUpti_SassMetricsDisable_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUcontext ctx
[in] CUDA context on which SASS metric data collection will be disabled. If set NULL, default context will be consider for SASS metric data collection.

size_t numOfDroppedRecords
[out] Num of dropped SASS records will be equal to numOfPatchedInstructions * numOfInstances. Number of dropped records will be zero when data is flushed prior to calling the disable API.