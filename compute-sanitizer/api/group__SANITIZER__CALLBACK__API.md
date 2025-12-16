# Sanitizer Callback API


Functions, types, and enums that implement the Sanitizer Callback API.


## Typedefs


Sanitizer_CallbackFunc
Function type for a callback.

Sanitizer_CallbackId
Callback ID.

Sanitizer_SubscriberHandle
A callback subscriber.


## Enumerations


Sanitizer_ApiCallbackSite
Specifies the point in an API call that a callback is issued.

Sanitizer_BatchMemopAtomicOp
Specifies the type of atomic operation for batch memory atomic reduction.

Sanitizer_BatchMemopType
Specifies the type of batch memory operation.

Sanitizer_CallackIdSync
Callback IDs for synchronization domain.

Sanitizer_CallbackDomain
Callback domains.

Sanitizer_CallbackIdBatchMemop
Callback IDs for batch memop domain.

Sanitizer_CallbackIdEvents
Callback IDs for events domain.

Sanitizer_CallbackIdExternalMemory
Callback IDs for external memory domain.

Sanitizer_CallbackIdGraphs
Callback IDs for graphs domain.

Sanitizer_CallbackIdLaunch
Callback IDs for launch domain.

Sanitizer_CallbackIdMemcpy
Callback IDs for memcpy domain.

Sanitizer_CallbackIdMemset
Callback IDs for memset domain.

Sanitizer_CallbackIdResource
Callback IDs for resource domain.

Sanitizer_CallbackIdUvm
Callback IDs for managed memory domain.

Sanitizer_MemcpyDirection
Memcpy direction.

Sanitizer_MemoryVisibility
Specifies the visibility of an allocation.

Sanitizer_ResourceMemoryFlags
Flags describing a memory allocation.

Sanitizer_ResourceMemoryPermissions
Permissions for a memory allocation.


## Functions


SanitizerResult sanitizerEnableAllDomains(uint32_t enable, Sanitizer_SubscriberHandle subscriber)
Enable or disable all callbacks in all domains.

SanitizerResult sanitizerEnableCallback(uint32_t enable, Sanitizer_SubscriberHandle subscriber, Sanitizer_CallbackDomain domain, Sanitizer_CallbackId cbid)
Enable or disable callbacks for a specific domain and callback ID.

SanitizerResult sanitizerEnableDomain(uint32_t enable, Sanitizer_SubscriberHandle subscriber, Sanitizer_CallbackDomain domain)
Enable or disable all callbacks for a specific domain.

SanitizerResult sanitizerGetCallbackState(uint32_t *enable, Sanitizer_SubscriberHandle subscriber, Sanitizer_CallbackDomain domain, Sanitizer_CallbackId cbid)
Get the current enabled/disabled state of a callback for a specific domain and function ID.

SanitizerResult sanitizerSubscribe(Sanitizer_SubscriberHandle *subscriber, Sanitizer_CallbackFunc callback, void *userdata)
Initialize a callback subscriber with a callback function and user data.

SanitizerResult sanitizerUnsubscribe(Sanitizer_SubscriberHandle subscriber)
Unregister a callback subscriber.


## Structs


Sanitizer_BatchMemopData
Data passed into a batch memop callback function.

Sanitizer_CallbackData
Data passed into a runtime or driver API callback function.

Sanitizer_EventData
Data passed into an event callback function.

Sanitizer_ExternalMemoryData
Data passed into an external memory callback function.

Sanitizer_GraphExecData
Data passed into a graphexec creation callback function.

Sanitizer_GraphLaunchData
Data passed into a graph launch callback function.

Sanitizer_GraphNodeLaunchData
Data passed into a graph node launch callback function.

Sanitizer_LaunchData
Data passed into a launch callback function.

Sanitizer_MemcpyData
Data passed into a memcpy callback function.

Sanitizer_MemsetData
Data passed into a memset callback function.

Sanitizer_ResourceArrayData
Data passed into a CUDA array callback function.

Sanitizer_ResourceContextData
Data passed into a context resource callback function.

Sanitizer_ResourceFunctionsLazyLoadedData
Data passed into a CUDA function callback function.

