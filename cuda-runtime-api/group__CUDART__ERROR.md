# CUDA Runtime API

[< Previous](group__CUDART__DEVICE__DEPRECATED.html) | [Next >](group__CUDART__STREAM.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 6.3. Error Handling


This section describes the error handling functions of the CUDA runtime application programming interface.


### Functions


__host__
                           ​
                           __device__
                           ​const   char* cudaGetErrorName (  cudaError_t error )
Returns the string representation of an error code enum name.

__host__
                           ​
                           __device__
                           ​const   char* cudaGetErrorString (  cudaError_t error )
Returns the description string for an error code.

__host__
                           ​
                           __device__
                           ​cudaError_t cudaGetLastError (  void )
Returns the last error from a runtime call.

__host__
                           ​
                           __device__
                           ​cudaError_t cudaPeekAtLastError (  void )
Returns the last error from a runtime call.


### Functions


__host__
                              ​
                              __device__
                              ​const   char* cudaGetErrorName (  cudaError_t error )
Returns the string representation of an error code enum name.

                                 Parameters



error
- Error code to convert to string

Returns
char* pointer to a NULL-terminated string


Description
Returns a string containing the name of an error code in the enum. If the error code is not recognized, "unrecognized error
                                 code" is returned.


See also:
cudaGetErrorString, cudaGetLastError, cudaPeekAtLastError, cudaError, cuGetErrorName

__host__
                              ​
                              __device__
                              ​const   char* cudaGetErrorString (  cudaError_t error )
Returns the description string for an error code.

                                 Parameters



error
- Error code to convert to string

Returns
char* pointer to a NULL-terminated string


Description
Returns the description string for an error code. If the error code is not recognized, "unrecognized error code" is returned.

See also:
cudaGetErrorName, cudaGetLastError, cudaPeekAtLastError, cudaError, cuGetErrorString

__host__
                              ​
                              __device__
                              ​cudaError_t cudaGetLastError (  void )
Returns the last error from a runtime call.

Returns
cudaSuccess, cudaErrorMissingConfiguration, cudaErrorMemoryAllocation, cudaErrorInitializationError, cudaErrorLaunchFailure, cudaErrorLaunchTimeout, cudaErrorLaunchOutOfResources, cudaErrorInvalidDeviceFunction, cudaErrorInvalidConfiguration, cudaErrorInvalidDevice, cudaErrorInvalidValue, cudaErrorInvalidPitchValue, cudaErrorInvalidSymbol, cudaErrorUnmapBufferObjectFailed, cudaErrorInvalidDevicePointer, cudaErrorInvalidTexture, cudaErrorInvalidTextureBinding, cudaErrorInvalidChannelDescriptor, cudaErrorInvalidMemcpyDirection, cudaErrorInvalidFilterSetting, cudaErrorInvalidNormSetting, cudaErrorUnknown, cudaErrorInvalidResourceHandle, cudaErrorInsufficientDriver, cudaErrorNoDevice, cudaErrorSetOnActiveProcess, cudaErrorStartupFailure, cudaErrorInvalidPtx, cudaErrorUnsupportedPtxVersion, cudaErrorNoKernelImageForDevice, cudaErrorJitCompilerNotFound, cudaErrorJitCompilationDisabled

Description
Returns the last error that has been produced by any of the runtime calls in the same instance of the CUDA Runtime library
                                 in the host thread and resets it to cudaSuccess.

Note: Multiple instances of the CUDA Runtime library can be present in an application when using a library that statically
                                 links the CUDA Runtime.


Note:

Note that this function may also return error codes from previous, asynchronous launches.

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


See also:
cudaPeekAtLastError, cudaGetErrorName, cudaGetErrorString, cudaError

__host__
                              ​
                              __device__
                              ​cudaError_t cudaPeekAtLastError (  void )
Returns the last error from a runtime call.

Returns
cudaSuccess, cudaErrorMissingConfiguration, cudaErrorMemoryAllocation, cudaErrorInitializationError, cudaErrorLaunchFailure, cudaErrorLaunchTimeout, cudaErrorLaunchOutOfResources, cudaErrorInvalidDeviceFunction, cudaErrorInvalidConfiguration, cudaErrorInvalidDevice, cudaErrorInvalidValue, cudaErrorInvalidPitchValue, cudaErrorInvalidSymbol, cudaErrorUnmapBufferObjectFailed, cudaErrorInvalidDevicePointer, cudaErrorInvalidTexture, cudaErrorInvalidTextureBinding, cudaErrorInvalidChannelDescriptor, cudaErrorInvalidMemcpyDirection, cudaErrorInvalidFilterSetting, cudaErrorInvalidNormSetting, cudaErrorUnknown, cudaErrorInvalidResourceHandle, cudaErrorInsufficientDriver, cudaErrorNoDevice, cudaErrorSetOnActiveProcess, cudaErrorStartupFailure, cudaErrorInvalidPtx, cudaErrorUnsupportedPtxVersion, cudaErrorNoKernelImageForDevice, cudaErrorJitCompilerNotFound, cudaErrorJitCompilationDisabled

Description
Returns the last error that has been produced by any of the runtime calls in the same instance of the CUDA Runtime library
                                 in the host thread. This call does not reset the error to cudaSuccess like cudaGetLastError().

Note: Multiple instances of the CUDA Runtime library can be present in an application when using a library that statically
                                 links the CUDA Runtime.


Note:

Note that this function may also return error codes from previous, asynchronous launches.

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


See also:
cudaGetLastError, cudaGetErrorName, cudaGetErrorString, cudaError


---