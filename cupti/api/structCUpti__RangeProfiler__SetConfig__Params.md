# 7.185. CUpti_RangeProfiler_SetConfig_Params


struct CUpti_RangeProfiler_SetConfig_Params
Params for cuptiRangeProfilerSetConfig.

Public Members

size_t structSize
[in] Size of the data structure.

void *pPriv
[in] Set to NULL.

CUpti_RangeProfiler_Object *pRangeProfilerObject
[in] Range Profiler Object.

size_t configSize
[in] Size of the config image.

const uint8_t *pConfig
[in] Config image.

size_t counterDataImageSize
[in] Size of the counter data image.

uint8_t *pCounterDataImage
[in] Counter data image.

CUpti_ProfilerRange range
[in] Profiling Range mode.

CUpti_ProfilerReplayMode replayMode
[in] Replay mode.

size_t maxRangesPerPass
[in] Maximum number of ranges that can be profiled in a pass.

uint16_t numNestingLevels
[in] number of nesting level to be profiled. For Auto range mode, this should be set to 1.

uint16_t minNestingLevel
[in] minimum nesting level to be profiled.

size_t passIndex
[in] Pass index for the replay session.

uint16_t targetNestingLevel
[in] Target nesting level for the replay session.