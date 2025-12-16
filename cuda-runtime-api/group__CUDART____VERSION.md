# CUDA Runtime API

[< Previous](group__CUDART__SURFACE__OBJECT.html) | [Next >](group__CUDART__LOGS.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 6.28. Version Management




### Functions


__host__
                           ​cudaError_t cudaDriverGetVersion (  int* driverVersion )
Returns the latest version of CUDA supported by the driver.

__host__
                           ​
                           __device__
                           ​cudaError_t cudaRuntimeGetVersion (  int* runtimeVersion )
Returns the CUDA Runtime version.


### Functions


__host__
                              ​cudaError_t cudaDriverGetVersion (  int* driverVersion )
Returns the latest version of CUDA supported by the driver.

                                 Parameters



driverVersion
- Returns the CUDA driver version.

Returns
cudaSuccess, cudaErrorInvalidValue

Description
Returns in *driverVersion the latest version of CUDA supported by the driver. The version is returned as (1000  major + 10  minor). For example, CUDA
                                 9.2 would be represented by 9020. If no driver is installed, then 0 is returned as the driver version.

This function automatically returns cudaErrorInvalidValue if driverVersion is NULL.


Note:

Note that this function may also return error codes from previous, asynchronous launches.

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


See also:
cudaRuntimeGetVersion, cuDriverGetVersion

__host__
                              ​
                              __device__
                              ​cudaError_t cudaRuntimeGetVersion (  int* runtimeVersion )
Returns the CUDA Runtime version.

                                 Parameters



runtimeVersion
- Returns the CUDA Runtime version.

Returns
cudaSuccess, cudaErrorInvalidValue

Description
Returns in *runtimeVersion the version number of the current CUDA Runtime instance. The version is returned as (1000  major + 10  minor). For example,
                                 CUDA 9.2 would be represented by 9020.

As of CUDA 12.0, this function no longer initializes CUDA. The purpose of this API is solely to return a compile-time constant
                                 stating the CUDA Toolkit version in the above format.

This function automatically returns cudaErrorInvalidValue if the runtimeVersion argument is NULL.


Note:

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


See also:
cudaDriverGetVersion, cuDriverGetVersion


---