# 7.196. CUpti_SassMetrics_Data


struct CUpti_SassMetrics_Data
Public Members

size_t structSize
[in] equal to CUpti_SassMetricsFlushData_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

uint32_t cubinCrc
[out] Unique cubin id

uint32_t functionIndex
[out] function’s unique symbol index in the module.

const char *functionName
[out] The function name

uint32_t pcOffset
[out] pc offset for the function in a module

CUpti_SassMetrics_InstanceValue *pInstanceValues
[out] array of size equal to number of instances per metric, which contains the metric ID and metric value.