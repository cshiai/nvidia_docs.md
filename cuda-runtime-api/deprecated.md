# CUDA Runtime API

Global cudaDeviceGetSharedMemConfigGlobal cudaDeviceSetSharedMemConfigGlobal cudaFuncSetSharedMemConfigGlobal cudaMemcpyArrayToArrayGlobal cudaMemcpyFromArrayGlobal cudaMemcpyFromArrayAsyncGlobal cudaMemcpyToArrayGlobal cudaMemcpyToArrayAsyncGlobal cudaGLMapBufferObject
This function is deprecated as of CUDA 3.0.


Global cudaGLMapBufferObjectAsync
This function is deprecated as of CUDA 3.0.


Global cudaGLRegisterBufferObject
This function is deprecated as of CUDA 3.0.


Global cudaGLSetBufferObjectMapFlags
This function is deprecated as of CUDA 3.0.


Global cudaGLSetGLDevice
This function is deprecated as of CUDA 5.0.


Global cudaGLUnmapBufferObject
This function is deprecated as of CUDA 3.0.


Global cudaGLUnmapBufferObjectAsync
This function is deprecated as of CUDA 3.0.


Global cudaGLUnregisterBufferObject
This function is deprecated as of CUDA 3.0.


Global cudaD3D9MapResources
This function is deprecated as of CUDA 3.0.


Global cudaD3D9RegisterResource
This function is deprecated as of CUDA 3.0.


Global cudaD3D9ResourceGetMappedArray
This function is deprecated as of CUDA 3.0.


Global cudaD3D9ResourceGetMappedPitch
This function is deprecated as of CUDA 3.0.


Global cudaD3D9ResourceGetMappedPointer
This function is deprecated as of CUDA 3.0.


Global cudaD3D9ResourceGetMappedSize
This function is deprecated as of CUDA 3.0.


Global cudaD3D9ResourceGetSurfaceDimensions
This function is deprecated as of CUDA 3.0.


Global cudaD3D9ResourceSetMapFlags
This function is deprecated as of CUDA 3.0.


Global cudaD3D9UnmapResources
This function is deprecated as of CUDA 3.0.


Global cudaD3D9UnregisterResource
This function is deprecated as of CUDA 3.0.


Global cudaD3D10GetDirect3DDevice
This function is deprecated as of CUDA 5.0.


Global cudaD3D10MapResources
This function is deprecated as of CUDA 3.0.


Global cudaD3D10RegisterResource
This function is deprecated as of CUDA 3.0.


Global cudaD3D10ResourceGetMappedArray
This function is deprecated as of CUDA 3.0.


Global cudaD3D10ResourceGetMappedPitch
This function is deprecated as of CUDA 3.0.


Global cudaD3D10ResourceGetMappedPointer
This function is deprecated as of CUDA 3.0.


Global cudaD3D10ResourceGetMappedSize
This function is deprecated as of CUDA 3.0.


Global cudaD3D10ResourceGetSurfaceDimensions
This function is deprecated as of CUDA 3.0.


Global cudaD3D10ResourceSetMapFlags
This function is deprecated as of CUDA 3.0.


Global cudaD3D10SetDirect3DDevice
This function is deprecated as of CUDA 5.0.


Global cudaD3D10UnmapResources
This function is deprecated as of CUDA 3.0.


Global cudaD3D10UnregisterResource
This function is deprecated as of CUDA 3.0.


Global cudaD3D11GetDirect3DDevice
This function is deprecated as of CUDA 5.0.


Global cudaD3D11SetDirect3DDevice
This function is deprecated as of CUDA 5.0.


Global cudaGetDriverEntryPoint
This function is deprecated as of CUDA 13.0


Global cudaErrorProfilerNotInitialized
This error return is deprecated as of CUDA 5.0. It is no longer an error to attempt to enable/disable the profiling via cudaProfilerStart or cudaProfilerStop without initialization.


Global cudaErrorProfilerAlreadyStarted
This error return is deprecated as of CUDA 5.0. It is no longer an error to call cudaProfilerStart() when profiling is already enabled.


Global cudaErrorProfilerAlreadyStopped
This error return is deprecated as of CUDA 5.0. It is no longer an error to call cudaProfilerStop() when profiling is already disabled.


Global cudaErrorInvalidHostPointer
This error return is deprecated as of CUDA 10.1.


Global cudaErrorInvalidDevicePointer
This error return is deprecated as of CUDA 10.1.


Global cudaErrorAddressOfConstant
This error return is deprecated as of CUDA 3.1. Variables in constant memory may now have their address taken by the runtime
                                    via cudaGetSymbolAddress().


Global cudaErrorTextureFetchFailed
This error return is deprecated as of CUDA 3.1. Device emulation mode was removed with the CUDA 3.1 release.


Global cudaErrorTextureNotBound
This error return is deprecated as of CUDA 3.1. Device emulation mode was removed with the CUDA 3.1 release.


Global cudaErrorSynchronizationError
This error return is deprecated as of CUDA 3.1. Device emulation mode was removed with the CUDA 3.1 release.


Global cudaErrorMixedDeviceExecution
This error return is deprecated as of CUDA 3.1. Device emulation mode was removed with the CUDA 3.1 release.


Global cudaErrorNotYetImplemented
This error return is deprecated as of CUDA 4.1.


Global cudaErrorMemoryValueTooLarge
This error return is deprecated as of CUDA 3.1. Device emulation mode was removed with the CUDA 3.1 release.


Global cudaErrorPriorLaunchFailure
This error return is deprecated as of CUDA 3.1. Device emulation mode was removed with the CUDA 3.1 release.


Global cudaSharedMemConfigGlobal cudaDeviceBlockingSync
This flag was deprecated as of CUDA 4.0 and replaced with cudaDeviceScheduleBlockingSync.