# Debugger API

[< Previous](modules.html) | [Next >](group__INIT.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 3.1. General




### Classes


struct
CUDBGCudaLogMessage
CUDA Log Message.


### Enumerations


enum CUDBGCudaLogLevel
CUDA Log severity level.

enum CUDBGResult
Result values of all the API routines.


### Enumerations


enum CUDBGCudaLogLevel
Values



CUDBG_CUDA_LOG_LEVEL_INVALID = 0xFFFFFFFFU
Invalid log level.
CUDBG_CUDA_LOG_LEVEL_ERROR = 0
Error log level, matches CU_LOG_LEVEL_ERROR.
CUDBG_CUDA_LOG_LEVEL_WARNING = 1
Warning log level, matches CU_LOG_LEVEL_WARNING.

enum CUDBGResult
Values



CUDBG_SUCCESS = 0x0000
The API call executed successfully.
CUDBG_ERROR_UNKNOWN = 0x0001
Error type not listed below.
CUDBG_ERROR_BUFFER_TOO_SMALL = 0x0002
Cannot copy all the queried data into the buffer argument.
CUDBG_ERROR_UNKNOWN_FUNCTION = 0x0003
Function cannot be found in the CUDA kernel.
CUDBG_ERROR_INVALID_ARGS = 0x0004
Wrong use of arguments (NULL pointer, illegal value,....).
CUDBG_ERROR_UNINITIALIZED = 0x0005
Debugger API has not yet been properly initialized.
CUDBG_ERROR_INVALID_COORDINATES = 0x0006
Invalid block or thread coordinates were provided.
CUDBG_ERROR_INVALID_MEMORY_SEGMENT = 0x0007
Invalid memory segment requested.
CUDBG_ERROR_INVALID_MEMORY_ACCESS = 0x0008
Requested address (+size) is not within proper segment boundaries.
CUDBG_ERROR_MEMORY_MAPPING_FAILED = 0x0009
Memory is not mapped and cannot be mapped.
CUDBG_ERROR_INTERNAL = 0x000a
A debugger internal error occurred.
CUDBG_ERROR_INVALID_DEVICE = 0x000b
Specified device cannot be found.
CUDBG_ERROR_INVALID_SM = 0x000c
Specified sm cannot be found.
CUDBG_ERROR_INVALID_WARP = 0x000d
Specified warp cannot be found.
CUDBG_ERROR_INVALID_LANE = 0x000e
Specified lane cannot be found.
CUDBG_ERROR_SUSPENDED_DEVICE = 0x000f
The requested operation is not allowed when the device is suspended.
CUDBG_ERROR_RUNNING_DEVICE = 0x0010
Device is running and not suspended.
CUDBG_ERROR_RESERVED_0 = 0x0011

CUDBG_ERROR_INVALID_ADDRESS = 0x0012
Address is out-of-range.
CUDBG_ERROR_INCOMPATIBLE_API = 0x0013
The requested API is not available.
CUDBG_ERROR_INITIALIZATION_FAILURE = 0x0014
The API could not be initialized.
CUDBG_ERROR_INVALID_GRID = 0x0015
The specified grid is not valid.
CUDBG_ERROR_NO_EVENT_AVAILABLE = 0x0016
The event queue is empty and there is no event left to be processed.
CUDBG_ERROR_SOME_DEVICES_WATCHDOGGED = 0x0017
Some devices were excluded because they have a watchdog associated with them.
CUDBG_ERROR_ALL_DEVICES_WATCHDOGGED = 0x0018
All devices were exclude because they have a watchdog associated with them.
CUDBG_ERROR_INVALID_ATTRIBUTE = 0x0019
Specified attribute does not exist or is incorrect.
CUDBG_ERROR_ZERO_CALL_DEPTH = 0x001a
No function calls have been made on the device.
CUDBG_ERROR_INVALID_CALL_LEVEL = 0x001b
Specified call level is invalid.
CUDBG_ERROR_COMMUNICATION_FAILURE = 0x001c
Communication error between the debugger and the application.
CUDBG_ERROR_INVALID_CONTEXT = 0x001d
Specified context cannot be found.
CUDBG_ERROR_ADDRESS_NOT_IN_DEVICE_MEM = 0x001e
Requested address was not originally allocated from device memory (most likely visible in system memory).
CUDBG_ERROR_MEMORY_UNMAPPING_FAILED = 0x001f
Requested address is not mapped and cannot be unmapped.
CUDBG_ERROR_INCOMPATIBLE_DISPLAY_DRIVER = 0x0020
The display driver is incompatible with the API.
CUDBG_ERROR_INVALID_MODULE = 0x0021
The specified module is not valid.
CUDBG_ERROR_LANE_NOT_IN_SYSCALL = 0x0022
The specified lane is not inside a device syscall.
CUDBG_ERROR_RESERVED_1 = 0x0023

CUDBG_ERROR_INVALID_ENVVAR_ARGS = 0x0024
Some environment variable's value is invalid.
CUDBG_ERROR_OS_RESOURCES = 0x0025
Error while allocating resources from the OS.
CUDBG_ERROR_FORK_FAILED = 0x0026
Error while forking the debugger process.
CUDBG_ERROR_NO_DEVICE_AVAILABLE = 0x0027
No CUDA capable device was found.
CUDBG_ERROR_ATTACH_NOT_POSSIBLE = 0x0028
Attaching to the CUDA program is not possible.
CUDBG_ERROR_WARP_RESUME_NOT_POSSIBLE = 0x0029

CUDBG_ERROR_INVALID_WARP_MASK = 0x002a

CUDBG_ERROR_AMBIGUOUS_MEMORY_ADDRESS = 0x002b
Specified device pointer cannot be resolved to a GPU unambiguously because it is valid on more than one GPU.
CUDBG_ERROR_RECURSIVE_API_CALL = 0x002c

CUDBG_ERROR_MISSING_DATA = 0x002d

CUDBG_ERROR_NOT_SUPPORTED = 0x002e


---