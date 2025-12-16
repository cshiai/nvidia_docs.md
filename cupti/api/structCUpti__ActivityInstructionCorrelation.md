# 7.38. CUpti_ActivityInstructionCorrelation


struct CUpti_ActivityInstructionCorrelation
The activity record for source-level sass/source line-by-line correlation.
This activity records source level sass/source correlation information. (CUPTI_ACTIVITY_KIND_INSTRUCTION_CORRELATION).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_INSTRUCTION_CORRELATION.

CUpti_ActivityFlag flags
The properties of this instruction.

uint32_t sourceLocatorId
The ID for source locator.

uint32_t functionId
Correlation ID with global/device function name.

uint32_t pcOffset
The pc offset for the instruction.

uint32_t pad
Undefined.
Reserved for internal use.