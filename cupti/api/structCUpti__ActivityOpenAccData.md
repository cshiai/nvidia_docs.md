# 7.88. CUpti_ActivityOpenAccData


struct CUpti_ActivityOpenAccData
The activity record for OpenACC data.
(CUPTI_ACTIVITY_KIND_OPENACC_DATA).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_OPENACC_DATA.

CUpti_OpenAccEventKind eventKind
CUPTI OpenACC event kind (.

See also
CUpti_OpenAccEventKind)

uint32_t threadId
ThreadId.

uint64_t start
CUPTI start timestamp.

uint64_t end
CUPTI end timestamp.

uint32_t cuDeviceId
CUDA device id Valid only if deviceType is acc_device_nvidia.

uint32_t cuContextId
CUDA context id Valid only if deviceType is acc_device_nvidia.

uint32_t cuStreamId
CUDA stream id Valid only if deviceType is acc_device_nvidia.

uint32_t cuProcessId
The ID of the process where the OpenACC activity is executing.

uint32_t cuThreadId
The ID of the thread where the OpenACC activity is executing.

uint32_t externalId
The OpenACC correlation ID.
Valid only if deviceType is acc_device_nvidia. If not 0, it uniquely identifies this record. It is identical to the externalId in the preceding external correlation record of type CUPTI_EXTERNAL_CORRELATION_KIND_OPENACC.

uint64_t bytes
Number of bytes.

uint64_t hostPtr
Host pointer if available.

uint64_t devicePtr
Device pointer if available.