# 6.10. CUPTI Result Codes


Error and result codes returned by CUPTI functions.


## 6.10.1. Enumerations


CUptiResult
CUPTI result codes.


## 6.10.2. Functions


CUptiResult cuptiGetErrorMessage(CUptiResult result, const char str)
Get the descriptive message corresponding to error codes returned by CUPTI.

CUptiResult cuptiGetResultString(CUptiResult result, const char str)
Get the descriptive string for a CUptiResult.


## 6.10.3. Enumerations


enum CUptiResult
CUPTI result codes.
Error and result codes returned by CUPTI functions.
Values:

enumerator CUPTI_SUCCESS
No error.

enumerator CUPTI_ERROR_INVALID_PARAMETER
One or more of the parameters is invalid.

enumerator CUPTI_ERROR_INVALID_DEVICE
The device does not correspond to a valid CUDA device.

enumerator CUPTI_ERROR_INVALID_CONTEXT
The context is NULL or not valid.

enumerator CUPTI_ERROR_INVALID_EVENT_DOMAIN_ID
The event domain id is invalid.

enumerator CUPTI_ERROR_INVALID_EVENT_ID
The event id is invalid.

enumerator CUPTI_ERROR_INVALID_EVENT_NAME
The event name is invalid.

enumerator CUPTI_ERROR_INVALID_OPERATION
The current operation cannot be performed due to dependency on other factors.

enumerator CUPTI_ERROR_OUT_OF_MEMORY
Unable to allocate enough memory to perform the requested operation.

enumerator CUPTI_ERROR_HARDWARE
An error occurred on the performance monitoring hardware.

enumerator CUPTI_ERROR_PARAMETER_SIZE_NOT_SUFFICIENT
The output buffer size is not sufficient to return all requested data.

enumerator CUPTI_ERROR_API_NOT_IMPLEMENTED
API is not implemented.

enumerator CUPTI_ERROR_MAX_LIMIT_REACHED
The maximum limit is reached.

enumerator CUPTI_ERROR_NOT_READY
The object is not yet ready to perform the requested operation.

enumerator CUPTI_ERROR_NOT_COMPATIBLE
The current operation is not compatible with the current state of the object.

enumerator CUPTI_ERROR_NOT_INITIALIZED
CUPTI is unable to initialize its connection to the CUDA driver.

enumerator CUPTI_ERROR_INVALID_METRIC_ID
The metric id is invalid.

enumerator CUPTI_ERROR_INVALID_METRIC_NAME
The metric name is invalid.

enumerator CUPTI_ERROR_QUEUE_EMPTY
The queue is empty.

enumerator CUPTI_ERROR_INVALID_HANDLE
Invalid handle (internal?).

enumerator CUPTI_ERROR_INVALID_STREAM
Invalid stream.

enumerator CUPTI_ERROR_INVALID_KIND
Invalid kind.

enumerator CUPTI_ERROR_INVALID_EVENT_VALUE
Invalid event value.

enumerator CUPTI_ERROR_DISABLED
CUPTI is disabled due to conflicts with other enabled profilers.

enumerator CUPTI_ERROR_INVALID_MODULE
Invalid module.

enumerator CUPTI_ERROR_INVALID_METRIC_VALUE
Invalid metric value.

enumerator CUPTI_ERROR_HARDWARE_BUSY
The performance monitoring hardware is in use by other client.

enumerator CUPTI_ERROR_NOT_SUPPORTED
The attempted operation is not supported on the current system or device.

enumerator CUPTI_ERROR_UM_PROFILING_NOT_SUPPORTED
Unified memory profiling is not supported on the system.
Potential reason could be unsupported OS or architecture.

enumerator CUPTI_ERROR_UM_PROFILING_NOT_SUPPORTED_ON_DEVICE
Unified memory profiling is not supported on the device.

enumerator CUPTI_ERROR_UM_PROFILING_NOT_SUPPORTED_ON_NON_P2P_DEVICES
Unified memory profiling is not supported on a multi-GPU configuration without P2P support between any pair of devices.

enumerator CUPTI_ERROR_UM_PROFILING_NOT_SUPPORTED_WITH_MPS
Unified memory profiling is not supported under the Multi-Process Service (MPS) environment.
CUDA 7.5 removes this restriction.

enumerator CUPTI_ERROR_CDP_TRACING_NOT_SUPPORTED
In CUDA 9.0, devices with compute capability 7.0 don’t support CDP tracing.

enumerator CUPTI_ERROR_VIRTUALIZED_DEVICE_NOT_SUPPORTED
Profiling on virtualized GPU is not supported.

enumerator CUPTI_ERROR_CUDA_COMPILER_NOT_COMPATIBLE
Profiling results might be incorrect for CUDA applications compiled with nvcc version older than 9.0 for devices with compute capability 6.0 and 6.1.
Profiling session will continue and CUPTI will notify it using this error code. User is advised to recompile the application code with nvcc version 9.0 or later. Ignore this warning if code is already compiled with the recommended nvcc version.

