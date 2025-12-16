# CUDA Driver API

Global CU_CTX_BLOCKING_SYNC
This flag was deprecated as of CUDA 4.0 and was replaced with CU_CTX_SCHED_BLOCKING_SYNC.


Global CU_CTX_MAP_HOST
This flag was deprecated as of CUDA 11.0 and it no longer has any effect. All contexts as of CUDA 3.2 behave as though the
                                    flag is enabled.


Global CU_DEVICE_P2P_ATTRIBUTE_ACCESS_ACCESS_SUPPORTED
use CU_DEVICE_P2P_ATTRIBUTE_CUDA_ARRAY_ACCESS_SUPPORTED instead


Global CU_JIT_NEW_SM3X_OPT
This jit option is deprecated and should not be used.


Global CU_JIT_LTO
Enable link-time optimization (-dlto) for device code (Disabled by default).

                                    This option is not supported on 32-bit platforms.


                                    Option type: int


                                    Applies to: compiler and linker


Global CU_JIT_FTZ
Control single-precision denormals (-ftz) support (0: false, default). 1 : flushes denormal values to zero 0 : preserves denormal
                                    values Option type: int


                                    Applies to: link-time optimization specified with CU_JIT_LTO


Global CU_JIT_PREC_DIV
Control single-precision floating-point division and reciprocals (-prec-div) support (1: true, default). 1 : Enables the IEEE
                                    round-to-nearest mode 0 : Enables the fast approximation mode Option type: int


                                    Applies to: link-time optimization specified with CU_JIT_LTO


Global CU_JIT_PREC_SQRT
Control single-precision floating-point square root (-prec-sqrt) support (1: true, default). 1 : Enables the IEEE round-to-nearest
                                    mode 0 : Enables the fast approximation mode Option type: int


                                    Applies to: link-time optimization specified with CU_JIT_LTO


Global CU_JIT_FMA
Enable/Disable the contraction of floating-point multiplies and adds/subtracts into floating-point multiply-add (-fma) operations
                                    (1: Enable, default; 0: Disable). Option type: int


                                    Applies to: link-time optimization specified with CU_JIT_LTO


Global CU_JIT_REFERENCED_KERNEL_NAMES
Array of kernel names that should be preserved at link time while others can be removed.

                                    Must contain CU_JIT_REFERENCED_KERNEL_COUNT entries.


                                    Note that kernel names can be mangled by the compiler in which case the mangled name needs to be specified.


                                    Wildcard "*" can be used to represent zero or more characters instead of specifying the full or mangled name.


                                    It is important to note that the wildcard "*" is also added implicitly. For example, specifying "foo" will match "foobaz",
                                    "barfoo", "barfoobaz" and thus preserve all kernels with those names. This can be avoided by providing a more specific name
                                    like "barfoobaz".


                                    Option type: const char 


                                    Applies to: dynamic linker only


Global CU_JIT_REFERENCED_KERNEL_COUNT
Number of entries in CU_JIT_REFERENCED_KERNEL_NAMES array.


                                    Option type: unsigned int


                                    Applies to: dynamic linker only


Global CU_JIT_REFERENCED_VARIABLE_NAMES
Array of variable names (__device__ and/or __constant__) that should be preserved at link time while others can be removed.

                                    Must contain CU_JIT_REFERENCED_VARIABLE_COUNT entries.


                                    Note that variable names can be mangled by the compiler in which case the mangled name needs to be specified.


                                    Wildcard "*" can be used to represent zero or more characters instead of specifying the full or mangled name.


                                    It is important to note that the wildcard "*" is also added implicitly. For example, specifying "foo" will match "foobaz",
                                    "barfoo", "barfoobaz" and thus preserve all variables with those names. This can be avoided by providing a more specific name
                                    like "barfoobaz".


                                    Option type: const char 


                                    Applies to: link-time optimization specified with CU_JIT_LTO


Global CU_JIT_REFERENCED_VARIABLE_COUNT
Number of entries in CU_JIT_REFERENCED_VARIABLE_NAMES array.


                                    Option type: unsigned int


                                    Applies to: link-time optimization specified with CU_JIT_LTO


Global CU_JIT_OPTIMIZE_UNUSED_DEVICE_VARIABLES
This option serves as a hint to enable the JIT compiler/linker to remove constant (__constant__) and device (__device__) variables
                                    unreferenced in device code (Disabled by default).


                                    Note that host references to constant and device variables using APIs like cuModuleGetGlobal() with this option specified may result in undefined behavior unless the variables are explicitly specified using CU_JIT_REFERENCED_VARIABLE_NAMES.


                                    Option type: int


                                    Applies to: link-time optimization specified with CU_JIT_LTO


Global CU_JIT_INPUT_NVVM
High-level intermediate code for link-time optimization

                                    Applicable options: NVVM compiler options, PTX compiler options


Global CUDA_ERROR_PROFILER_NOT_INITIALIZED
This error return is deprecated as of CUDA 5.0. It is no longer an error to attempt to enable/disable the profiling via cuProfilerStart or cuProfilerStop without initialization.


Global CUDA_ERROR_PROFILER_ALREADY_STARTED
This error return is deprecated as of CUDA 5.0. It is no longer an error to call cuProfilerStart() when profiling is already enabled.


Global CUDA_ERROR_PROFILER_ALREADY_STOPPED
This error return is deprecated as of CUDA 5.0. It is no longer an error to call cuProfilerStop() when profiling is already disabled.


