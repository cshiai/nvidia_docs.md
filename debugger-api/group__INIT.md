# Debugger API

[< Previous](group__GENERAL.html) | [Next >](group__EXEC.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 3.2. Initialization




### Variables


CUDBGResult
                            ( *CUDBGAPI_st::finalize )(   )
Finalize the API and free all memory.

CUDBGResult
                            ( *CUDBGAPI_st::getSupportedDebuggerCapabilities )(  CUDBGCapabilityFlags* capabilities )
Returns debugger capabilities that are supported by this version of the API.

CUDBGResult
                            ( *CUDBGAPI_st::initialize )(   )
Initialize the API.


### Variables


CUDBGResult
                              ( *CUDBGAPI_st::finalize )(   )
Finalize the API and free all memory.  Since CUDA 3.0.

See also:
initialize

Returns
CUDBG_SUCCESS, CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_COMMUNICATION_FAILURE, CUDBG_ERROR_UNKNOWN

CUDBGResult
                              ( *CUDBGAPI_st::getSupportedDebuggerCapabilities )(  CUDBGCapabilityFlags* capabilities )
Returns debugger capabilities that are supported by this version of the API.  Since CUDA 12.5.
This API method can be called without initializing the API.

                                 Parameters



capabilities
- returned debugger capabilities

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS,

CUDBGResult
                              ( *CUDBGAPI_st::initialize )(   )
Initialize the API.  Since CUDA 3.0.

See also:
finalize

Returns
CUDBG_SUCCESS, CUDBG_ERROR_UNKNOWN


---