Sanitizer_ResourceMemoryData
Data passed into a memory resource callback function.

Sanitizer_ResourceMempoolData
Data passed into a mempool resource callback function.

Sanitizer_ResourceModuleData
Data passed into a module resource callback function.

Sanitizer_ResourceStreamData
Data passed into a stream resource callback function.

Sanitizer_ResourceVirtualRange
Data passed into a VA reservation callback function.

Sanitizer_SynchronizeData
Data passed into a synchronization callback function.

Sanitizer_UvmData
Data passed into a managed memory callback function.


## Typedefs


typedef void (*Sanitizer_CallbackFunc)(void *userdata, Sanitizer_CallbackDomain domain, Sanitizer_CallbackId cbid, const void *cbdata)
Function type for a callback.
Function type for a callback. The type of the data passed to the callback in cbdata depends on the domain. If domain is SANITIZER_CB_DOMAIN_DRIVER_API or SANITIZER_CB_DOMAIN_RUNTIME_API the type of cbdata will be Sanitizer_CallbackData. If domain is SANITIZER_CB_DOMAIN_RESOURCE the type of cbdata will be dependent on cbid. Refer to Sanitizer_ResourceContextData, Sanitizer_ResourceStreamData, Sanitizer_ResourceModuleData and Sanitizer_ResourceMemoryFlags documentations. If domain is SANITIZER_CB_DOMAIN_SYNCHRONIZE the type of cbdata will be Sanitizer_SynchronizeData. If domain is SANITIZER_CB_DOMAIN_LAUNCH the type of cbdata will be Sanitizer_LaunchData. If domain is SANITIZER_CB_DOMAIN_MEMCPY the type of cbdata will be Sanitizer_MemcpyData. If domain is SANITIZER_CB_DOMAIN_MEMSET the type of cbdata will be Sanitizer_MemsetData. If domain is SANITIZER_CB_DOMAIN_BATCH_MEMOP the type of cbdata will be Sanitizer_BatchMemopData.


typedef uint32_t Sanitizer_CallbackId
Callback ID.


typedef struct Sanitizer_Subscriber_st *Sanitizer_SubscriberHandle
A callback subscriber.


## Enumerations


enum Sanitizer_ApiCallbackSite
Specifies the point in an API call that a callback is issued.
Specifies the point in an API that a callback is issued. This value is communicated to the callback function via Sanitizer_CallbackData::CallbackSize.
Values:

enumerator SANITIZER_API_ENTER
This callback is at API entry.

enumerator SANITIZER_API_EXIT
This callback is at API exit.

enumerator SANITIZER_API_CBSITE_FORCE_INT


enum Sanitizer_BatchMemopAtomicOp
Specifies the type of atomic operation for batch memory atomic reduction.
Specifies the type ofatomic operation for batch memory atomic reduction reported by a callback in domain SANITIZER_CB_DOMAIN_BATCH_MEMOP. This value is communicated to the callback function via Sanitizer_BatchMemopData::atomicOperation.
Values:

enumerator SANITIZER_BATCH_MEMOP_ATOMIC_OP_OR
The batch memory atomic operation is a binary OR.

enumerator SANITIZER_BATCH_MEMOP_ATOMIC_OP_AND
The batch memory atomic operation is a binary AND.

enumerator SANITIZER_BATCH_MEMOP_ATOMIC_OP_ADD
The batch memory atomic operation is an addition.

enumerator SANITIZER_BATCH_MEMOP_ATOMIC_OP_INT


enum Sanitizer_BatchMemopType
Specifies the type of batch memory operation.
Specifies the type of batch memory operation reported by a callback in domain SANITIZER_CB_DOMAIN_BATCH_MEMOP. This value is communicated to the callback function via Sanitizer_BatchMemopData::type.
Values:

enumerator SANITIZER_BATCH_MEMOP_TYPE_32B
Batch memory operation size is 32 bits.

enumerator SANITIZER_BATCH_MEMOP_TYPE_64B
Batch memory operation size is 64 bits.

enumerator SANITIZER_BATCH_MEMOP_TYPE_FORCE_INT


