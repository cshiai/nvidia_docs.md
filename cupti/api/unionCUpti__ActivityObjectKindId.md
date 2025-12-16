# 7.86. CUpti_ActivityObjectKindId


union CUpti_ActivityObjectKindId
#include </dvs/p4/build/sw/devtools/Agora/Rel/CUDA13.1/Built/Int/rel-pub/linux-desktop-glibc_2_11_3-x64/Shared/Cuda/Modules/Cupti/Inc/cupti_activity.h>
Identifiers for object kinds as specified by CUpti_ActivityObjectKind.

See also
CUpti_ActivityObjectKind

Public Members

uint32_t processId

uint32_t threadId

struct CUpti_ActivityObjectKindId::[anonymous] pt
A process object requires that we identify the process ID.
A thread object requires that we identify both the process and thread ID.

uint32_t deviceId

uint32_t contextId

uint32_t streamId

struct CUpti_ActivityObjectKindId::[anonymous] dcs
A device object requires that we identify the device ID.
A context object requires that we identify both the device and context ID. A stream object requires that we identify device, context, and stream ID.