Global CUDA_ERROR_CONTEXT_ALREADY_CURRENT
This error return is deprecated as of CUDA 3.2. It is no longer an error to attempt to push the active context via cuCtxPushCurrent().


Global CUsharedconfigGlobal cuDeviceComputeCapabilityGlobal cuDeviceGetPropertiesGlobal cuCtxAttachGlobal cuCtxDetachGlobal cuCtxGetSharedMemConfigGlobal cuCtxSetSharedMemConfigGlobal cuModuleGetSurfRefGlobal cuModuleGetTexRefGlobal cuLaunchCooperativeKernelMultiDevice
This function is deprecated as of CUDA 11.3.


Global cuFuncSetBlockShapeGlobal cuFuncSetSharedMemConfigGlobal cuFuncSetSharedSizeGlobal cuLaunchGlobal cuLaunchGridGlobal cuLaunchGridAsyncGlobal cuParamSetfGlobal cuParamSetiGlobal cuParamSetSizeGlobal cuParamSetTexRefGlobal cuParamSetvGlobal cuTexRefCreateGlobal cuTexRefDestroyGlobal cuTexRefGetAddressGlobal cuTexRefGetAddressModeGlobal cuTexRefGetArrayGlobal cuTexRefGetBorderColorGlobal cuTexRefGetFilterModeGlobal cuTexRefGetFlagsGlobal cuTexRefGetFormatGlobal cuTexRefGetMaxAnisotropyGlobal cuTexRefGetMipmapFilterModeGlobal cuTexRefGetMipmapLevelBiasGlobal cuTexRefGetMipmapLevelClampGlobal cuTexRefGetMipmappedArrayGlobal cuTexRefSetAddressGlobal cuTexRefSetAddress2DGlobal cuTexRefSetAddressModeGlobal cuTexRefSetArrayGlobal cuTexRefSetBorderColorGlobal cuTexRefSetFilterModeGlobal cuTexRefSetFlagsGlobal cuTexRefSetFormatGlobal cuTexRefSetMaxAnisotropyGlobal cuTexRefSetMipmapFilterModeGlobal cuTexRefSetMipmapLevelBiasGlobal cuTexRefSetMipmapLevelClampGlobal cuTexRefSetMipmappedArrayGlobal cuSurfRefGetArrayGlobal cuSurfRefSetArrayGlobal cuProfilerInitializeGlobal cuGLCtxCreate
This function is deprecated as of Cuda 5.0.


Global cuGLInit
This function is deprecated as of Cuda 3.0.


Global cuGLMapBufferObject
This function is deprecated as of Cuda 3.0.


Global cuGLMapBufferObjectAsync
This function is deprecated as of Cuda 3.0.


Global cuGLRegisterBufferObject
This function is deprecated as of Cuda 3.0.


Global cuGLSetBufferObjectMapFlags
This function is deprecated as of Cuda 3.0.


Global cuGLUnmapBufferObject
This function is deprecated as of Cuda 3.0.


Global cuGLUnmapBufferObjectAsync
This function is deprecated as of Cuda 3.0.


Global cuGLUnregisterBufferObject
This function is deprecated as of Cuda 3.0.


Global cuD3D9MapResources
This function is deprecated as of CUDA 3.0.


Global cuD3D9RegisterResource
This function is deprecated as of CUDA 3.0.


Global cuD3D9ResourceGetMappedArray
This function is deprecated as of CUDA 3.0.


Global cuD3D9ResourceGetMappedPitch
This function is deprecated as of CUDA 3.0.


Global cuD3D9ResourceGetMappedPointer
This function is deprecated as of CUDA 3.0.


Global cuD3D9ResourceGetMappedSize
This function is deprecated as of CUDA 3.0.


Global cuD3D9ResourceGetSurfaceDimensions
This function is deprecated as of CUDA 3.0.


Global cuD3D9ResourceSetMapFlags
This function is deprecated as of Cuda 3.0.


Global cuD3D9UnmapResources
This function is deprecated as of CUDA 3.0.


Global cuD3D9UnregisterResource
This function is deprecated as of CUDA 3.0.


Global cuD3D10CtxCreate
This function is deprecated as of CUDA 5.0.


Global cuD3D10CtxCreateOnDevice
This function is deprecated as of CUDA 5.0.


Global cuD3D10GetDirect3DDevice
This function is deprecated as of CUDA 5.0.


Global cuD3D10MapResources
This function is deprecated as of CUDA 3.0.


Global cuD3D10RegisterResource
This function is deprecated as of CUDA 3.0.


Global cuD3D10ResourceGetMappedArray
This function is deprecated as of CUDA 3.0.


Global cuD3D10ResourceGetMappedPitch
This function is deprecated as of CUDA 3.0.


Global cuD3D10ResourceGetMappedPointer
This function is deprecated as of CUDA 3.0.


Global cuD3D10ResourceGetMappedSize
This function is deprecated as of CUDA 3.0.


Global cuD3D10ResourceGetSurfaceDimensions
This function is deprecated as of CUDA 3.0.


Global cuD3D10ResourceSetMapFlags
This function is deprecated as of CUDA 3.0.


Global cuD3D10UnmapResources
This function is deprecated as of CUDA 3.0.


Global cuD3D10UnregisterResource
This function is deprecated as of CUDA 3.0.


Global cuD3D11CtxCreate
This function is deprecated as of CUDA 5.0.


Global cuD3D11CtxCreateOnDevice
This function is deprecated as of CUDA 5.0.


Global cuD3D11GetDirect3DDevice
This function is deprecated as of CUDA 5.0.