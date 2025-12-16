# CUDA Driver API

[< Previous](group__CUDA__INITIALIZE.html) | [Next >](group__CUDA__DEVICE.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.4. Version Management


This section describes the version management functions of the low-level CUDA driver application programming interface.


### Functions


CUresult cuDriverGetVersion (  int* driverVersion )
Returns the latest CUDA version supported by driver.


### Functions


CUresult cuDriverGetVersion (  int* driverVersion )
Returns the latest CUDA version supported by driver.

                                 Parameters



driverVersion
- Returns the CUDA driver version

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE

Description
Returns in *driverVersion the version of CUDA supported by the driver. The version is returned as (1000 * major + 10 * minor). For example, CUDA 9.2
                                 would be represented by 9020.

This function automatically returns CUDA_ERROR_INVALID_VALUE if driverVersion is NULL.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cudaDriverGetVersion, cudaRuntimeGetVersion


---