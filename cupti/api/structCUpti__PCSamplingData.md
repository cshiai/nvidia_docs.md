# 7.121. CUpti_PCSamplingData


struct CUpti_PCSamplingData
Collected PC Sampling data.

Public Members

size_t size
[w] Size of the data structure.
CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

size_t collectNumPcs
[w] Number of PCs to be collected

uint64_t totalSamples
[r] Number of samples collected across all PCs.
It includes samples for user modules, samples for non-user kernels and dropped samples. It includes counts for all non selected stall reasons. CUPTI does not provide PC records for non-user kernels. CUPTI does not provide PC records for instructions for which all selected stall reason metrics counts are zero.

uint64_t droppedSamples
[r] Number of samples that were dropped by hardware due to backpressure/overflow.

size_t totalNumPcs
[r] Number of PCs collected

size_t remainingNumPcs
[r] Number of PCs available for collection

uint64_t rangeId
[r] Unique identifier for each range.
Data collected across multiple ranges in multiple buffers can be identified using range id.

CUpti_PCSamplingPCData *pPcData
[r] Profiled PC data This data struct should have enough memory to collect number of PCs mentioned in
collectNumPcs

uint64_t nonUsrKernelsTotalSamples
[r] Number of samples collected across all non user kernels PCs.
It includes samples for non-user kernels. It includes counts for all non selected stall reasons as well. CUPTI does not provide PC records for non-user kernels.

uint8_t hardwareBufferFull
[r] Status of the hardware buffer.
CUPTI returns the error code CUPTI_ERROR_OUT_OF_MEMORY when hardware buffer is full. When hardware buffer is full, user will get pc data as 0. To mitigate this issue, one or more of the below options can be tried:
Increase the hardware buffer size using the attribute CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_HARDWARE_BUFFER_SIZE
Decrease the thread sleep span using the attribute CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_WORKER_THREAD_PERIODIC_SLEEP_SPAN
Decrease the sampling frequency using the attribute CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_SAMPLING_PERIOD