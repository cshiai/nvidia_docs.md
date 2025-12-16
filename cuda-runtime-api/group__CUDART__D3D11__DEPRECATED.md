# CUDA Runtime API

[< Previous](group__CUDART__D3D11.html) | [Next >](group__CUDART__VDPAU.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 6.22. Direct3D 11 Interoperability [DEPRECATED]


This section describes deprecated Direct3D 11 interoperability functions.


### Functions


__host__
                           ​cudaError_t cudaD3D11GetDirect3DDevice (  ID3D11Device ppD3D11Device )
Gets the Direct3D device against which the current CUDA context was created.

__host__
                           ​cudaError_t cudaD3D11SetDirect3DDevice (  ID3D11Device* pD3D11Device, int  device = -1 )
Sets the Direct3D 11 device to use for interoperability with a CUDA device.


### Functions


__host__
                              ​cudaError_t cudaD3D11GetDirect3DDevice (  ID3D11Device ppD3D11Device )
Gets the Direct3D device against which the current CUDA context was created.

                                 Parameters



ppD3D11Device
- Returns the Direct3D device for this thread

Returns
cudaSuccess, cudaErrorUnknown

Deprecated
This function is deprecated as of CUDA 5.0.
Description
This function is deprecated and should no longer be used. It is no longer necessary to associate a CUDA device with a D3D11
                                 device in order to achieve maximum interoperability performance.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cudaD3D11SetDirect3DDevice

__host__
                              ​cudaError_t cudaD3D11SetDirect3DDevice (  ID3D11Device* pD3D11Device, int  device = -1 )
Sets the Direct3D 11 device to use for interoperability with a CUDA device.

                                 Parameters



pD3D11Device
- Direct3D device to use for interoperability
device
- The CUDA device to use. This device must be among the devices returned when querying cudaD3D11DeviceListAll from cudaD3D11GetDevices, may be set to -1 to automatically select an appropriate CUDA device.


Returns
cudaSuccess, cudaErrorInitializationError, cudaErrorInvalidValue, cudaErrorSetOnActiveProcess

Deprecated
This function is deprecated as of CUDA 5.0.
Description
This function is deprecated and should no longer be used. It is no longer necessary to associate a CUDA device with a D3D11
                                 device in order to achieve maximum interoperability performance.

This function will immediately initialize the primary context on device if needed.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cudaD3D11GetDevice, cudaGraphicsD3D11RegisterResource, cudaDeviceReset


---