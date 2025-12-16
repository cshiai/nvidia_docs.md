# 7.192. CUpti_SassMetricsGetDataProperties_Params


struct CUpti_SassMetricsGetDataProperties_Params
Params for cuptiSassMetricsGetDataProperties.

Public Members

size_t structSize
[in] equal to CUpti_SassMetricsGetDataProperties_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUcontext ctx
[in] CUDA context on which SASS metric data collection was enabled. If set NULL, default context will be consider for SASS metric data collection.

size_t numOfPatchedInstructionRecords
[out] total number of SASS records has been collected

size_t numOfInstances
[out] number of instances for each metric value per instruction. This will depend on CUpti_SassPatching_OutputGranularity level set for the metric config.