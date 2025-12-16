# 7.158. CUpti_Profiler_Host_Deinitialize_Params


struct CUpti_Profiler_Host_Deinitialize_Params
Params for cuptiProfilerHostDeinitialize.

Public Members

size_t structSize
[in] Size of the data structure. CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

void *pPriv
[in] Assign to NULL

struct CUpti_Profiler_Host_Object *pHostObject
[in] reference to the profiler host object allocated by CUPTI in cuptiProfilerHostInitialize