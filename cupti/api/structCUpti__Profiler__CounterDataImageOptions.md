# 7.144. CUpti_Profiler_CounterDataImageOptions


struct CUpti_Profiler_CounterDataImageOptions
Input parameter to define the counterDataImage.

Public Members

size_t structSize
[in] CUpti_Profiler_CounterDataImageOptions_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

const uint8_t *pCounterDataPrefix
[in] Address of CounterDataPrefix generated from NVPW_CounterDataBuilder_GetCounterDataPrefix().
Must be align(8).

size_t counterDataPrefixSize
[in] Size of CounterDataPrefix generated from NVPW_CounterDataBuilder_GetCounterDataPrefix().

uint32_t maxNumRanges
[in] Maximum number of ranges that can be profiled

uint32_t maxNumRangeTreeNodes
[in] Maximum number of RangeTree nodes; must be >= maxNumRanges

uint32_t maxRangeNameLength
[in] Maximum string length of each RangeName, including the trailing NULL character