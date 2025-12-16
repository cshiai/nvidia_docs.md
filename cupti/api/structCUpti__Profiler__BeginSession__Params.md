# 7.143. CUpti_Profiler_BeginSession_Params


struct CUpti_Profiler_BeginSession_Params
Params for cuptiProfilerBeginSession.

Public Members

size_t structSize
[in] CUpti_Profiler_BeginSession_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUcontext ctx
[in] if NULL, the current CUcontext is used

size_t counterDataImageSize
[in] size calculated from cuptiProfilerCounterDataImageCalculateSize

uint8_t *pCounterDataImage
[in] address of CounterDataImage

size_t counterDataScratchBufferSize
[in] size calculated from cuptiProfilerCounterDataImageInitializeScratchBuffer

uint8_t *pCounterDataScratchBuffer
[in] address of CounterDataImage scratch buffer

uint8_t bDumpCounterDataInFile
[in] [optional]

const char *pCounterDataFilePath
[in] [optional]

CUpti_ProfilerRange range
[in] CUpti_ProfilerRange

CUpti_ProfilerReplayMode replayMode
[in] CUpti_ProfilerReplayMode

size_t maxRangesPerPass
[in] Maximum number of ranges that can be recorded in a single pass.

size_t maxLaunchesPerPass
[in] Maximum number of kernel launches that can be recorded in a single pass; must be >= maxRangesPerPass.