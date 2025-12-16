# 7.169. CUpti_Profiler_Host_Initialize_Params


struct CUpti_Profiler_Host_Initialize_Params
Params for cuptiProfilerHostInitialize.

Public Members

size_t structSize
[in] Size of the data structure. CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

void *pPriv
[in] Assign to NULL

CUpti_ProfilerType profilerType
[in] the profiler kind one from CUpti_ProfilerType

const char *pChipName
[in] accepted for chips supported at the time-of-release.

const uint8_t *pCounterAvailabilityImage
[in] buffer with counter availability image - required for future chip support

CUpti_Profiler_Host_Object *pHostObject
[out] binary blob allocated by CUPTI and operations associated with this object.