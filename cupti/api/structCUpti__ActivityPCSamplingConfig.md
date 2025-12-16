# 7.99. CUpti_ActivityPCSamplingConfig


struct CUpti_ActivityPCSamplingConfig
PC sampling configuration structure.
This structure defines the pc sampling configuration.
See function cuptiActivityConfigurePCSampling

Public Members

uint32_t size
Size of configuration structure.
CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

CUpti_ActivityPCSamplingPeriod samplingPeriod
There are 5 level provided for sampling period.
The level internally maps to a period in terms of cycles. Same level can map to different number of cycles on different gpus. No of cycles will be chosen to minimize information loss. The period chosen will be given by samplingPeriodInCycles in CUpti_ActivityPCSamplingRecordInfo for each kernel instance.

uint32_t samplingPeriod2
This will override the period set by samplingPeriod.
Value 0 in samplingPeriod2 will be considered as samplingPeriod2 should not be used and samplingPeriod should be used. Valid values for samplingPeriod2 are between 5 to 31 both inclusive. This will set the sampling period to (2^samplingPeriod2) cycles.