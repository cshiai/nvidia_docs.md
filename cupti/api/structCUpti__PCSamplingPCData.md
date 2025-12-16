# 7.127. CUpti_PCSamplingPCData


struct CUpti_PCSamplingPCData
PC Sampling data.

Public Members

size_t size
[w] Size of the data structure.
CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

uint64_t cubinCrc
[r] Unique cubin id

uint64_t pcOffset
[r] PC offset

uint32_t functionIndex
The function’s unique symbol index in the module.

uint32_t pad
Padding.

char *functionName
[r] The function name.
This name string might be shared across all the records including records from activity APIs representing the same function, and so it should not be modified or freed until post processing of all the records is done. Once done, it is user’s responsibility to free the memory using free() function.

size_t stallReasonCount
[r] Collected stall reason count

CUpti_PCSamplingStallReason *stallReason
[r] Stall reason id Total samples

uint32_t correlationId
The correlation ID of the kernel to which this result is associated.
Only valid for serialized mode of pc sampling collection. For continous mode of collection the correlationId will be set to 0.