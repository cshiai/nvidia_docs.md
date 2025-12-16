# 7.39. CUpti_ActivityInstructionExecution


struct CUpti_ActivityInstructionExecution
The activity record for source-level instruction execution.
This activity records result for source level instruction execution. (CUPTI_ACTIVITY_KIND_INSTRUCTION_EXECUTION).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_INSTRUCTION_EXECUTION.

CUpti_ActivityFlag flags
The properties of this instruction execution.

uint32_t sourceLocatorId
The ID for source locator.

uint32_t correlationId
The correlation ID of the kernel to which this result is associated.

uint32_t functionId
Correlation ID with global/device function name.

uint32_t pcOffset
The pc offset for the instruction.

uint64_t threadsExecuted
This increments each time when this instruction is executed by number of threads that executed this instruction, regardless of predicate or condition code.

uint64_t notPredOffThreadsExecuted
This increments each time when this instruction is executed by number of threads that executed this instruction with predicate and condition code evaluating to true.

uint32_t executed
The number of times this instruction was executed per warp.
It will be incremented regardless of predicate or condition code.

uint32_t pad
Undefined.
Reserved for internal use.