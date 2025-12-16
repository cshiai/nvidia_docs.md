# CUDA Runtime API

[< Previous](group__CUDART__HIGHLEVEL.html) | [Next >](group__CUDART__PROFILER.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 6.35. Interactions with the CUDA Driver API


This section describes the interactions between the CUDA Driver API and the CUDA Runtime API


Execution Contexts


The CUDA Runtime provides [cudaExecutionContext_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g06d5848ef843b4254502134742502fe0) as an abstraction over driver-level contexts—specifically, green contexts and the primary context.


There are two primary ways to obtain an execution context:


 - [cudaDeviceGetExecutionCtx](group__CUDART__EXECUTION__CONTEXT.html#group__CUDART__EXECUTION__CONTEXT_1g485f61e7d1bd079170e2d0c30dcddac5): Returns the execution context that corresponds to the primary context of the specified device.
 - [cudaGreenCtxCreate](group__CUDART__EXECUTION__CONTEXT.html#group__CUDART__EXECUTION__CONTEXT_1g382a6e584f1e94865254f90080ff8f2c): Creates a green context with the specified resources and returns an execution context.


Note: Developers should treat [cudaExecutionContext_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g06d5848ef843b4254502134742502fe0) as an opaque handle and avoid assumptions about its underlying representation. The CUDA Runtime does not provide a way to convert this handle into a [CUcontext](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gf9f5bd81658f866613785b3a0bb7d7d9) or [CUgreenCtx](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g453cb79a1ceb13bec502a9c5f06a0268).


Primary Context (aka Device Execution Context)


The primary context is the default execution context associated with a device in the Runtime. It can be obtained via a call to [cudaDeviceGetExecutionCtx()](group__CUDART__EXECUTION__CONTEXT.html#group__CUDART__EXECUTION__CONTEXT_1g485f61e7d1bd079170e2d0c30dcddac5). There is a one-to-one mapping between CUDA devices in the runtime and their primary contexts within a process.


From the CUDA Runtime’s perspective, a device and its primary context are functionally synonymous.


Unless explicitly overridden, either by making a different context current via the Driver API (e.g., [cuCtxSetCurrent()](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__CTX.html#group__CUDA__CTX_1gbe562ee6258b4fcc272ca6478ca2a2f7)) or by using an explicit execution context handle, the Runtime will implicitly initialize and use the primary context for API calls as needed.


Initialization and Tear-Down


Unless an explicit execution context is specified (see “Execution Context Management” for APIs), CUDA Runtime API calls operate on the CUDA Driver [CUcontext](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gf9f5bd81658f866613785b3a0bb7d7d9) which is current to the calling host thread. If no [CUcontext](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gf9f5bd81658f866613785b3a0bb7d7d9) is current to the calling thread when a CUDA Runtime API call which requires an active context is made, then the primary context (device execution context) for a device will be selected, made current to the calling thread, and initialized. The context will be initialized using the parameters specified by the CUDA Runtime API functions [cudaSetDeviceFlags()](group__CUDART__DEVICE.html#group__CUDART__DEVICE_1g69e73c7dda3fc05306ae7c811a690fac), [cudaD3D9SetDirect3DDevice()](group__CUDART__D3D9.html#group__CUDART__D3D9_1g0733a6f0bdc8aca6c6812da66c6d814a), [cudaD3D10SetDirect3DDevice()](group__CUDART__D3D10__DEPRECATED.html#group__CUDART__D3D10__DEPRECATED_1g7c942225222284fbfc3794a4ed6edf98), [cudaD3D11SetDirect3DDevice()](group__CUDART__D3D11__DEPRECATED.html#group__CUDART__D3D11__DEPRECATED_1g533524c773e7ca4ef57c0698b157d670), [cudaGLSetGLDevice()](group__CUDART__OPENGL__DEPRECATED.html#group__CUDART__OPENGL__DEPRECATED_1g88fddf479c2b597af49fd839bb42345e), and [cudaVDPAUSetVDPAUDevice()](group__CUDART__VDPAU.html#group__CUDART__VDPAU_1g2a9ccfe8e6c87fe694bafd8cfcc67586). Note that these functions will fail with [cudaErrorSetOnActiveProcess](group__CUDART__TYPES.html#group__CUDART__TYPES_1gg3f51e3575c2178246db0a94a430e0038a906ddf08d574274bf7334adb1497550) if they are called when the primary context for the specified device has already been initialized, except for [cudaSetDeviceFlags()](group__CUDART__DEVICE.html#group__CUDART__DEVICE_1g69e73c7dda3fc05306ae7c811a690fac) which will simply overwrite the previous settings.


The function [cudaInitDevice()](group__CUDART__DEVICE.html#group__CUDART__DEVICE_1gac04a5d82168676b20121ca870919419) ensures that the primary context is initialized for the requested device but does not make it current to the calling thread.


The function [cudaSetDevice()](group__CUDART__DEVICE.html#group__CUDART__DEVICE_1g159587909ffa0791bbe4b40187a4c6bb) initializes the primary context for the specified device and makes it current to the calling thread by calling [cuCtxSetCurrent()](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__CTX.html#group__CUDA__CTX_1gbe562ee6258b4fcc272ca6478ca2a2f7).


Primary contexts will remain active until they are explicitly deinitialized using [cudaDeviceReset()](group__CUDART__DEVICE.html#group__CUDART__DEVICE_1gef69dd5c6d0206c2b8d099abac61f217). The function [cudaDeviceReset()](group__CUDART__DEVICE.html#group__CUDART__DEVICE_1gef69dd5c6d0206c2b8d099abac61f217) will deinitialize the primary context for the calling thread's current device immediately. The context will remain current to all of the threads that it was current to. The next CUDA Runtime API call on any thread which requires an active context will trigger the reinitialization of that device's primary context.


Note that primary contexts are shared resources. It is recommended that the primary context not be reset except just before exit or to recover from an unspecified launch failure.


CUcontext Interoperability


Note that the use of multiple [CUcontext](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gf9f5bd81658f866613785b3a0bb7d7d9) s per device within a single process will substantially degrade performance and is strongly discouraged. Instead, it is highly recommended to either use execution contexts [cudaExecutionContext_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g06d5848ef843b4254502134742502fe0) or the implicit one-to-one device-to-primary context mapping for the process provided by the CUDA Runtime API.


If a non-primary [CUcontext](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gf9f5bd81658f866613785b3a0bb7d7d9) created by the CUDA Driver API is current to a thread then the CUDA Runtime API calls to that thread will operate on that [CUcontext](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gf9f5bd81658f866613785b3a0bb7d7d9), with some exceptions listed below. Interoperability between data types is discussed in the following sections.


The function [cudaDeviceEnablePeerAccess()](group__CUDART__PEER.html#group__CUDART__PEER_1g2b0adabf90db37e5cfddc92cbb2589f3) and the rest of the peer access API may not be called when a non-primary CUcontext is current. To use the peer access APIs with a context created using the CUDA Driver API, it is necessary that the CUDA Driver API be used to access these features.


All CUDA Runtime API state (e.g, global variables' addresses and values) travels with its underlying [CUcontext](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gf9f5bd81658f866613785b3a0bb7d7d9). In particular, if a [CUcontext](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gf9f5bd81658f866613785b3a0bb7d7d9) is moved from one thread to another then all CUDA Runtime API state will move to that thread as well.


Please note that attaching to legacy CUcontext (those with a version of 3010 as returned by [cuCtxGetApiVersion()](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__CTX.html#group__CUDA__CTX_1g088a90490dafca5893ef6fbebc8de8fb)) is not possible. The CUDA Runtime will return [cudaErrorIncompatibleDriverContext](group__CUDART__TYPES.html#group__CUDART__TYPES_1gg3f51e3575c2178246db0a94a430e0038bfc1b14096f31fc7b43c08397af90856) in such cases.


Interactions between CUstream and cudaStream_t


The types [CUstream](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gb946c7f02e09efd788a204718015d88a) and [cudaStream_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1ge15d9c8b7a240312b533d6122558085a) are identical and may be used interchangeably.


Interactions between CUevent and cudaEvent_t


The types [CUevent](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g6d740185cf0953636d4ae37f68d7559b) and [cudaEvent_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1gea2f543a9fc0e52fe4ae712920fd1247) are identical and may be used interchangeably.


Interactions between CUarray and cudaArray_t


The types [CUarray](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gd550651524a56766b60f10f0e7628042) and struct cudaArray * represent the same data type and may be used interchangeably by casting the two types between each other.


In order to use a [CUarray](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gd550651524a56766b60f10f0e7628042) in a CUDA Runtime API function which takes a struct cudaArray *, it is necessary to explicitly cast the [CUarray](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gd550651524a56766b60f10f0e7628042) to a struct cudaArray *.


In order to use a struct cudaArray * in a CUDA Driver API function which takes a [CUarray](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gd550651524a56766b60f10f0e7628042), it is necessary to explicitly cast the struct cudaArray * to a [CUarray](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gd550651524a56766b60f10f0e7628042) .


Interactions between CUgraphicsResource and cudaGraphicsResource_t


The types [CUgraphicsResource](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gc0c4e1704647178d9c5ba3be46517dcd) and [cudaGraphicsResource_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1gf58dd8d3c7a65714ff7f5459adbf7e6f) represent the same data type and may be used interchangeably by casting the two types between each other.


In order to use a [CUgraphicsResource](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gc0c4e1704647178d9c5ba3be46517dcd) in a CUDA Runtime API function which takes a [cudaGraphicsResource_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1gf58dd8d3c7a65714ff7f5459adbf7e6f), it is necessary to explicitly cast the [CUgraphicsResource](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gc0c4e1704647178d9c5ba3be46517dcd) to a [cudaGraphicsResource_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1gf58dd8d3c7a65714ff7f5459adbf7e6f).


In order to use a [cudaGraphicsResource_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1gf58dd8d3c7a65714ff7f5459adbf7e6f) in a CUDA Driver API function which takes a [CUgraphicsResource](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gc0c4e1704647178d9c5ba3be46517dcd), it is necessary to explicitly cast the [cudaGraphicsResource_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1gf58dd8d3c7a65714ff7f5459adbf7e6f) to a [CUgraphicsResource](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gc0c4e1704647178d9c5ba3be46517dcd).


Interactions between CUtexObject and cudaTextureObject_t


The types [CUtexObject](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g65fb6720dea73d56db0b4d4974be052d) and [cudaTextureObject_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g83eb271ebc4cb2817e66d7c752f0c29b) represent the same data type and may be used interchangeably by casting the two types between each other.


In order to use a [CUtexObject](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g65fb6720dea73d56db0b4d4974be052d) in a CUDA Runtime API function which takes a [cudaTextureObject_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g83eb271ebc4cb2817e66d7c752f0c29b), it is necessary to explicitly cast the [CUtexObject](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g65fb6720dea73d56db0b4d4974be052d) to a [cudaTextureObject_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g83eb271ebc4cb2817e66d7c752f0c29b).


In order to use a [cudaTextureObject_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g83eb271ebc4cb2817e66d7c752f0c29b) in a CUDA Driver API function which takes a [CUtexObject](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g65fb6720dea73d56db0b4d4974be052d), it is necessary to explicitly cast the [cudaTextureObject_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g83eb271ebc4cb2817e66d7c752f0c29b) to a [CUtexObject](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g65fb6720dea73d56db0b4d4974be052d).


Interactions between CUsurfObject and cudaSurfaceObject_t


The types [CUsurfObject](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g4acc685a8412637d05668e30e984e220) and [cudaSurfaceObject_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1gbe57cf2ccbe7f9d696f18808dd634c0a) represent the same data type and may be used interchangeably by casting the two types between each other.


In order to use a [CUsurfObject](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g4acc685a8412637d05668e30e984e220) in a CUDA Runtime API function which takes a [cudaSurfaceObject_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1gbe57cf2ccbe7f9d696f18808dd634c0a), it is necessary to explicitly cast the [CUsurfObject](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g4acc685a8412637d05668e30e984e220) to a [cudaSurfaceObject_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1gbe57cf2ccbe7f9d696f18808dd634c0a).


In order to use a [cudaSurfaceObject_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1gbe57cf2ccbe7f9d696f18808dd634c0a) in a CUDA Driver API function which takes a [CUsurfObject](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g4acc685a8412637d05668e30e984e220), it is necessary to explicitly cast the [cudaSurfaceObject_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1gbe57cf2ccbe7f9d696f18808dd634c0a) to a [CUsurfObject](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g4acc685a8412637d05668e30e984e220).


Interactions between CUfunction and cudaFunction_t


The types [CUfunction](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gba6128b948022f495706d93bc2cea9c8) and [cudaFunction_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g6ac3a22cc596d09ac07cdafb8a4638cf) represent the same data type and may be used interchangeably by casting the two types between each other.


In order to use a [cudaFunction_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g6ac3a22cc596d09ac07cdafb8a4638cf) in a CUDA Driver API function which takes a [CUfunction](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gba6128b948022f495706d93bc2cea9c8), it is necessary to explicitly cast the [cudaFunction_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g6ac3a22cc596d09ac07cdafb8a4638cf) to a [CUfunction](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1gba6128b948022f495706d93bc2cea9c8).


Interactions between CUkernel and cudaKernel_t


The types [CUkernel](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g612028921e5736db673e4307589989ed) and [cudaKernel_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g0b33f204b307b3154aa4f005a3c8a46a) represent the same data type and may be used interchangeably by casting the two types between each other.


In order to use a [cudaKernel_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g0b33f204b307b3154aa4f005a3c8a46a) in a CUDA Driver API function which takes a [CUkernel](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g612028921e5736db673e4307589989ed), it is necessary to explicitly cast the [cudaKernel_t](group__CUDART__TYPES.html#group__CUDART__TYPES_1g0b33f204b307b3154aa4f005a3c8a46a) to a [CUkernel](https://docs.nvidia.com/cuda/cuda-driver-api/group__CUDA__TYPES.html#group__CUDA__TYPES_1g612028921e5736db673e4307589989ed).


### Functions


__host__
                           ​cudaError_t cudaGetFuncBySymbol (  cudaFunction_t* functionPtr, const void* symbolPtr )
Get pointer to device entry function that matches entry function symbolPtr.

__host__
                           ​cudaError_t cudaGetKernel (  cudaKernel_t* kernelPtr, const void* entryFuncAddr )
Get pointer to device kernel that matches entry function entryFuncAddr.


### Functions


__host__
                              ​cudaError_t cudaGetFuncBySymbol (  cudaFunction_t* functionPtr, const void* symbolPtr )
Get pointer to device entry function that matches entry function symbolPtr.


                                 Parameters



functionPtr
- Returns the device entry function
symbolPtr
- Pointer to device entry function to search for

Returns
cudaSuccess

Description
Returns in functionPtr the device entry function corresponding to the symbol symbolPtr.

__host__
                              ​cudaError_t cudaGetKernel (  cudaKernel_t* kernelPtr, const void* entryFuncAddr )
Get pointer to device kernel that matches entry function entryFuncAddr.


                                 Parameters



kernelPtr
- Returns the device kernel
entryFuncAddr
- Address of device entry function to search kernel for

Returns
cudaSuccess

Description
Returns in kernelPtr the device kernel corresponding to the entry function entryFuncAddr.

Note that it is possible that there are multiple symbols belonging to different translation units with the same entryFuncAddr registered with this CUDA Runtime and so the order which the translation units are loaded and registered with the CUDA Runtime
                                 can lead to differing return pointers in kernelPtr . Suggested methods of ensuring uniqueness are to limit visibility of __global__ device functions by using static or hidden
                                 visibility attribute in the respective translation units.


See also:
cudaGetKernel (C++ API)


---