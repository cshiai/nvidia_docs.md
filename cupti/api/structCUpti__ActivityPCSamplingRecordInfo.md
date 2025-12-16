# 7.100. CUpti_ActivityPCSamplingRecordInfo


struct CUpti_ActivityPCSamplingRecordInfo
The activity record for record status for PC sampling.
This activity records information obtained by sampling PC (CUPTI_ACTIVITY_KIND_PC_SAMPLING_RECORD_INFO).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_PC_SAMPLING_RECORD_INFO.

uint32_t correlationId
The correlation ID of the kernel to which this result is associated.

uint64_t totalSamples
Number of times the PC was sampled for this kernel instance including all dropped samples.

uint64_t droppedSamples
Number of samples that were dropped by hardware due to backpressure/overflow.

uint64_t samplingPeriodInCycles
Sampling period in terms of number of cycles .