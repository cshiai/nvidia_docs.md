# CUDA Driver API

[< Previous](group__CUDA__D3D11__DEPRECATED.html) | [Next >](group__CUDA__EGL.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.44. VDPAU Interoperability


This section describes the VDPAU interoperability functions of the low-level CUDA driver application programming interface.


### Functions


CUresult cuGraphicsVDPAURegisterOutputSurface (  CUgraphicsResource* pCudaResource, VdpOutputSurface vdpSurface, unsigned int  flags )
Registers a VDPAU VdpOutputSurface object.

CUresult cuGraphicsVDPAURegisterVideoSurface (  CUgraphicsResource* pCudaResource, VdpVideoSurface vdpSurface, unsigned int  flags )
Registers a VDPAU VdpVideoSurface object.

CUresult cuVDPAUCtxCreate (  CUcontext* pCtx, unsigned int  flags, CUdevice device, VdpDevice vdpDevice, VdpGetProcAddress* vdpGetProcAddress )
Create a CUDA context for interoperability with VDPAU.

CUresult cuVDPAUGetDevice (  CUdevice* pDevice, VdpDevice vdpDevice, VdpGetProcAddress* vdpGetProcAddress )
Gets the CUDA device associated with a VDPAU device.


### Functions


CUresult cuGraphicsVDPAURegisterOutputSurface (  CUgraphicsResource* pCudaResource, VdpOutputSurface vdpSurface, unsigned int  flags )
Registers a VDPAU VdpOutputSurface object.

                                 Parameters



pCudaResource
- Pointer to the returned object handle
vdpSurface
- The VdpOutputSurface to be registered
flags
- Map flags

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_HANDLE, CUDA_ERROR_ALREADY_MAPPED, CUDA_ERROR_INVALID_CONTEXT,


Description
Registers the VdpOutputSurface specified by vdpSurface for access by CUDA. A handle to the registered object is returned as pCudaResource. The surface's intended usage is specified using flags, as follows:


CU_GRAPHICS_MAP_RESOURCE_FLAGS_NONE: Specifies no hints about how this resource will be used. It is therefore assumed that
                                          this resource will be read from and written to by CUDA. This is the default value.


CU_GRAPHICS_MAP_RESOURCE_FLAGS_READ_ONLY: Specifies that CUDA will not write to this resource.

CU_GRAPHICS_MAP_RESOURCE_FLAGS_WRITE_DISCARD: Specifies that CUDA will not read from this resource and will write over the
                                          entire contents of the resource, so none of the data previously stored in the resource will be preserved.


The VdpOutputSurface is presented as an array of subresources that may be accessed using pointers returned by cuGraphicsSubResourceGetMappedArray. The exact number of valid arrayIndex values depends on the VDPAU surface format. The mapping is shown in the table below. mipLevel must be 0.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuCtxCreate, cuVDPAUCtxCreate, cuGraphicsVDPAURegisterVideoSurface, cuGraphicsUnregisterResource, cuGraphicsResourceSetMapFlags, cuGraphicsMapResources, cuGraphicsUnmapResources, cuGraphicsSubResourceGetMappedArray, cuVDPAUGetDevice, cudaGraphicsVDPAURegisterOutputSurface

CUresult cuGraphicsVDPAURegisterVideoSurface (  CUgraphicsResource* pCudaResource, VdpVideoSurface vdpSurface, unsigned int  flags )
Registers a VDPAU VdpVideoSurface object.

                                 Parameters



pCudaResource
- Pointer to the returned object handle
vdpSurface
- The VdpVideoSurface to be registered
flags
- Map flags

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_HANDLE, CUDA_ERROR_ALREADY_MAPPED, CUDA_ERROR_INVALID_CONTEXT,


Description
Registers the VdpVideoSurface specified by vdpSurface for access by CUDA. A handle to the registered object is returned as pCudaResource. The surface's intended usage is specified using flags, as follows:


CU_GRAPHICS_MAP_RESOURCE_FLAGS_NONE: Specifies no hints about how this resource will be used. It is therefore assumed that
                                          this resource will be read from and written to by CUDA. This is the default value.


CU_GRAPHICS_MAP_RESOURCE_FLAGS_READ_ONLY: Specifies that CUDA will not write to this resource.

CU_GRAPHICS_MAP_RESOURCE_FLAGS_WRITE_DISCARD: Specifies that CUDA will not read from this resource and will write over the
                                          entire contents of the resource, so none of the data previously stored in the resource will be preserved.


The VdpVideoSurface is presented as an array of subresources that may be accessed using pointers returned by cuGraphicsSubResourceGetMappedArray. The exact number of valid arrayIndex values depends on the VDPAU surface format. The mapping is shown in the table below. mipLevel must be 0.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuCtxCreate, cuVDPAUCtxCreate, cuGraphicsVDPAURegisterOutputSurface, cuGraphicsUnregisterResource, cuGraphicsResourceSetMapFlags, cuGraphicsMapResources, cuGraphicsUnmapResources, cuGraphicsSubResourceGetMappedArray, cuVDPAUGetDevice, cudaGraphicsVDPAURegisterVideoSurface

CUresult cuVDPAUCtxCreate (  CUcontext* pCtx, unsigned int  flags, CUdevice device, VdpDevice vdpDevice, VdpGetProcAddress* vdpGetProcAddress )
Create a CUDA context for interoperability with VDPAU.

                                 Parameters



pCtx
- Returned CUDA context
flags
- Options for CUDA context creation
device
- Device on which to create the context
vdpDevice
- The VdpDevice to interop with
vdpGetProcAddress
- VDPAU's VdpGetProcAddress function pointer

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_OUT_OF_MEMORY

Description
Creates a new CUDA context, initializes VDPAU interoperability, and associates the CUDA context with the calling thread. It
                                 must be called before performing any other VDPAU interoperability operations. It may fail if the needed VDPAU driver facilities
                                 are not available. For usage of the flags parameter, see cuCtxCreate().


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuCtxCreate, cuGraphicsVDPAURegisterVideoSurface, cuGraphicsVDPAURegisterOutputSurface, cuGraphicsUnregisterResource, cuGraphicsResourceSetMapFlags, cuGraphicsMapResources, cuGraphicsUnmapResources, cuGraphicsSubResourceGetMappedArray, cuVDPAUGetDevice

CUresult cuVDPAUGetDevice (  CUdevice* pDevice, VdpDevice vdpDevice, VdpGetProcAddress* vdpGetProcAddress )
Gets the CUDA device associated with a VDPAU device.

                                 Parameters



pDevice
- Device associated with vdpDevice
vdpDevice
- A VdpDevice handle
vdpGetProcAddress
- VDPAU's VdpGetProcAddress function pointer

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE

Description
Returns in *pDevice the CUDA device associated with a vdpDevice, if applicable.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuCtxCreate, cuVDPAUCtxCreate, cuGraphicsVDPAURegisterVideoSurface, cuGraphicsVDPAURegisterOutputSurface, cuGraphicsUnregisterResource, cuGraphicsResourceSetMapFlags, cuGraphicsMapResources, cuGraphicsUnmapResources, cuGraphicsSubResourceGetMappedArray, cudaVDPAUGetDevice


---