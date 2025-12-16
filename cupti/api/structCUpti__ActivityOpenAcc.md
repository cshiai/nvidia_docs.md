# 7.87. CUpti_ActivityOpenAcc


struct CUpti_ActivityOpenAcc
The base activity record for OpenAcc records.
The OpenACC activity API part uses a CUpti_ActivityOpenAcc as a generic representation for any OpenACC activity. The ‘kind’ field is used to determine the specific activity kind, and from that the CUpti_ActivityOpenAcc object can be cast to the specific OpenACC activity record type appropriate for that kind.
Note that all OpenACC activity record types are padded and aligned to ensure that each member of the record is naturally aligned.

See also
CUpti_ActivityKind

Public Members

CUpti_ActivityKind kind
The kind of this activity.

CUpti_OpenAccEventKind eventKind
CUPTI OpenACC event kind (.

See also
CUpti_OpenAccEventKind)

CUpti_OpenAccConstructKind parentConstruct
CUPTI OpenACC parent construct kind (.

Note that for applications using PGI OpenACC runtime < 16.1, this will always be CUPTI_OPENACC_CONSTRUCT_KIND_UNKNOWN.
See also
CUpti_OpenAccConstructKind)

uint32_t version
Version number.

uint32_t implicit
1 for any implicit event, such as an implicit wait at a synchronous data construct 0 otherwise

uint32_t deviceType
Device type.

uint32_t deviceNumber
Device number.

uint32_t threadId
ThreadId.

uint64_t async
Value of async() clause of the corresponding directive.

uint64_t asyncMap
Internal asynchronous queue number used.

uint32_t lineNo
The line number of the directive or program construct or the starting line number of the OpenACC construct corresponding to the event.
A zero value means the line number is not known.

uint32_t endLineNo
For an OpenACC construct, this contains the line number of the end of the construct.
A zero value means the line number is not known.

uint32_t funcLineNo
The line number of the first line of the function named in funcName.
A zero value means the line number is not known.

uint32_t funcEndLineNo
The last line number of the function named in funcName.
A zero value means the line number is not known.

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