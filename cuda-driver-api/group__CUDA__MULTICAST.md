# CUDA Driver API

[< Previous](group__CUDA__MALLOC__ASYNC.html) | [Next >](group__CUDA__UNIFIED.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.16. Multicast Object Management


This section describes the CUDA multicast object operations exposed by the low-level CUDA driver application programming interface.


overview


A multicast object created via [cuMulticastCreate](group__CUDA__MULTICAST.html#group__CUDA__MULTICAST_1gd4413361f466d4ed86a93d8c309c0242) enables certain memory operations to be broadcast to a team of devices. Devices can be added to a multicast object via [cuMulticastAddDevice](group__CUDA__MULTICAST.html#group__CUDA__MULTICAST_1g2df07b38ff506c519e9f799c5ddf7e5d). Memory can be bound on each participating device via [cuMulticastBindMem](group__CUDA__MULTICAST.html#group__CUDA__MULTICAST_1gcadf88b616a3f766f6279288e435a4bb), [cuMulticastBindMem_v2](group__CUDA__MULTICAST.html#group__CUDA__MULTICAST_1g0e0ed2e81af121bdcbb54e1a9c4e63a5), [cuMulticastBindAddr](group__CUDA__MULTICAST.html#group__CUDA__MULTICAST_1g07c8cf1d3bf1d04a2d1867f09647b03f), or [cuMulticastBindAddr_v2](group__CUDA__MULTICAST.html#group__CUDA__MULTICAST_1g0eb82d8911bf179ae239d522da049bed). Multicast objects can be mapped into a device's virtual address space using the virtual memmory management APIs (see [cuMemMap](group__CUDA__VA.html#group__CUDA__VA_1gff1d395423af5c5c75375516959dae56) and [cuMemSetAccess](group__CUDA__VA.html#group__CUDA__VA_1g1b6b12b10e8324bf462ecab4e7ef30e1)).


Supported Platforms


Support for multicast on a specific device can be queried using the device attribute [CU_DEVICE_ATTRIBUTE_MULTICAST_SUPPORTED](group__CUDA__TYPES.html#group__CUDA__TYPES_1gge12b8a782bebe21b1ac0091bf9f4e2a3ce470c9ff9166a3a8740bef623f5d299)


### Functions


CUresult cuMulticastAddDevice (  CUmemGenericAllocationHandle mcHandle, CUdevice dev )
Associate a device to a multicast object.

CUresult cuMulticastBindAddr (  CUmemGenericAllocationHandle mcHandle, size_t mcOffset, CUdeviceptr memptr, size_t size, unsigned long long flags )
Bind a memory allocation represented by a virtual address to a multicast object.

CUresult cuMulticastBindAddr_v2 (  CUmemGenericAllocationHandle mcHandle, CUdevice dev, size_t mcOffset, CUdeviceptr memptr, size_t size, unsigned long long flags )
Bind a memory allocation represented by a virtual address to a multicast object.

CUresult cuMulticastBindMem (  CUmemGenericAllocationHandle mcHandle, size_t mcOffset, CUmemGenericAllocationHandle memHandle, size_t memOffset, size_t size, unsigned long long flags )
Bind a memory allocation represented by a handle to a multicast object.

CUresult cuMulticastBindMem_v2 (  CUmemGenericAllocationHandle mcHandle, CUdevice dev, size_t mcOffset, CUmemGenericAllocationHandle memHandle, size_t memOffset, size_t size, unsigned long long flags )
Bind a memory allocation represented by a handle to a multicast object.

CUresult cuMulticastCreate (  CUmemGenericAllocationHandle* mcHandle, const CUmulticastObjectProp* prop )
Create a generic allocation handle representing a multicast object described by the given properties.

CUresult cuMulticastGetGranularity (  size_t* granularity, const CUmulticastObjectProp* prop, CUmulticastGranularity_flags option )
Calculates either the minimal or recommended granularity for multicast object.

CUresult cuMulticastUnbind (  CUmemGenericAllocationHandle mcHandle, CUdevice dev, size_t mcOffset, size_t size )
Unbind any memory allocations bound to a multicast object at a given offset and upto a given size.


### Functions


CUresult cuMulticastAddDevice (  CUmemGenericAllocationHandle mcHandle, CUdevice dev )
Associate a device to a multicast object.

                                 Parameters



mcHandle
Handle representing a multicast object.
dev
Device that will be associated to the multicast object.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_OUT_OF_MEMORY, CUDA_ERROR_INVALID_DEVICE, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_PERMITTED, CUDA_ERROR_NOT_SUPPORTED

Description
Associates a device to a multicast object. The added device will be a part of the multicast team of size specified by CUmulticastObjectProp::numDevices during cuMulticastCreate. The association of the device to the multicast object is permanent during the life time of the multicast object. All devices
                                 must be added to the multicast team before any memory can be bound to any device in the team. Any calls to cuMulticastBindMem, cuMulticastBindMem_v2, cuMulticastBindAddr, or cuMulticastBindAddr_v2 will block until all devices have been added. Similarly all devices must be added to the multicast team before a virtual
                                 address range can be mapped to the multicast object. A call to cuMemMap will block until all devices have been added.


See also:
cuMulticastCreate, cuMulticastBindMem, cuMulticastBindAddr

CUresult cuMulticastBindAddr (  CUmemGenericAllocationHandle mcHandle, size_t mcOffset, CUdeviceptr memptr, size_t size, unsigned long long flags )
Bind a memory allocation represented by a virtual address to a multicast object.

                                 Parameters



mcHandle
Handle representing a multicast object.
mcOffset
Offset into multicast va range for attachment.
memptr
Virtual address of the memory allocation.
size
Size of memory that will be bound to the multicast object.
flags
Flags for future use, must be zero now.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_INVALID_DEVICE, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_PERMITTED, CUDA_ERROR_NOT_SUPPORTED, CUDA_ERROR_OUT_OF_MEMORY, CUDA_ERROR_SYSTEM_NOT_READY, CUDA_ERROR_ILLEGAL_STATE

Description
Binds a memory allocation specified by its mapped address memptr to a multicast object represented by mcHandle. The memory must have been allocated via cuMemCreate or cudaMallocAsync. The intended size of the bind, the offset in the multicast range mcOffset and memptr must be a multiple of the value returned by cuMulticastGetGranularity with the flag CU_MULTICAST_GRANULARITY_MINIMUM. For best performance however, size, mcOffset and memptr should be aligned to the value returned by cuMulticastGetGranularity with the flag CU_MULTICAST_GRANULARITY_RECOMMENDED.

The size cannot be larger than the size of the allocated memory. Similarly the size + mcOffset cannot be larger than the total size of the multicast object. The memory allocation must have beeen created on one of the
                                 devices that was added to the multicast team via cuMulticastAddDevice. Externally shareable as well as imported multicast objects can be bound only to externally shareable memory. Note that this
                                 call will return CUDA_ERROR_OUT_OF_MEMORY if there are insufficient resources required to perform the bind. This call may
                                 also return CUDA_ERROR_SYSTEM_NOT_READY if the necessary system software is not initialized or running.

This call may return CUDA_ERROR_ILLEGAL_STATE if the system configuration is in an illegal state. In such cases, to continue
                                 using multicast, verify that the system configuration is in a valid state and all required driver daemons are running properly.


See also:
cuMulticastCreate, cuMulticastAddDevice, cuMemCreate
cuMulticastBindAddr_v2

CUresult cuMulticastBindAddr_v2 (  CUmemGenericAllocationHandle mcHandle, CUdevice dev, size_t mcOffset, CUdeviceptr memptr, size_t size, unsigned long long flags )
Bind a memory allocation represented by a virtual address to a multicast object.

                                 Parameters



mcHandle
Handle representing a multicast object.
dev
The device that for which the multicast memory binding will be applicable.
mcOffset
Offset into multicast va range for attachment.
memptr
Virtual address of the memory allocation.
size
Size of memory that will be bound to the multicast object.
flags
Flags for future use, must be zero now.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_INVALID_DEVICE, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_PERMITTED, CUDA_ERROR_NOT_SUPPORTED, CUDA_ERROR_OUT_OF_MEMORY, CUDA_ERROR_SYSTEM_NOT_READY, CUDA_ERROR_ILLEGAL_STATE

Description
Binds a memory allocation specified by its mapped address memptr to a multicast object represented by mcHandle. The binding will be applicable for the device dev. The memory must have been allocated via cuMemCreate or cudaMallocAsync. The intended size of the bind, the offset in the multicast range mcOffset and memptr must be a multiple of the value returned by cuMulticastGetGranularity with the flag CU_MULTICAST_GRANULARITY_MINIMUM. For best performance however, size, mcOffset and memptr should be aligned to the value returned by cuMulticastGetGranularity with the flag CU_MULTICAST_GRANULARITY_RECOMMENDED.

The size cannot be larger than the size of the allocated memory. Similarly the size + mcOffset cannot be larger than the total size of the multicast object. For device memory, i.e., type CU_MEM_LOCATION_TYPE_DEVICE, the memory allocation must have been created on the device specified by dev. For host NUMA memory, i.e., type CU_MEM_LOCATION_TYPE_HOST_NUMA, the memory allocation must have been created on the CPU NUMA node closest to dev. That is, the value returned when querying CU_DEVICE_ATTRIBUTE_HOST_NUMA_ID for dev, must be the CPU NUMA node where the memory was allocated. In both cases, the device named by dev must have been added to the multicast team via cuMulticastAddDevice. Externally shareable as well as imported multicast objects can be bound only to externally shareable memory. Note that this
                                 call will return CUDA_ERROR_OUT_OF_MEMORY if there are insufficient resources required to perform the bind. This call may
                                 also return CUDA_ERROR_SYSTEM_NOT_READY if the necessary system software is not initialized or running.

This call may return CUDA_ERROR_ILLEGAL_STATE if the system configuration is in an illegal state. In such cases, to continue
                                 using multicast, verify that the system configuration is in a valid state and all required driver daemons are running properly.


See also:
cuMulticastCreate, cuMulticastAddDevice, cuMemCreate

CUresult cuMulticastBindMem (  CUmemGenericAllocationHandle mcHandle, size_t mcOffset, CUmemGenericAllocationHandle memHandle, size_t memOffset, size_t size, unsigned long long flags )
Bind a memory allocation represented by a handle to a multicast object.

                                 Parameters



mcHandle
Handle representing a multicast object.
mcOffset
Offset into the multicast object for attachment.
memHandle
Handle representing a memory allocation.
memOffset
Offset into the memory for attachment.
size
Size of the memory that will be bound to the multicast object.
flags
Flags for future use, must be zero for now.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_INVALID_DEVICE, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_PERMITTED, CUDA_ERROR_NOT_SUPPORTED, CUDA_ERROR_OUT_OF_MEMORY, CUDA_ERROR_SYSTEM_NOT_READY, CUDA_ERROR_ILLEGAL_STATE

Description
Binds a memory allocation specified by memHandle and created via cuMemCreate to a multicast object represented by mcHandle and created via cuMulticastCreate. The intended size of the bind, the offset in the multicast range mcOffset as well as the offset in the memory memOffset must be a multiple of the value returned by cuMulticastGetGranularity with the flag CU_MULTICAST_GRANULARITY_MINIMUM. For best performance however, size, mcOffset and memOffset should be aligned to the granularity of the memory allocation(see ::cuMemGetAllocationGranularity) or to the value returned
                                 by cuMulticastGetGranularity with the flag CU_MULTICAST_GRANULARITY_RECOMMENDED.

The size + memOffset cannot be larger than the size of the allocated memory. Similarly the size + mcOffset cannot be larger than the size of the multicast object. The memory allocation must have beeen created on one of the devices
                                 that was added to the multicast team via cuMulticastAddDevice. Externally shareable as well as imported multicast objects can be bound only to externally shareable memory. Note that this
                                 call will return CUDA_ERROR_OUT_OF_MEMORY if there are insufficient resources required to perform the bind. This call may
                                 also return CUDA_ERROR_SYSTEM_NOT_READY if the necessary system software is not initialized or running.

This call may return CUDA_ERROR_ILLEGAL_STATE if the system configuration is in an illegal state. In such cases, to continue
                                 using multicast, verify that the system configuration is in a valid state and all required driver daemons are running properly.


See also:
cuMulticastCreate, cuMulticastAddDevice, cuMemCreate
cuMulticastBindMem_v2

CUresult cuMulticastBindMem_v2 (  CUmemGenericAllocationHandle mcHandle, CUdevice dev, size_t mcOffset, CUmemGenericAllocationHandle memHandle, size_t memOffset, size_t size, unsigned long long flags )
Bind a memory allocation represented by a handle to a multicast object.

                                 Parameters



mcHandle
Handle representing a multicast object.
dev
The device that for which the multicast memory binding will be applicable.
mcOffset
Offset into the multicast object for attachment.
memHandle
Handle representing a memory allocation.
memOffset
Offset into the memory for attachment.
size
Size of the memory that will be bound to the multicast object.
flags
Flags for future use, must be zero for now.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_INVALID_DEVICE, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_PERMITTED, CUDA_ERROR_NOT_SUPPORTED, CUDA_ERROR_OUT_OF_MEMORY, CUDA_ERROR_SYSTEM_NOT_READY, CUDA_ERROR_ILLEGAL_STATE

Description
Binds a memory allocation specified by memHandle and created via cuMemCreate to a multicast object represented by mcHandle and created via cuMulticastCreate. The binding will be applicable for the device dev. The intended size of the bind, the offset in the multicast range mcOffset as well as the offset in the memory memOffset must be a multiple of the value returned by cuMulticastGetGranularity with the flag CU_MULTICAST_GRANULARITY_MINIMUM. For best performance however, size, mcOffset and memOffset should be aligned to the granularity of the memory allocation(see ::cuMemGetAllocationGranularity) or to the value returned
                                 by cuMulticastGetGranularity with the flag CU_MULTICAST_GRANULARITY_RECOMMENDED.

The size + memOffset cannot be larger than the size of the allocated memory. Similarly the size + mcOffset cannot be larger than the size of the multicast object. The memory allocation must have beeen created on one of the devices
                                 that was added to the multicast team via cuMulticastAddDevice. For device memory, i.e., type CU_MEM_LOCATION_TYPE_DEVICE, the memory allocation must have been created on the device specified by dev. For host NUMA memory, i.e., type CU_MEM_LOCATION_TYPE_HOST_NUMA, the memory allocation must have been created on the CPU NUMA node closest to dev. That is, the value returned when querying CU_DEVICE_ATTRIBUTE_HOST_NUMA_ID for dev, must be the CPU NUMA node where the memory was allocated. In both cases, the device named by dev must have been added to the multicast team via cuMulticastAddDevice. Externally shareable as well as imported multicast objects can be bound only to externally shareable memory. Note that this
                                 call will return CUDA_ERROR_OUT_OF_MEMORY if there are insufficient resources required to perform the bind. This call may
                                 also return CUDA_ERROR_SYSTEM_NOT_READY if the necessary system software is not initialized or running.

This call may return CUDA_ERROR_ILLEGAL_STATE if the system configuration is in an illegal state. In such cases, to continue
                                 using multicast, verify that the system configuration is in a valid state and all required driver daemons are running properly.


See also:
cuMulticastCreate, cuMulticastAddDevice, cuMemCreate

CUresult cuMulticastCreate (  CUmemGenericAllocationHandle* mcHandle, const CUmulticastObjectProp* prop )
Create a generic allocation handle representing a multicast object described by the given properties.

                                 Parameters



mcHandle
Value of handle returned.
prop
Properties of the multicast object to create.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_OUT_OF_MEMORY, CUDA_ERROR_INVALID_DEVICE, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_PERMITTED, CUDA_ERROR_NOT_SUPPORTED

Description
This creates a multicast object as described by prop. The number of participating devices is specified by CUmulticastObjectProp::numDevices. Devices can be added to the multicast object via cuMulticastAddDevice. All participating devices must be added to the multicast object before memory can be bound to it. Memory is bound to the
                                 multicast object via cuMulticastBindMem, cuMulticastBindMem_v2, cuMulticastBindAddr, or cuMulticastBindAddr_v2. and can be unbound via cuMulticastUnbind. The total amount of memory that can be bound per device is specified by :CUmulticastObjectProp::size. This size must be a multiple of the value returned by cuMulticastGetGranularity with the flag CU_MULTICAST_GRANULARITY_MINIMUM. For best performance however, the size should be aligned to the value returned by cuMulticastGetGranularity with the flag CU_MULTICAST_GRANULARITY_RECOMMENDED.

After all participating devices have been added, multicast objects can also be mapped to a device's virtual address space
                                 using the virtual memory management APIs (see cuMemMap and cuMemSetAccess). Multicast objects can also be shared with other processes by requesting a shareable handle via cuMemExportToShareableHandle. Note that the desired types of shareable handles must be specified in the bitmask CUmulticastObjectProp::handleTypes. Multicast objects can be released using the virtual memory management API cuMemRelease.


See also:
cuMulticastAddDevice, cuMulticastBindMem, cuMulticastBindAddr, cuMulticastUnbind
cuMemCreate, cuMemRelease, cuMemExportToShareableHandle, cuMemImportFromShareableHandle
cuMulticastBindAddr_v2, cuMulticastBindMem_v2

CUresult cuMulticastGetGranularity (  size_t* granularity, const CUmulticastObjectProp* prop, CUmulticastGranularity_flags option )
Calculates either the minimal or recommended granularity for multicast object.

                                 Parameters



granularity
Returned granularity.
prop
Properties of the multicast object.
option
Determines which granularity to return.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_PERMITTED, CUDA_ERROR_NOT_SUPPORTED

Description
Calculates either the minimal or recommended granularity for a given set of multicast object properties and returns it in
                                 granularity. This granularity can be used as a multiple for size, bind offsets and address mappings of the multicast object.


See also:
cuMulticastCreate, cuMulticastBindMem, cuMulticastBindAddr, cuMulticastUnbind
cuMulticastBindMem_v2, cuMulticastBindAddr_v2

CUresult cuMulticastUnbind (  CUmemGenericAllocationHandle mcHandle, CUdevice dev, size_t mcOffset, size_t size )
Unbind any memory allocations bound to a multicast object at a given offset and upto a given size.

                                 Parameters



mcHandle
Handle representing a multicast object.
dev
Device that hosts the memory allocation.
mcOffset
Offset into the multicast object.
size
Desired size to unbind.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_INVALID_DEVICE, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_PERMITTED, CUDA_ERROR_NOT_SUPPORTED

Description
Unbinds any memory allocations hosted on dev and bound to a multicast object at mcOffset and upto a given size. The intended size of the unbind and the offset in the multicast range ( mcOffset ) must be a multiple of the value returned by cuMulticastGetGranularity flag CU_MULTICAST_GRANULARITY_MINIMUM. The size + mcOffset cannot be larger than the total size of the multicast object.


Note:Warning: The mcOffset and the size must match the corresponding values specified during the bind call. Any other values may result in undefined behavior.


See also:
cuMulticastBindMem, cuMulticastBindAddr
cuMulticastBindMem_v2, cuMulticastBindAddr_v2


---