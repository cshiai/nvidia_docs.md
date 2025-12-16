# 7.98. CUpti_ActivityPCSampling3


struct CUpti_ActivityPCSampling3
The activity record for PC sampling.
This activity records information obtained by sampling PC (CUPTI_ACTIVITY_KIND_PC_SAMPLING).

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

uint32_t latencySamples
Number of times the PC was sampled with the stallReason in the record.
These samples indicate that no instruction was issued in that cycle from the warp scheduler from where the warp was sampled. Field is valid for devices with compute capability 6.0 and higher

uint32_t samples
Number of times the PC was sampled with the stallReason in the record.
The same PC can be sampled with different stall reasons. The count includes latencySamples.

CUpti_ActivityPCSamplingStallReason stallReason
Current stall reason.
Includes one of the reasons from CUpti_ActivityPCSamplingStallReason

uint64_t pcOffset
The pc offset for the instruction.