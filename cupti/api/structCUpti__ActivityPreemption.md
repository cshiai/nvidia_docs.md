# 7.102. CUpti_ActivityPreemption


struct CUpti_ActivityPreemption
The activity record for a preemption of a CDP kernel.
This activity record represents a preemption of a CDP kernel.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_PREEMPTION.

CUpti_ActivityPreemptionKind preemptionKind
kind of the preemption

uint64_t timestamp
The timestamp of the preemption, in ns.
A value of 0 indicates that timestamp information could not be collected for the preemption.

int64_t gridId
The grid-id of the block that is preempted.

uint32_t blockX
The X-dimension of the block that is preempted.

uint32_t blockY
The Y-dimension of the block that is preempted.

uint32_t blockZ
The Z-dimension of the block that is preempted.

uint32_t pad
Undefined.
Reserved for internal use.