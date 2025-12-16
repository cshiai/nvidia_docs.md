# 7.96. CUpti_ActivityPCSampling


struct CUpti_ActivityPCSampling
The activity record for PC sampling.
(deprecated in CUDA 8.0)
This activity records information obtained by sampling PC (CUPTI_ACTIVITY_KIND_PC_SAMPLING). PC sampling activities are now reported using the CUpti_ActivityPCSampling2 activity record.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_PC_SAMPLING.

CUpti_ActivityFlag flags
The properties of this instruction.

uint32_t sourceLocatorId
The ID for source locator.

uint32_t correlationId
The correlation ID of the kernel to which this result is associated.

uint32_t functionId
Correlation ID with global/device function name.

uint32_t pcOffset
The pc offset for the instruction.

uint32_t samples
Number of times the PC was sampled with the stallReason in the record.
The same PC can be sampled with different stall reasons.

CUpti_ActivityPCSamplingStallReason stallReason
Current stall reason.
Includes one of the reasons from CUpti_ActivityPCSamplingStallReason