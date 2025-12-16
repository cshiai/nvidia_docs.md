# 7.2. CUpti_ActivityAPI


struct CUpti_ActivityAPI
The activity record for a driver or runtime API invocation.
This activity record represents an invocation of a driver or runtime API (CUPTI_ACTIVITY_KIND_DRIVER and CUPTI_ACTIVITY_KIND_RUNTIME).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_DRIVER, CUPTI_ACTIVITY_KIND_RUNTIME, or CUPTI_ACTIVITY_KIND_INTERNAL_LAUNCH_API.

CUpti_CallbackId cbid
The ID of the driver or runtime function.

uint64_t start
The start timestamp for the function, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the function.

uint64_t end
The end timestamp for the function, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the function.

uint32_t processId
The ID of the process where the driver or runtime CUDA function is executing.

uint32_t threadId
The ID of the thread where the driver or runtime CUDA function is executing.

uint32_t correlationId
The correlation ID of the driver or runtime CUDA function.
Each function invocation is assigned a unique correlation ID that is identical to the correlation ID in the memcpy, memset, or kernel activity record that is associated with this function.

uint32_t returnValue
The return value for the function.
For a CUDA driver function with will be a CUresult value, and for a CUDA runtime function this will be a cudaError_t value.