enum Sanitizer_CallackIdSync
Callback IDs for synchronization domain.
Callback IDs for resource domain SANITIZER_CB_DOMAIN_SYNCHRONIZE. This value is communicated to the callback function via the cbid parameter.
Values:

enumerator SANITIZER_CBID_SYNCHRONIZE_INVALID
Invalid synchronize callback ID.

enumerator SANITIZER_CBID_SYNCHRONIZE_STREAM_SYNCHRONIZED
Stream synchronization has completed for a given stream.

enumerator SANITIZER_CBID_SYNCHRONIZE_CONTEXT_SYNCHRONIZED
Context synchronization has completed for a given context.

enumerator SANITIZER_CBID_SYNCHRONIZE_GREEN_CONTEXT_SYNCHRONIZED
Context synchronization has completed for a given green context.

enumerator SANITIZER_CBID_SYNCHRONIZE_SIZE

enumerator SANITIZER_CBID_SYNCHRONIZE_FORCE_INT


enum Sanitizer_CallbackDomain
Callback domains.
Callback domain. Each domain represents callback points for a group of related API functions or CUDA driver activity.
Values:

enumerator SANITIZER_CB_DOMAIN_INVALID
Invalid domain.

enumerator SANITIZER_CB_DOMAIN_DRIVER_API
Domain containing callback points for all driver API functions.

enumerator SANITIZER_CB_DOMAIN_RUNTIME_API
Domain containing callback points for all runtime API functions.

enumerator SANITIZER_CB_DOMAIN_RESOURCE
Domain containing callback points for CUDA resource tracking.

enumerator SANITIZER_CB_DOMAIN_SYNCHRONIZE
Domain containing callback points for CUDA synchronization.

enumerator SANITIZER_CB_DOMAIN_LAUNCH
Domain containing callback points for CUDA grid launches.

enumerator SANITIZER_CB_DOMAIN_MEMCPY
Domain containing callback points for CUDA memcpy operations.

enumerator SANITIZER_CB_DOMAIN_MEMSET
Domain containing callback points for CUDA memset operations.

enumerator SANITIZER_CB_DOMAIN_BATCH_MEMOP
Domain containing callback points for CUDA batch memop operations.

enumerator SANITIZER_CB_DOMAIN_UVM
Domain containing callback points for CUDA managed memory operations.

enumerator SANITIZER_CB_DOMAIN_GRAPHS
Domain containing callback points for CUDA graphs operations.

enumerator SANITIZER_CB_DOMAIN_EVENTS
Domain containing callback points for CUDA events.

enumerator SANITIZER_CB_DOMAIN_EXTERNAL_MEMORY
Domain containing callback points for CUDA external memory.

enumerator SANITIZER_CB_DOMAIN_SIZE

enumerator SANITIZER_CB_DOMAIN_FORCE_INT


enum Sanitizer_CallbackIdBatchMemop
Callback IDs for batch memop domain.
Callback IDs for resource domain SANITIZER_CB_DOMAIN_BATCH_MEMOP. This value is communicated to the callback function via the cbid parameter.
Values:

enumerator SANITIZER_CBID_BATCH_MEMOP_INVALID
Invalid batch memop callback ID.

enumerator SANITIZER_CBID_BATCH_MEMOP_WRITE
A batch memory write operation was initiated.

enumerator SANITIZER_CBID_BATCH_MEMOP_WAIT_BEGIN
A batch memory wait operation was initiated.

enumerator SANITIZER_CBID_BATCH_MEMOP_ATOMIC_REDUCTION
A batch memory atomic reduction operation was initiated.

enumerator SANITIZER_CBID_BATCH_MEMOP_SIZE

enumerator SANITIZER_CBID_BATCH_MEMOP_FORCE_INT


enum Sanitizer_CallbackIdEvents
Callback IDs for events domain.
Callback IDs for resource domain SANITIZER_CB_DOMAIN_EVENTS. This value is communicated to the callback function via the cbid parameter. Available with a driver version of 515 or newer.
Values:

enumerator SANITIZER_CBID_EVENTS_INVALID
Invalid event callback ID.

