# 7.163. CUpti_Profiler_Host_GetMaxNumHardwareMetricsPerPass_Params


struct CUpti_Profiler_Host_GetMaxNumHardwareMetricsPerPass_Params
Params for cuptiProfilerHostGetMaxNumHardwareMetricsPerPass.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Assign to NULL

CUpti_ProfilerType profilerType
[in] the profiler kind one from CUpti_ProfilerType

const char *pChipName
[in] accepted for chips supported at the time-of-release.

uint8_t *pCounterAvailabilityImage
[in] buffer with counter availability image - required for future chip support

size_t maxMetricsPerPass
[out] maximum number of metrics that can be scheduled in a pass