enumerator CUPTI_ERROR_INSUFFICIENT_PRIVILEGES
User doesn’t have sufficient privileges which are required to start the profiling session.
One possible reason for this may be that the NVIDIA driver or your system administrator may have restricted access to the NVIDIA GPU performance counters. To learn how to resolve this issue and find more information, please visit https://developer.nvidia.com/CUPTI_ERROR_INSUFFICIENT_PRIVILEGES

enumerator CUPTI_ERROR_OLD_PROFILER_API_INITIALIZED
Legacy CUPTI Profiling API i.e.
event API from the header cupti_events.h and metric API from the header cupti_metrics.h are not compatible with the Profiling API in the header cupti_profiler_target.h and Perfworks metrics API in the headers nvperf_host.h and nvperf_target.h.

enumerator CUPTI_ERROR_OPENACC_UNDEFINED_ROUTINE
Missing definition of the OpenACC API routine in the linked OpenACC library.
One possible reason is that OpenACC library is linked statically in the user application, which might not have the definition of all the OpenACC API routines needed for the OpenACC profiling, as compiler might ignore definitions for the functions not used in the application. This issue can be mitigated by linking the OpenACC library dynamically.

enumerator CUPTI_ERROR_LEGACY_PROFILER_NOT_SUPPORTED
Legacy CUPTI Profiling API i.e.
event API from the header cupti_events.h and metric API from the header cupti_metrics.h are not supported on devices with compute capability 7.5 and higher (i.e. Turing and later GPU architectures). These APIs were deprecated in CUDA 12.8 and removed in CUDA 13.0. These are replaced by the host profiling API in the header cupti_profiler_host.h and target profiling API in the header cupti_range_profiler.h which are supported on devices with compute capability 7.5 and higher (i.e. Turing and later GPU architectures). Further, the PC Sampling Activity API and the source/SASS level metrics from the header cupti_activity.h are removed in CUDA 13.0.

enumerator CUPTI_ERROR_MULTIPLE_SUBSCRIBERS_NOT_SUPPORTED
CUPTI doesn’t allow multiple callback subscribers.
Only a single subscriber can be registered at a time. Same error code is used when application is launched using NVIDIA tools like Nsight Systems, Nsight Compute, and cuda-gdb.

enumerator CUPTI_ERROR_VIRTUALIZED_DEVICE_INSUFFICIENT_PRIVILEGES
Profiling on virtualized GPU is not allowed by hypervisor.

enumerator CUPTI_ERROR_CONFIDENTIAL_COMPUTING_NOT_SUPPORTED
Profiling and tracing are not allowed when confidential computing mode is enabled.

enumerator CUPTI_ERROR_CMP_DEVICE_NOT_SUPPORTED
CUPTI does not support NVIDIA Crypto Mining Processors (CMP).
For more information, please visit https://developer.nvidia.com/ERR_NVCMPGPU

enumerator CUPTI_ERROR_MIG_DEVICE_NOT_SUPPORTED
Profiling on Multi-instance GPU (MIG) is not supported.

enumerator CUPTI_ERROR_SLI_DEVICE_NOT_SUPPORTED
Profiling on SLI device is not supported.

enumerator CUPTI_ERROR_WSL_DEVICE_NOT_SUPPORTED
Profiling on WSL device is not supported.

enumerator CUPTI_ERROR_INVALID_CHIP_NAME
For invalid or unsupported chip name passed to cuptiProfilerHostInitialize.

enumerator CUPTI_ERROR_HES_TRACE_NOT_SUPPORTED_ON_MPS
Hardware Event System (HES) trace is not supported on MPS.

enumerator CUPTI_ERROR_UNKNOWN
An unknown internal error has occurred.

enumerator CUPTI_ERROR_FORCE_INT


## 6.10.4. Functions


CUptiResult cuptiGetErrorMessage(

CUptiResult result,
const char str,

)
Get the descriptive message corresponding to error codes returned by CUPTI.
Return the descriptive error message for a CUptiResult in *str.

Note
Thread-safety: this function is thread safe.

Parameters:

result – The result to get the descriptive error message for
str – Returns the error message string

Return values:

CUPTI_SUCCESS – on success
CUPTI_ERROR_INVALID_PARAMETER – if str is NULL or result is not a valid CUptiResult


CUptiResult cuptiGetResultString(

CUptiResult result,
const char str,

)
Get the descriptive string for a CUptiResult.
Return the descriptive string for a CUptiResult in *str.

Note
Thread-safety: this function is thread safe.

Parameters:

result – The result to get the string for
str – Returns the string

Return values:

CUPTI_SUCCESS – on success
CUPTI_ERROR_INVALID_PARAMETER – if str is NULL or result is not a valid CUptiResult