enumerator SANITIZER_CBID_EVENTS_CREATED
An event was created.

enumerator SANITIZER_CBID_EVENTS_DESTROYED
An event was destroyed.

enumerator SANITIZER_CBID_EVENTS_RECORD
An event was recorded.

enumerator SANITIZER_CBID_EVENTS_STREAM_WAIT
A stream was synchronized to an event.

enumerator SANITIZER_CBID_EVENTS_SYNCHRONIZE
An event was synchronized.

enumerator SANITIZER_CBID_CTX_RECORD_EVENT
A ctx event was recorded.

enumerator SANITIZER_CBID_GREEN_CTX_RECORD_EVENT
A green ctx event was recorded.

enumerator SANITIZER_CBID_CTX_WAIT_EVENT
A wait for event was scheduled on context.

enumerator SANITIZER_CBID_GREEN_CTX_WAIT_EVENT
A wait for event was scheduled on context.

enumerator SANITIZER_CBID_CTX_EVENT_SYNCHRONIZE
An event was synchronized.

enumerator SANITIZER_CBID_EVENTS_SIZE

enumerator SANITIZER_CBID_EVENTS_FORCE_INT


enum Sanitizer_CallbackIdExternalMemory
Callback IDs for external memory domain.
Callback IDs for resource domain SANITIZER_CB_DOMAIN_EXTERNA_MEMORY. This value is communicated to the callback function via the cbid parameter. Available with a driver version of 535 or newer.
Values:

enumerator SANITIZER_CBID_EXTERNAL_MEMORY_INVALID
Invalid external memory callback ID.

enumerator SANITIZER_CBID_EXTERNAL_MEMORY_IMPORT
External memory was imported.

enumerator SANITIZER_CBID_EXTERNAL_MEMORY_MAPPED
External memory was mapped.

enumerator SANITIZER_CBID_EXTERNAL_MEMORY_DESTROYED
External memory was destroyed.

enumerator SANITIZER_CBID_EXTERNAL_MEMORY_SIZE

enumerator SANITIZER_CBID_EXTERNAL_MEMORY_FORCE_INT


enum Sanitizer_CallbackIdGraphs
Callback IDs for graphs domain.
Callback IDs for resource domain SANITIZER_CB_DOMAIN_GRAPHS. This value is communicated to the callback function via the cbid parameter.
Values:

enumerator SANITIZER_CBID_GRAPHS_INVALID
Invalid graphs callback ID.

enumerator SANITIZER_CBID_GRAPHS_GRAPHEXEC_CREATING
A new graphexec is being created.

enumerator SANITIZER_CBID_GRAPHS_GRAPHEXEC_CREATED
A new graphexec is created.

enumerator SANITIZER_CBID_GRAPHS_GRAPHEXEC_DESTROYING
A graphexec is being destroyed.

enumerator SANITIZER_CBID_GRAPHS_NODE_LAUNCH_BEGIN
A node launch was initiated.

enumerator SANITIZER_CBID_GRAPHS_NODE_LAUNCH_END
A node launch is complete.

enumerator SANITIZER_CBID_GRAPHS_LAUNCH_BEGIN
A graph launch was initiated.

enumerator SANITIZER_CBID_GRAPHS_LAUNCH_END
A graph launch is complete.

enumerator SANITIZER_CBID_GRAPHS_SIZE

enumerator SANITIZER_CBID_GRAPHS_FORCE_INT


enum Sanitizer_CallbackIdLaunch
Callback IDs for launch domain.
Callback IDs for resource domain SANITIZER_CB_DOMAIN_LAUNCH. This value is communicated to the callback function via the cbid parameter.
Values:

enumerator SANITIZER_CBID_LAUNCH_INVALID
Invalid launch callback ID.

enumerator SANITIZER_CBID_LAUNCH_BEGIN
A grid launch was initiated.

enumerator SANITIZER_CBID_LAUNCH_AFTER_SYSCALL_SETUP
A grid launch has completed syscalls setup.

enumerator SANITIZER_CBID_LAUNCH_END
The grid launch is complete.

