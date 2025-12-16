# CUDA Driver API

[< Previous](group__CUDA__D3D11.html) | [Next >](group__CUDA__VDPAU.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.43.1. Direct3D 11 Interoperability [DEPRECATED]


## [[Direct3D 11 Interoperability](group__CUDA__D3D11.html#group__CUDA__D3D11)]


This section describes deprecated Direct3D 11 interoperability functionality.


### Functions


CUresult cuD3D11CtxCreate (  CUcontext* pCtx, CUdevice* pCudaDevice, unsigned int  Flags, ID3D11Device* pD3DDevice )
Create a CUDA context for interoperability with Direct3D 11.

CUresult cuD3D11CtxCreateOnDevice (  CUcontext* pCtx, unsigned int  flags, ID3D11Device* pD3DDevice, CUdevice cudaDevice )
Create a CUDA context for interoperability with Direct3D 11.

CUresult cuD3D11GetDirect3DDevice (  ID3D11Device ppD3DDevice )
Get the Direct3D 11 device against which the current CUDA context was created.


### Functions


CUresult cuD3D11CtxCreate (  CUcontext* pCtx, CUdevice* pCudaDevice, unsigned int  Flags, ID3D11Device* pD3DDevice )
Create a CUDA context for interoperability with Direct3D 11.

                                 Parameters



pCtx
- Returned newly created CUDA context
pCudaDevice
- Returned pointer to the device on which the context was created
Flags
- Context creation flags (see cuCtxCreate() for details)

pD3DDevice
- Direct3D device to create interoperability context with

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_OUT_OF_MEMORY, CUDA_ERROR_UNKNOWN

Deprecated
This function is deprecated as of CUDA 5.0.
Description
This function is deprecated and should no longer be used. It is no longer necessary to associate a CUDA context with a D3D11
                                 device in order to achieve maximum interoperability performance.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuD3D11GetDevice, cuGraphicsD3D11RegisterResource

CUresult cuD3D11CtxCreateOnDevice (  CUcontext* pCtx, unsigned int  flags, ID3D11Device* pD3DDevice, CUdevice cudaDevice )
Create a CUDA context for interoperability with Direct3D 11.

                                 Parameters



pCtx
- Returned newly created CUDA context
flags
- Context creation flags (see cuCtxCreate() for details)

pD3DDevice
- Direct3D device to create interoperability context with
cudaDevice
- The CUDA device on which to create the context. This device must be among the devices returned when querying CU_D3D11_DEVICES_ALL
                                    from cuD3D11GetDevices.


Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_OUT_OF_MEMORY, CUDA_ERROR_UNKNOWN

Deprecated
This function is deprecated as of CUDA 5.0.
Description
This function is deprecated and should no longer be used. It is no longer necessary to associate a CUDA context with a D3D11
                                 device in order to achieve maximum interoperability performance.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuD3D11GetDevices, cuGraphicsD3D11RegisterResource

CUresult cuD3D11GetDirect3DDevice (  ID3D11Device ppD3DDevice )
Get the Direct3D 11 device against which the current CUDA context was created.

                                 Parameters



ppD3DDevice
- Returned Direct3D device corresponding to CUDA context

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT

Deprecated
This function is deprecated as of CUDA 5.0.
Description
This function is deprecated and should no longer be used. It is no longer necessary to associate a CUDA context with a D3D11
                                 device in order to achieve maximum interoperability performance.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuD3D11GetDevice


---