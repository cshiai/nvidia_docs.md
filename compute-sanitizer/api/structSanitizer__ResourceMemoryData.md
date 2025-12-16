# Sanitizer_ResourceMemoryData


struct Sanitizer_ResourceMemoryData
Data passed into a memory resource callback function.
Data passed into a memory resource callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_RESOURCE and cbid equal to SANITIZER_CBID_RESOURCE_DEVICE_MEMORY_ALLOC, SANITIZER_CBID_RESOURCE_DEVICE_MEMORY_FREE, SANITIZER_CBID_RESOURCE_HOST_MEMORY_ALLOC, SANITIZER_CBID_RESOURCE_HOST_MEMORY_FREE, SANITIZER_CBID_RESOURCE_MEMORY_ALLOC_ASYNC, SANITIZER_CBID_RESOURCE_MEMORY_FREE_ASYNC or SANITIZER_CBID_RESOURCE_MEMORY_FREE_ASYNC_DONE or SANITIZER_CBID_RESOURCE_MEMPOOL_IMPORT_POINTER. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

uint64_t address
Address of the allocation being created or destroyed.

CUcontext context
Context containing the allocation being created or destroyed.
Can be NULL if the allocation is not attached to a context.

CUdevice device
Device where the allocation is being created.
Available for all cbid with a driver version of 455 or newer.

uint32_t flags
Allocation details: use Sanitizer_ResourceMemoryFlags to interpret this field.

Sanitizer_StreamHandle hStream
Stream containing the allocation being created or destroyed.
Can be NULL if the allocation is not attached to a stream.

CUmemoryPool memoryPool
Memory pool containing the allocation being created or destroyed.
Can be NULL if the allocation is not attached to a memory pool.

uint32_t permissions
Allocation permissions: use Sanitizer_ResourceMemoryPermissions to interpret this field.

uint64_t size
Size of the allocation being created or destroyed.

CUdevice sourceDevice
Source device of this allocation (different from device if SANITIZER_MEMORY_FLAG_PEER is set).

CUstream stream
Public handle for the stream.

Sanitizer_MemoryVisibility visibility
Visibility of the allocation.