enumerator SANITIZER_CBID_LAUNCH_SIZE

enumerator SANITIZER_CBID_LAUNCH_FORCE_INT


enum Sanitizer_CallbackIdMemcpy
Callback IDs for memcpy domain.
Callback IDs for resource domain SANITIZER_CB_DOMAIN_MEMCPY. This value is communicated to the callback function via the cbid parameter.
Values:

enumerator SANITIZER_CBID_MEMCPY_INVALID
Invalid memcpy callback ID.

enumerator SANITIZER_CBID_MEMCPY_STARTING
A memcpy operation was initiated.

enumerator SANITIZER_CBID_MEMCPY_SIZE

enumerator SANITIZER_CBID_MEMCPY_FORCE_INT


enum Sanitizer_CallbackIdMemset
Callback IDs for memset domain.
Callback IDs for resource domain SANITIZER_CB_DOMAIN_MEMSET. This value is communicated to the callback function via the cbid parameter.
Values:

enumerator SANITIZER_CBID_MEMSET_INVALID
Invalid memset callback ID.

enumerator SANITIZER_CBID_MEMSET_STARTING
A memset operation was initiated.

enumerator SANITIZER_CBID_MEMSET_SIZE

enumerator SANITIZER_CBID_MEMSET_FORCE_INT


enum Sanitizer_CallbackIdResource
Callback IDs for resource domain.
Callback IDs for resource domain SANITIZER_CB_DOMAIN_RESOURCE. This value is communicated to the callback function via the cbid parameter.
Values:

enumerator SANITIZER_CBID_RESOURCE_INVALID
Invalid resource callback ID.

enumerator SANITIZER_CBID_RESOURCE_INIT_FINISHED
Driver initialization is finished.

enumerator SANITIZER_CBID_RESOURCE_CONTEXT_CREATION_STARTING
A new context is about to be created.

enumerator SANITIZER_CBID_RESOURCE_CONTEXT_CREATION_FINISHED
A new context was created.

enumerator SANITIZER_CBID_RESOURCE_CONTEXT_DESTROY_STARTING
A context is about to be destroyed.

enumerator SANITIZER_CBID_RESOURCE_CONTEXT_DESTROY_FINISHED
A context was destroyed.

enumerator SANITIZER_CBID_RESOURCE_STREAM_CREATED
A new stream was created.

enumerator SANITIZER_CBID_RESOURCE_STREAM_DESTROY_STARTING
A stream is about to be destroyed.

enumerator SANITIZER_CBID_RESOURCE_STREAM_DESTROY_FINISHED
A stream was destroyed.

enumerator SANITIZER_CBID_RESOURCE_MODULE_LOADED
A module was loaded.

enumerator SANITIZER_CBID_RESOURCE_MODULE_UNLOAD_STARTING
A module is about to be unloaded.

enumerator SANITIZER_CBID_RESOURCE_DEVICE_MEMORY_ALLOC
Device memory was allocated.

enumerator SANITIZER_CBID_RESOURCE_DEVICE_MEMORY_FREE
Device memory was freed.

enumerator SANITIZER_CBID_RESOURCE_HOST_MEMORY_ALLOC
Pinned host memory was allocated.

enumerator SANITIZER_CBID_RESOURCE_HOST_MEMORY_FREE
Pinned host memory was freed.

enumerator SANITIZER_CBID_RESOURCE_MEMORY_ALLOC_ASYNC
Memory was allocated asynchronously.

enumerator SANITIZER_CBID_RESOURCE_MEMORY_FREE_ASYNC
Memory was freed asynchronously.

enumerator SANITIZER_CBID_RESOURCE_MEMORY_FREE_ASYNC_DONE
Memory freed asynchronously was released, only happens if a regular allocation (cudaMalloc) is free’d asynchronously (cudaFreeAsync).
See CUDA runtime documentation for cudaFreeAsync.

enumerator SANITIZER_CBID_RESOURCE_MEMPOOL_CREATED
A new mempool was created.

enumerator SANITIZER_CBID_RESOURCE_MEMPOOL_DESTROYING
A mempool is about to be destroyed.

