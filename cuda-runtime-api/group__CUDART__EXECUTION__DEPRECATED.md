# CUDA Runtime API

[< Previous](group__CUDART__EXECUTION.html) | [Next >](group__CUDART__OCCUPANCY.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 6.8. Execution Control [DEPRECATED]


This section describes the deprecated execution control functions of the CUDA runtime application programming interface.


Some functions have overloaded C++ API template versions documented separately in the [C++ API Routines](group__CUDART__HIGHLEVEL.html#group__CUDART__HIGHLEVEL) module.


### Functions


__host__
                           ​cudaError_t cudaFuncSetSharedMemConfig (  const void* func, cudaSharedMemConfig config )
Sets the shared memory configuration for a device function.


### Functions


__host__
                              ​cudaError_t cudaFuncSetSharedMemConfig (  const void* func, cudaSharedMemConfig config )
Sets the shared memory configuration for a device function.

                                 Parameters



func
- Device function symbol
config
- Requested shared memory configuration

Returns
cudaSuccess, cudaErrorInvalidDeviceFunction, cudaErrorInvalidValue,


Deprecated

DescriptionOn devices with configurable shared memory banks, this function will force all subsequent launches of the specified device
                              function to have the given shared memory bank size configuration. On any given launch of the function, the shared memory configuration
                              of the device will be temporarily changed if needed to suit the function's preferred configuration. Changes in shared memory
                              configuration between subsequent launches of functions, may introduce a device side synchronization point.
                              Any per-function setting of shared memory bank size set via cudaFuncSetSharedMemConfig will override the device wide setting set by cudaDeviceSetSharedMemConfig.

Changing the shared memory bank size will not increase shared memory usage or affect occupancy of kernels, but may have major
                                 effects on performance. Larger bank sizes will allow for greater potential bandwidth to shared memory, but will change what
                                 kinds of accesses to shared memory will result in bank conflicts.

This function will do nothing on devices with fixed shared memory bank size.
For templated functions, pass the function symbol as follows: func_name<template_arg_0,...,template_arg_N>
The supported bank configurations are:


cudaSharedMemBankSizeDefault: use the device's shared memory configuration when launching this function.

cudaSharedMemBankSizeFourByte: set shared memory bank width to be four bytes natively when launching this function.

cudaSharedMemBankSizeEightByte: set shared memory bank width to be eight bytes natively when launching this function.

Note:

Note that this function may also return error codes from previous, asynchronous launches.

Use of a string naming a function as the func parameter was deprecated in CUDA 4.1 and removed in CUDA 5.0.


Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


See also:
cudaDeviceSetSharedMemConfig, cudaDeviceGetSharedMemConfig, cudaDeviceSetCacheConfig, cudaDeviceGetCacheConfig, cudaFuncSetCacheConfig, cuFuncSetSharedMemConfig


---