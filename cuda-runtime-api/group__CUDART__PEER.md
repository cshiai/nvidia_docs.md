# CUDA Runtime API

[< Previous](group__CUDART__UNIFIED.html) | [Next >](group__CUDART__OPENGL.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 6.14. Peer Device Memory Access


This section describes the peer device memory access functions of the CUDA runtime application programming interface.


### Functions


__host__
                           ​cudaError_t cudaDeviceCanAccessPeer (  int* canAccessPeer, int  device, int  peerDevice )
Queries if a device may directly access a peer device's memory.

__host__
                           ​cudaError_t cudaDeviceDisablePeerAccess (  int  peerDevice )
Disables direct access to memory allocations on a peer device.

__host__
                           ​cudaError_t cudaDeviceEnablePeerAccess (  int  peerDevice, unsigned int  flags )
Enables direct access to memory allocations on a peer device.


### Functions


__host__
                              ​cudaError_t cudaDeviceCanAccessPeer (  int* canAccessPeer, int  device, int  peerDevice )
Queries if a device may directly access a peer device's memory.

                                 Parameters



canAccessPeer
- Returned access capability
device
- Device from which allocations on peerDevice are to be directly accessed.

peerDevice
- Device on which the allocations to be directly accessed by device reside.


Returns
cudaSuccess, cudaErrorInvalidDevice

Description
Returns in *canAccessPeer a value of 1 if device device is capable of directly accessing memory from peerDevice and 0 otherwise. If direct access of peerDevice from device is possible, then access may be enabled by calling cudaDeviceEnablePeerAccess().


Note:

Note that this function may also return error codes from previous, asynchronous launches.

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


See also:
cudaDeviceEnablePeerAccess, cudaDeviceDisablePeerAccess, cuDeviceCanAccessPeer

__host__
                              ​cudaError_t cudaDeviceDisablePeerAccess (  int  peerDevice )
Disables direct access to memory allocations on a peer device.

                                 Parameters



peerDevice
- Peer device to disable direct access to

Returns
cudaSuccess, cudaErrorPeerAccessNotEnabled, cudaErrorInvalidDevice

Description
Returns cudaErrorPeerAccessNotEnabled if direct access to memory on peerDevice has not yet been enabled from the current device.


Note:

Note that this function may also return error codes from previous, asynchronous launches.

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


See also:
cudaDeviceCanAccessPeer, cudaDeviceEnablePeerAccess, cuCtxDisablePeerAccess

__host__
                              ​cudaError_t cudaDeviceEnablePeerAccess (  int  peerDevice, unsigned int  flags )
Enables direct access to memory allocations on a peer device.

                                 Parameters



peerDevice
- Peer device to enable direct access to from the current device
flags
- Reserved for future use and must be set to 0

Returns
cudaSuccess, cudaErrorInvalidDevice, cudaErrorPeerAccessAlreadyEnabled, cudaErrorInvalidValue

Description
On success, all allocations from peerDevice will immediately be accessible by the current device. They will remain accessible until access is explicitly disabled using
                                 cudaDeviceDisablePeerAccess() or either device is reset using cudaDeviceReset().

Note that access granted by this call is unidirectional and that in order to access memory on the current device from peerDevice, a separate symmetric call to cudaDeviceEnablePeerAccess() is required.

Note that there are both device-wide and system-wide limitations per system configuration, as noted in the CUDA Programming
                                 Guide under the section "Peer-to-Peer Memory Access".

Returns cudaErrorInvalidDevice if cudaDeviceCanAccessPeer() indicates that the current device cannot directly access memory from peerDevice.

Returns cudaErrorPeerAccessAlreadyEnabled if direct access of peerDevice from the current device has already been enabled.

Returns cudaErrorInvalidValue if flags is not 0.


Note:

Note that this function may also return error codes from previous, asynchronous launches.

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


See also:
cudaDeviceCanAccessPeer, cudaDeviceDisablePeerAccess, cuCtxEnablePeerAccess


---