enumerator SANITIZER_CBID_RESOURCE_MEMPOOL_PEER_ACCESS_ENABLED
A mempool is now accessible from a peer device.

enumerator SANITIZER_CBID_RESOURCE_MEMPOOL_PEER_ACCESS_DISABLING
A mempool is no longer accessible from a peer device.

enumerator SANITIZER_CBID_RESOURCE_ARRAY_CREATED
A CUDA array was created.

enumerator SANITIZER_CBID_RESOURCE_ARRAY_DESTROYED
A CUDA array was destroyed.

enumerator SANITIZER_CBID_RESOURCE_FUNCTIONS_LAZY_LOADED
CUDA functions were loaded lazily and are fully loaded.

enumerator SANITIZER_CBID_RESOURCE_FUNCTIONS_LAZY_PATCHED
CUDA lazily loaded functions were patched.

enumerator SANITIZER_CBID_RESOURCE_VIRTUAL_RESERVE
The CUDA driver reserved a virtual address range.

enumerator SANITIZER_CBID_RESOURCE_VIRTUAL_RELEASE
The CUDA driver released a virtual address range.

enumerator SANITIZER_CBID_RESOURCE_MEMPOOL_IMPORT_POINTER
A memory pool allocation was imported.

enumerator SANITIZER_CBID_RESOURCE_GREEN_CONTEXT_CREATION_FINISHED
A new green context was created.

enumerator SANITIZER_CBID_RESOURCE_GREEN_CONTEXT_DESTROY_STARTING
A green context is about to be destroyed.

enumerator SANITIZER_CBID_RESOURCE_GREEN_CONTEXT_DESTROY_FINISHED
A green context was destroyed.

enumerator SANITIZER_CBID_RESOURCE_SIZE

enumerator SANITIZER_CBID_RESOURCE_FORCE_INT


enum Sanitizer_CallbackIdUvm
Callback IDs for managed memory domain.
Callback IDs for resource domain SANITIZER_CB_DOMAIN_UVM. This value is communicated to the callback function via the cbid parameter.
Values:

enumerator SANITIZER_CBID_UVM_INVALID
Invalid managed memory callback ID.

enumerator SANITIZER_CBID_UVM_ATTACH_MEM
Modify the stream association of an allocation (see cudaStreamAttachMemAsync)

enumerator SANITIZER_CBID_UVM_SIZE

enumerator SANITIZER_CBID_UVM_FORCE_ITN


enum Sanitizer_MemcpyDirection
Memcpy direction.
Indicates the direction of a memcpy, passed inside Sanitizer_Memcpydata.
Values:

enumerator SANITIZER_MEMCPY_DIRECTION_UNKNOWN
Unknown memcpy direction.

enumerator SANITIZER_MEMCPY_DIRECTION_HOST_TO_HOST
Memcpy from host to host.

enumerator SANITIZER_MEMCPY_DIRECTION_HOST_TO_DEVICE
Memcpy from host to device.

enumerator SANITIZER_MEMCPY_DIRECTION_DEVICE_TO_HOST
Memcpy from device to host.

enumerator SANITIZER_MEMCPY_DIRECTION_DEVICE_TO_DEVICE
Memcpy from device to device.

enumerator SANITIZER_MEMCPY_DIRECTION_SIZE

enumerator SANITIZER_MEMCPY_DIRECTION_FORCE_INT


enum Sanitizer_MemoryVisibility
Specifies the visibility of an allocation.
Specifies the visibility of an allocation. This is typically GLOBAL on allocations made via cudaMalloc, cudaHostAlloc and similar APIs. This can be GLOBAL or HOST for cudaMallocManaged allocations depending on the flags parameter. This can be changed after allocation time using cudaMemAttachSingle API (see SANITIZER_CBID_UVM_ATTACH_MEM for the corresponding callback).
Values:

enumerator SANITIZER_MEMORY_VISIBILITY_INVALID
Invalid memory visibility.

enumerator SANITIZER_MEMORY_VISIBILITY_GLOBAL
Memory can be accessed by any stream on any device (see cudaMemAttachGlobal).

