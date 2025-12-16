# CUDA Driver API

[< Previous](group__CUDA__PROFILER__DEPRECATED.html) | [Next >](group__CUDA__GL.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.39. Profiler Control


This section describes the profiler control functions of the low-level CUDA driver application programming interface.


### Functions


CUresult cuProfilerStart (  void )
Enable profiling.

CUresult cuProfilerStop (  void )
Disable profiling.


### Functions


CUresult cuProfilerStart (  void )
Enable profiling.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_CONTEXT

Description
Enables profile collection by the active profiling tool for the current context. If profiling is already enabled, then cuProfilerStart() has no effect.

cuProfilerStart and cuProfilerStop APIs are used to programmatically control the profiling granularity by allowing profiling
                                 to be done only on selective pieces of code.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuProfilerInitialize, cuProfilerStop, cudaProfilerStart

CUresult cuProfilerStop (  void )
Disable profiling.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_CONTEXT

Description
Disables profile collection by the active profiling tool for the current context. If profiling is already disabled, then cuProfilerStop() has no effect.

cuProfilerStart and cuProfilerStop APIs are used to programmatically control the profiling granularity by allowing profiling
                                 to be done only on selective pieces of code.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuProfilerInitialize, cuProfilerStart, cudaProfilerStop


---