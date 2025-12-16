# 7.5. CUpti_ActivityBranch2


struct CUpti_ActivityBranch2
The activity record for source level result branch.
This activity record the locations of the branches in the source (CUPTI_ACTIVITY_KIND_BRANCH).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_BRANCH.

uint32_t sourceLocatorId
The ID for source locator.

uint32_t correlationId
The correlation ID of the kernel to which this result is associated.

uint32_t functionId
Correlation ID with global/device function name.

uint32_t pcOffset
The pc offset for the branch.

uint32_t diverged
Number of times this branch diverged.

uint64_t threadsExecuted
This increments each time when this instruction is executed by number of threads that executed this instruction.

uint32_t executed
The number of times this instruction was executed per warp.
It will be incremented regardless of predicate or condition code.

uint32_t pad
Undefined.
Reserved for internal use.