enumerator SANITIZER_MEMORY_VISIBILITY_HOST
Memory cannot be accessed by any stream on any device (see cudaMemAttachHost).

enumerator SANITIZER_MEMORY_VISIBILITY_STREAM
Memory can only be accessed by a single stream on the associated device (see cudaMemAttachSingle).

enumerator SANITIZER_MEMORY_VISIBILITY_FORCE_INT


enum Sanitizer_ResourceMemoryFlags
Flags describing a memory allocation.
Flags describing a memory allocation. These values are to be used in order to interpret the value of Sanitizer_ResourceMemoryData::flags.
Values:

enumerator SANITIZER_MEMORY_FLAG_NONE
Empty flag.

enumerator SANITIZER_MEMORY_FLAG_MODULE
Specifies that the allocation is static scoped to a module.

enumerator SANITIZER_MEMORY_FLAG_MANAGED
Specifies that the allocation is managed memory.

enumerator SANITIZER_MEMORY_FLAG_HOST_MAPPED
Species that the allocation accessible from the host.

enumerator SANITIZER_MEMORY_FLAG_HOST_PINNED
Specifies that the allocation is pinned on the host.

enumerator SANITIZER_MEMORY_FLAG_PEER
Specifies that the allocation is located on a peer GPU.

enumerator SANITIZER_MEMORY_FLAG_PEER_ATOMIC
Specifies that the allocation is located on a peer GPU supporting native atomics.
This implies that SANITIZER_MEMORY_FLAG_PEER is set as well.

enumerator SANITIZER_MEMORY_FLAG_CG_RUNTIME
Specifies that the allocation is used by the Cooperative Groups runtime functions.

enumerator SANITIZER_MEMORY_FLAG_CNP
Specifies that this is an allocation used for CUDA Dynamic Parallelism purposes.

enumerator SANITIZER_MEMORY_FLAG_FORCE_INT


enum Sanitizer_ResourceMemoryPermissions
Permissions for a memory allocation.
Permissions for a memory allocation. These values are to be used in order to interpret the value of Sanitizer_ResourceMemoryData::permissions.
Values:

enumerator SANITIZER_MEMORY_PERMISSION_NONE
No permissions.

enumerator SANITIZER_MEMORY_PERMISSION_READ
Specifies that the allocation is readable.

enumerator SANITIZER_MEMORY_PERMISSION_WRITE
Specifies that the allocation is writable.

enumerator SANITIZER_MEMORY_PERMISSION_ATOMIC
Specifies that the allocation is readable/writable with atomic operations.

enumerator SANITIZER_MEMORY_PERMISSION_ALL
Specifies that the allocation has all permissions.

enumerator SANITIZER_MEMORY_PERMISSION_FORCE_INT


## Functions


SanitizerResult sanitizerEnableAllDomains(

uint32_t enable,
Sanitizer_SubscriberHandle subscriber,

)
Enable or disable all callbacks in all domains.
Enable or disable all callbacks in all domains.

Note
Thread-safety: a subscriber must serialize access to sanitizerGetCallbackState, sanitizerEnableCallback, sanitizerEnableDomain, and sanitizerEnableAllDomains. For example, if sanitizerGetCallbackState(sub,
d, *) and sanitizerEnableAllDomains(sub) are called concurrently, the results are undefined.

Parameters:

enable – New enable state for all callbacks in all domains. Zero disables all callbacks, non-zero enables all callbacks.
subscriber – - Handle of the initialized subscriber.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_NOT_INITIALIZED – if unable to initialize the sanitizer.
SANITIZER_ERROR_INVALID_PARAMETER – if subscriber is invalid.


SanitizerResult sanitizerEnableCallback(

uint32_t enable,
Sanitizer_SubscriberHandle subscriber,
Sanitizer_CallbackDomain domain,
Sanitizer_CallbackId cbid,

)
Enable or disable callbacks for a specific domain and callback ID.
Enable or disable callbacks for a subscriber for a specific domain and callback ID.

Note
Thread-safety: a subscriber must serialize access to sanitizerGetCallbackState, sanitizerEnableCallback, sanitizerEnableDomain, and sanitizerEnableAllDomains. For example, if sanitizerGetCallbackState(sub, d,
c) and sanitizerEnableCallback(sub, d, c) are called concurrently, the results are undefined.

