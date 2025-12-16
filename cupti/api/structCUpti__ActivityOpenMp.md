# 7.91. CUpti_ActivityOpenMp


struct CUpti_ActivityOpenMp
The base activity record for OpenMp records.

See also
CUpti_ActivityKind

Public Members

CUpti_ActivityKind kind
The kind of this activity.

CUpti_OpenMpEventKind eventKind
CUPTI OpenMP event kind (.

See also
CUpti_OpenMpEventKind)

uint32_t version
Version number.

uint32_t threadId
ThreadId.

uint64_t start
CUPTI start timestamp.

uint64_t end
CUPTI end timestamp.

uint32_t cuProcessId
The ID of the process where the OpenMP activity is executing.

uint32_t cuThreadId
The ID of the thread where the OpenMP activity is executing.