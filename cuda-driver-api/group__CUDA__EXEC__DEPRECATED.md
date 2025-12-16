# CUDA Driver API

[< Previous](group__CUDA__EXEC.html) | [Next >](group__CUDA__GRAPH.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.23. Execution Control [DEPRECATED]


This section describes the deprecated execution control functions of the low-level CUDA driver application programming interface.


### Functions


CUresult cuFuncSetBlockShape (  CUfunction hfunc, int  x, int  y, int  z )
Sets the block-dimensions for the function.

CUresult cuFuncSetSharedMemConfig (  CUfunction hfunc, CUsharedconfig config )
Sets the shared memory configuration for a device function.

CUresult cuFuncSetSharedSize (  CUfunction hfunc, unsigned int  bytes )
Sets the dynamic shared-memory size for the function.

CUresult cuLaunch (  CUfunction f )
Launches a CUDA function.

CUresult cuLaunchGrid (  CUfunction f, int  grid_width, int  grid_height )
Launches a CUDA function.

CUresult cuLaunchGridAsync (  CUfunction f, int  grid_width, int  grid_height, CUstream hStream )
Launches a CUDA function.

CUresult cuParamSetSize (  CUfunction hfunc, unsigned int  numbytes )
Sets the parameter size for the function.

CUresult cuParamSetTexRef (  CUfunction hfunc, int  texunit, CUtexref hTexRef )
Adds a texture-reference to the function's argument list.

CUresult cuParamSetf (  CUfunction hfunc, int  offset, float  value )
Adds a floating-point parameter to the function's argument list.

CUresult cuParamSeti (  CUfunction hfunc, int  offset, unsigned int  value )
Adds an integer parameter to the function's argument list.

CUresult cuParamSetv (  CUfunction hfunc, int  offset, void* ptr, unsigned int  numbytes )
Adds arbitrary data to the function's argument list.


### Functions


CUresult cuFuncSetBlockShape (  CUfunction hfunc, int  x, int  y, int  z )
Sets the block-dimensions for the function.

                                 Parameters



hfunc
- Kernel to specify dimensions of
x
- X dimension
y
- Y dimension
z
- Z dimension

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_HANDLE, CUDA_ERROR_INVALID_VALUE

Deprecated

DescriptionSpecifies the x, y, and z dimensions of the thread blocks that are created when the kernel given by hfunc is launched.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuFuncSetSharedSize, cuFuncSetCacheConfig, cuFuncGetAttribute, cuParamSetSize, cuParamSeti, cuParamSetf, cuParamSetv, cuLaunch, cuLaunchGrid, cuLaunchGridAsync, cuLaunchKernel

CUresult cuFuncSetSharedMemConfig (  CUfunction hfunc, CUsharedconfig config )
Sets the shared memory configuration for a device function.

                                 Parameters



hfunc
- kernel to be given a shared memory config
config
- requested shared memory configuration

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT

Deprecated

DescriptionOn devices with configurable shared memory banks, this function will force all subsequent launches of the specified device
                              function to have the given shared memory bank size configuration. On any given launch of the function, the shared memory configuration
                              of the device will be temporarily changed if needed to suit the function's preferred configuration. Changes in shared memory
                              configuration between subsequent launches of functions, may introduce a device side synchronization point.
                              Any per-function setting of shared memory bank size set via cuFuncSetSharedMemConfig will override the context wide setting set with cuCtxSetSharedMemConfig.

Changing the shared memory bank size will not increase shared memory usage or affect occupancy of kernels, but may have major
                                 effects on performance. Larger bank sizes will allow for greater potential bandwidth to shared memory, but will change what
                                 kinds of accesses to shared memory will result in bank conflicts.

This function will do nothing on devices with fixed shared memory bank size.
The supported bank configurations are:


CU_SHARED_MEM_CONFIG_DEFAULT_BANK_SIZE: use the context's shared memory configuration when launching this function.


CU_SHARED_MEM_CONFIG_FOUR_BYTE_BANK_SIZE: set shared memory bank width to be natively four bytes when launching this function.


CU_SHARED_MEM_CONFIG_EIGHT_BYTE_BANK_SIZE: set shared memory bank width to be natively eight bytes when launching this function.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuCtxGetCacheConfig, cuCtxSetCacheConfig, cuCtxGetSharedMemConfig, cuCtxSetSharedMemConfig, cuFuncGetAttribute, cuLaunchKernel, cudaFuncSetSharedMemConfig

CUresult cuFuncSetSharedSize (  CUfunction hfunc, unsigned int  bytes )
Sets the dynamic shared-memory size for the function.

                                 Parameters



hfunc
- Kernel to specify dynamic shared-memory size for
bytes
- Dynamic shared-memory size per thread in bytes

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_HANDLE, CUDA_ERROR_INVALID_VALUE

Deprecated

DescriptionSets through bytes the amount of dynamic shared memory that will be available to each thread block when the kernel given by hfunc is launched.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuFuncSetBlockShape, cuFuncSetCacheConfig, cuFuncGetAttribute, cuParamSetSize, cuParamSeti, cuParamSetf, cuParamSetv, cuLaunch, cuLaunchGrid, cuLaunchGridAsync, cuLaunchKernel

CUresult cuLaunch (  CUfunction f )
Launches a CUDA function.

                                 Parameters



f
- Kernel to launch

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_LAUNCH_FAILED, CUDA_ERROR_LAUNCH_OUT_OF_RESOURCES, CUDA_ERROR_LAUNCH_TIMEOUT, CUDA_ERROR_LAUNCH_INCOMPATIBLE_TEXTURING, CUDA_ERROR_SHARED_OBJECT_INIT_FAILED

Deprecated

DescriptionInvokes the kernel f on a 1 x 1 x 1 grid of blocks. The block contains the number of threads specified by a previous call to cuFuncSetBlockShape().
                              The block shape, dynamic shared memory size, and parameter information must be set using cuFuncSetBlockShape(), cuFuncSetSharedSize(), cuParamSetSize(), cuParamSeti(), cuParamSetf(), and cuParamSetv() prior to calling this function.

Launching a function via cuLaunchKernel() invalidates the function's block shape, dynamic shared memory size, and parameter information. After launching via cuLaunchKernel,
                                 this state must be re-initialized prior to calling this function. Failure to do so results in undefined behavior.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuFuncSetBlockShape, cuFuncSetSharedSize, cuFuncGetAttribute, cuParamSetSize, cuParamSetf, cuParamSeti, cuParamSetv, cuLaunchGrid, cuLaunchGridAsync, cuLaunchKernel

CUresult cuLaunchGrid (  CUfunction f, int  grid_width, int  grid_height )
Launches a CUDA function.

                                 Parameters



f
- Kernel to launch
grid_width
- Width of grid in blocks
grid_height
- Height of grid in blocks

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_LAUNCH_FAILED, CUDA_ERROR_LAUNCH_OUT_OF_RESOURCES, CUDA_ERROR_LAUNCH_TIMEOUT, CUDA_ERROR_LAUNCH_INCOMPATIBLE_TEXTURING, CUDA_ERROR_SHARED_OBJECT_INIT_FAILED

Deprecated

DescriptionInvokes the kernel f on a grid_width x grid_height grid of blocks. Each block contains the number of threads specified by a previous call to cuFuncSetBlockShape().
                              The block shape, dynamic shared memory size, and parameter information must be set using cuFuncSetBlockShape(), cuFuncSetSharedSize(), cuParamSetSize(), cuParamSeti(), cuParamSetf(), and cuParamSetv() prior to calling this function.

Launching a function via cuLaunchKernel() invalidates the function's block shape, dynamic shared memory size, and parameter information. After launching via cuLaunchKernel,
                                 this state must be re-initialized prior to calling this function. Failure to do so results in undefined behavior.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuFuncSetBlockShape, cuFuncSetSharedSize, cuFuncGetAttribute, cuParamSetSize, cuParamSetf, cuParamSeti, cuParamSetv, cuLaunch, cuLaunchGridAsync, cuLaunchKernel

CUresult cuLaunchGridAsync (  CUfunction f, int  grid_width, int  grid_height, CUstream hStream )
Launches a CUDA function.

                                 Parameters



f
- Kernel to launch
grid_width
- Width of grid in blocks
grid_height
- Height of grid in blocks
hStream
- Stream identifier

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_HANDLE, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_LAUNCH_FAILED, CUDA_ERROR_LAUNCH_OUT_OF_RESOURCES, CUDA_ERROR_LAUNCH_TIMEOUT, CUDA_ERROR_LAUNCH_INCOMPATIBLE_TEXTURING, CUDA_ERROR_SHARED_OBJECT_INIT_FAILED

Deprecated

DescriptionInvokes the kernel f on a grid_width x grid_height grid of blocks. Each block contains the number of threads specified by a previous call to cuFuncSetBlockShape().
                              The block shape, dynamic shared memory size, and parameter information must be set using cuFuncSetBlockShape(), cuFuncSetSharedSize(), cuParamSetSize(), cuParamSeti(), cuParamSetf(), and cuParamSetv() prior to calling this function.

Launching a function via cuLaunchKernel() invalidates the function's block shape, dynamic shared memory size, and parameter information. After launching via cuLaunchKernel,
                                 this state must be re-initialized prior to calling this function. Failure to do so results in undefined behavior.


Note:

In certain cases where cubins are created with no ABI (i.e., using ptxas--abi-compileno), this function may serialize kernel launches. The CUDA driver retains asynchronous behavior by growing the per-thread stack
                                             as needed per launch and not shrinking it afterwards.


This function uses standard  default stream semantics.


Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuFuncSetBlockShape, cuFuncSetSharedSize, cuFuncGetAttribute, cuParamSetSize, cuParamSetf, cuParamSeti, cuParamSetv, cuLaunch, cuLaunchGrid, cuLaunchKernel

CUresult cuParamSetSize (  CUfunction hfunc, unsigned int  numbytes )
Sets the parameter size for the function.

                                 Parameters



hfunc
- Kernel to set parameter size for
numbytes
- Size of parameter list in bytes

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE

Deprecated

DescriptionSets through numbytes the total size in bytes needed by the function parameters of the kernel corresponding to hfunc.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuFuncSetBlockShape, cuFuncSetSharedSize, cuFuncGetAttribute, cuParamSetf, cuParamSeti, cuParamSetv, cuLaunch, cuLaunchGrid, cuLaunchGridAsync, cuLaunchKernel

CUresult cuParamSetTexRef (  CUfunction hfunc, int  texunit, CUtexref hTexRef )
Adds a texture-reference to the function's argument list.

                                 Parameters



hfunc
- Kernel to add texture-reference to
texunit
- Texture unit (must be CU_PARAM_TR_DEFAULT)

hTexRef
- Texture-reference to add to argument list

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE

Deprecated

DescriptionMakes the CUDA array or linear memory bound to the texture reference hTexRef available to a device program as a texture. In this version of CUDA, the texture-reference must be obtained via cuModuleGetTexRef() and the texunit parameter must be set to CU_PARAM_TR_DEFAULT.


Note:Note that this function may also return error codes from previous, asynchronous launches.

CUresult cuParamSetf (  CUfunction hfunc, int  offset, float  value )
Adds a floating-point parameter to the function's argument list.

                                 Parameters



hfunc
- Kernel to add parameter to
offset
- Offset to add parameter to argument list
value
- Value of parameter

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE

Deprecated

DescriptionSets a floating-point parameter that will be specified the next time the kernel corresponding to hfunc will be invoked. offset is a byte offset.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuFuncSetBlockShape, cuFuncSetSharedSize, cuFuncGetAttribute, cuParamSetSize, cuParamSeti, cuParamSetv, cuLaunch, cuLaunchGrid, cuLaunchGridAsync, cuLaunchKernel

CUresult cuParamSeti (  CUfunction hfunc, int  offset, unsigned int  value )
Adds an integer parameter to the function's argument list.

                                 Parameters



hfunc
- Kernel to add parameter to
offset
- Offset to add parameter to argument list
value
- Value of parameter

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE

Deprecated

DescriptionSets an integer parameter that will be specified the next time the kernel corresponding to hfunc will be invoked. offset is a byte offset.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuFuncSetBlockShape, cuFuncSetSharedSize, cuFuncGetAttribute, cuParamSetSize, cuParamSetf, cuParamSetv, cuLaunch, cuLaunchGrid, cuLaunchGridAsync, cuLaunchKernel

CUresult cuParamSetv (  CUfunction hfunc, int  offset, void* ptr, unsigned int  numbytes )
Adds arbitrary data to the function's argument list.

                                 Parameters



hfunc
- Kernel to add data to
offset
- Offset to add data to argument list
ptr
- Pointer to arbitrary data
numbytes
- Size of data to copy in bytes

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE

Deprecated

DescriptionCopies an arbitrary amount of data (specified in numbytes) from ptr into the parameter space of the kernel corresponding to hfunc. offset is a byte offset.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuFuncSetBlockShape, cuFuncSetSharedSize, cuFuncGetAttribute, cuParamSetSize, cuParamSetf, cuParamSeti, cuLaunch, cuLaunchGrid, cuLaunchGridAsync, cuLaunchKernel


---