Parameters:

enable – New enable state for the callback. Zero disables the callback, non-zero enables the callback.
subscriber – - Handle of the initialized subscriber.
domain – The domain of the callback.
cbid – The ID of the callback.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_NOT_INITIALIZED – if unable to initialize the sanitizer.
SANITIZER_ERROR_INVALID_PARAMETER – if subscriber, domain or cbid is invalid.


SanitizerResult sanitizerEnableDomain(

uint32_t enable,
Sanitizer_SubscriberHandle subscriber,
Sanitizer_CallbackDomain domain,

)
Enable or disable all callbacks for a specific domain.
Enable or disable all callbacks for a specific domain.

Note
Thread-safety: a subscriber must serialize access to sanitizerGetCallbackState, sanitizerEnableCallback, sanitizerEnableDomain, and sanitizerEnableAllDomains. For example, if sanitizerGetCallbackEnabled(sub,
d, *) and sanitizerEnableDomain(sub, d) are called concurrently, the results are undefined.

Parameters:

enable – New enable state for all callbacks in the domain. Zero disables all callbacks, non-zero enables all callbacks.
subscriber – - Handle of the initialized subscriber.
domain – The domain of the callback.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_NOT_INITIALIZED – if unable to initialize the sanitizer.
SANITIZER_ERROR_INVALID_PARAMETER – if subscriber or domain is invalid.


SanitizerResult sanitizerGetCallbackState(

uint32_t *enable,
Sanitizer_SubscriberHandle subscriber,
Sanitizer_CallbackDomain domain,
Sanitizer_CallbackId cbid,

)
Get the current enabled/disabled state of a callback for a specific domain and function ID.
Returns non-zero in *enable if the callback for a domain and callback ID is enabled, and zero if not enabled.

Note
Thread-safety: a subscriber must serialize access to sanitizerGetCallbackState, sanitizerEnableCallback, sanitizerEnableDomain, and sanitizerEnableAllDomains. For example, if sanitizerGetCallbackState(sub, d,
c) and sanitizerEnableCallback(sub, d, c) are called concurrently, the results are undefined.

Parameters:

enable – Returns non-zero if callback enabled, zero if not enabled.
subscriber – Handle to the initialized subscriber.
domain – The domain of the callback.
cbid – The ID of the callback.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_NOT_INITIALIZED – if unable to initialize the sanitizer.
SANITIZER_ERROR_INVALID_PARAMETER – if enabled is NULL, or if subscriber, domain or cbid is invalid.


SanitizerResult sanitizerSubscribe(

Sanitizer_SubscriberHandle *subscriber,
Sanitizer_CallbackFunc callback,
void *userdata,

)
Initialize a callback subscriber with a callback function and user data.
Initialize a callback subscriber with a callback function and (optionally) a pointer to user data. The returned subscriber handle can be used to enable and disable the callback for specific domains and callback IDs.

Note
Only one subscriber can be registered at a time.

Note
This function does not enable any callbacks.

Note
Thread-safety: this function is thread safe.

Parameters:

subscriber – Returns handle to initialize subscriber.
callback – The callback function.
userdata – A pointer to user data. This data will be passed to the callback function via the userdata parameter.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_NOT_INITIALIZED – if unable to initialize the sanitizer.
SANITIZER_ERROR_MAX_LIMIT_RACHED – if there is already a sanitizer subscriber.
SANITIZER_ERROR_INVALID_PARAMETER – if subscriber is NULL.


SanitizerResult sanitizerUnsubscribe(

Sanitizer_SubscriberHandle subscriber,

)
Unregister a callback subscriber.
Removes a callback subscriber so that no future callback will be issued to that subscriber.

Note
Thread-safety: this function is thread safe.

Parameters:
subscriber – Handle to the initialized subscriber.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_NOT_INITIALIZED – if unable to initialize the sanitizer.
SANITIZER_ERROR_INVALID_PARAMETER – if subscriber is NULL or not initialized.