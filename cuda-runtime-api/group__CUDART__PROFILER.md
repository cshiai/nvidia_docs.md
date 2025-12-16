# CUDA Runtime API

[< Previous](group__CUDART__DRIVER.html) | [Next >](group__CUDART__TYPES.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 6.36. Profiler Control


This section describes the profiler control functions of the CUDA runtime application programming interface.


### Functions


__host__
                           ​cudaError_t cudaProfilerStart (  void )
Enable profiling.

__host__
                           ​cudaError_t cudaProfilerStop (  void )
Disable profiling.


### Functions


__host__
                              ​cudaError_t cudaProfilerStart (  void )
Enable profiling.

Returns
cudaSuccess

Description
Enables profile collection by the active profiling tool for the current context. If profiling is already enabled, then cudaProfilerStart() has no effect.

cudaProfilerStart and cudaProfilerStop APIs are used to programmatically control the profiling granularity by allowing profiling
                                 to be done only on selective pieces of code.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cudaProfilerStop, cuProfilerStart

__host__
                              ​cudaError_t cudaProfilerStop (  void )
Disable profiling.

Returns
cudaSuccess

Description
Disables profile collection by the active profiling tool for the current context. If profiling is already disabled, then cudaProfilerStop() has no effect.

cudaProfilerStart and cudaProfilerStop APIs are used to programmatically control the profiling granularity by allowing profiling
                                 to be done only on selective pieces of code.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cudaProfilerStart, cuProfilerStop


---