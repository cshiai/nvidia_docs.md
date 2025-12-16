# CUDA Runtime API

[< Previous](group__CUDART__MEMORY__POOLS.html) | [Next >](group__CUDART__PEER.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 6.13. Unified Addressing


This section describes the unified addressing functions of the CUDA runtime application programming interface.


Overview


CUDA devices can share a unified address space with the host. For these devices there is no distinction between a device pointer and a host pointer -- the same pointer value may be used to access memory from the host program and from a kernel running on the device (with exceptions enumerated below).


Supported Platforms


Whether or not a device supports unified addressing may be queried by calling [cudaGetDeviceProperties()](group__CUDART__DEVICE.html#group__CUDART__DEVICE_1g1bf9d625a931d657e08db2b4391170f0) with the device property [cudaDeviceProp::unifiedAddressing](structcudaDeviceProp.html#structcudaDeviceProp_107b0114cefb43da05e05c65ec859542c).


Unified addressing is automatically enabled in 64-bit processes .


Looking Up Information from Pointer Values


It is possible to look up information about the memory which backs a pointer value. For instance, one may want to know if a pointer points to host or device memory. As another example, in the case of device memory, one may want to know on which CUDA device the memory resides. These properties may be queried using the function [cudaPointerGetAttributes()](group__CUDART__UNIFIED.html#group__CUDART__UNIFIED_1gd89830e17d399c064a2f3c3fa8bb4390)


Since pointers are unique, it is not necessary to specify information about the pointers specified to [cudaMemcpy()](group__CUDART__MEMORY.html#group__CUDART__MEMORY_1gc263dbe6574220cc776b45438fc351e8) and other copy functions. The copy direction [cudaMemcpyDefault](group__CUDART__TYPES.html#group__CUDART__TYPES_1gg18fa99055ee694244a270e4d5101e95b715aff8fb2b8f4f1bb553fee802db57a) may be used to specify that the CUDA runtime should infer the location of the pointer from its value.


Automatic Mapping of Host Allocated Host Memory


All host memory allocated through all devices using [cudaMallocHost()](group__CUDART__MEMORY.html#group__CUDART__MEMORY_1gab84100ae1fa1b12eaca660207ef585b) and [cudaHostAlloc()](group__CUDART__MEMORY.html#group__CUDART__MEMORY_1gb65da58f444e7230d3322b6126bb4902) is always directly accessible from all devices that support unified addressing. This is the case regardless of whether or not the flags [cudaHostAllocPortable](group__CUDART__TYPES.html#group__CUDART__TYPES_1gc46ce76be41cf79774331cc8cfceb52b) and [cudaHostAllocMapped](group__CUDART__TYPES.html#group__CUDART__TYPES_1g01e600c738b962c8f973dda7708f7a70) are specified.


The pointer value through which allocated host memory may be accessed in kernels on all devices that support unified addressing is the same as the pointer value through which that memory is accessed on the host. It is not necessary to call [cudaHostGetDevicePointer()](group__CUDART__MEMORY.html#group__CUDART__MEMORY_1gc00502b44e5f1bdc0b424487ebb08db0) to get the device pointer for these allocations.


Note that this is not the case for memory allocated using the flag [cudaHostAllocWriteCombined](group__CUDART__TYPES.html#group__CUDART__TYPES_1g3a7db37d02ce0b2350067ab639ef321c), as discussed below.


Direct Access of Peer Memory


Upon enabling direct access from a device that supports unified addressing to another peer device that supports unified addressing using [cudaDeviceEnablePeerAccess()](group__CUDART__PEER.html#group__CUDART__PEER_1g2b0adabf90db37e5cfddc92cbb2589f3) all memory allocated in the peer device using [cudaMalloc()](group__CUDART__MEMORY.html#group__CUDART__MEMORY_1g37d37965bfb4803b6d4e59ff26856356) and [cudaMallocPitch()](group__CUDART__MEMORY.html#group__CUDART__MEMORY_1g32bd7a39135594788a542ae72217775c) will immediately be accessible by the current device. The device pointer value through which any peer's memory may be accessed in the current device is the same pointer value through which that memory may be accessed from the peer device.


Exceptions, Disjoint Addressing


Not all memory may be accessed on devices through the same pointer value through which they are accessed on the host. These exceptions are host memory registered using [cudaHostRegister()](group__CUDART__MEMORY.html#group__CUDART__MEMORY_1ge8d5c17670f16ac4fc8fcb4181cb490c) and host memory allocated using the flag [cudaHostAllocWriteCombined](group__CUDART__TYPES.html#group__CUDART__TYPES_1g3a7db37d02ce0b2350067ab639ef321c). For these exceptions, there exists a distinct host and device address for the memory. The device address is guaranteed to not overlap any valid host pointer range and is guaranteed to have the same value across all devices that support unified addressing.


This device address may be queried using [cudaHostGetDevicePointer()](group__CUDART__MEMORY.html#group__CUDART__MEMORY_1gc00502b44e5f1bdc0b424487ebb08db0) when a device using unified addressing is current. Either the host or the unified device pointer value may be used to refer to this memory in [cudaMemcpy()](group__CUDART__MEMORY.html#group__CUDART__MEMORY_1gc263dbe6574220cc776b45438fc351e8) and similar functions using the [cudaMemcpyDefault](group__CUDART__TYPES.html#group__CUDART__TYPES_1gg18fa99055ee694244a270e4d5101e95b715aff8fb2b8f4f1bb553fee802db57a) memory direction.


### Functions


__host__
                           ​cudaError_t cudaPointerGetAttributes (  cudaPointerAttributes* attributes, const void* ptr )
Returns attributes about a specified pointer.


### Functions


__host__
                              ​cudaError_t cudaPointerGetAttributes (  cudaPointerAttributes* attributes, const void* ptr )
Returns attributes about a specified pointer.

                                 Parameters



attributes
- Attributes for the specified pointer
ptr
- Pointer to get attributes for

Returns
cudaSuccess, cudaErrorInvalidDevice, cudaErrorInvalidValue

Description
Returns in *attributes the attributes of the pointer ptr. If pointer was not allocated in, mapped by or registered with context supporting unified addressing cudaErrorInvalidValue is returned.


Note:In CUDA 11.0 forward passing host pointer will return cudaMemoryTypeUnregistered in cudaPointerAttributes::type and call will return cudaSuccess.


                                 The cudaPointerAttributes structure is defined as:
‎    struct cudaPointerAttributes {
              enum cudaMemoryType
                  type;
              int device;
              void *devicePointer;
              void *hostPointer;
          } In this structure, the individual fields mean


cudaPointerAttributes::type identifies type of memory. It can be cudaMemoryTypeUnregistered for unregistered host memory, cudaMemoryTypeHost for registered host memory, cudaMemoryTypeDevice for device memory or cudaMemoryTypeManaged for managed memory.


device is the device against which ptr was allocated. If ptr has memory type cudaMemoryTypeDevice then this identifies the device on which the memory referred to by ptr physically resides. If ptr has memory type cudaMemoryTypeHost then this identifies the device which was current when the allocation was made (and if that device is deinitialized then
                                          this allocation will vanish with that device's state).


devicePointer is the device pointer alias through which the memory referred to by ptr may be accessed on the current device. If the memory referred to by ptr cannot be accessed directly by the current device then this is NULL.


hostPointer is the host pointer alias through which the memory referred to by ptr may be accessed on the host. If the memory referred to by ptr cannot be accessed directly by the host then this is NULL.


Note:

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


See also:
cudaGetDeviceCount, cudaGetDevice, cudaSetDevice, cudaChooseDevice, cudaInitDevice, cuPointerGetAttributes


---