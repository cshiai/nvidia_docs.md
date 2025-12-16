# CUDA Driver API

[< Previous](group__CUDA__ERROR.html) | [Next >](group__CUDA__VERSION.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.3. Initialization


This section describes the initialization functions of the low-level CUDA driver application programming interface.


### Functions


CUresult cuInit (  unsigned int  Flags )
Initialize the CUDA driver API Initializes the driver API and must be called before any other function from the driver API
                           in the current process. Currently, the Flags parameter must be 0. If cuInit() has not been called, any function from the driver API will return CUDA_ERROR_NOT_INITIALIZED.


### Functions


CUresult cuInit (  unsigned int  Flags )
Initialize the CUDA driver API Initializes the driver API and must be called before any other function from the driver API
                              in the current process. Currently, the Flags parameter must be 0. If cuInit() has not been called, any function from the driver API will return CUDA_ERROR_NOT_INITIALIZED.



                                 Parameters



Flags
- Initialization flag for CUDA.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_INVALID_DEVICE, CUDA_ERROR_SYSTEM_DRIVER_MISMATCH, CUDA_ERROR_COMPAT_NOT_SUPPORTED_ON_DEVICE

Description
Note: cuInit preloads various libraries needed for JIT compilation. To opt-out of this behavior, set the environment variable
                                 CUDA_FORCE_PRELOAD_LIBRARIES=0. CUDA will lazily load JIT libraries as needed. To disable JIT entirely, set the environment
                                 variable CUDA_DISABLE_JIT=1.


Note:Note that this function may also return error codes from previous, asynchronous launches.


---