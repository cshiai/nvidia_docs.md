# 6.2. CUPTI Callback API


Functions, types, and enums that implement the CUPTI Callback API.


## 6.2.1. Data Structures


CUpti_CallbackData
Data passed into a runtime or driver API callback function.

CUpti_GraphData
CUDA graphs data passed into a resource callback function.

CUpti_ModuleResourceData
Module data passed into a resource callback function.

CUpti_NvtxData
Data passed into a NVTX callback function.

CUpti_ResourceData
Data passed into a resource callback function.

CUpti_StateData
Data passed into a State callback function.

CUpti_StreamAttrData
Stream attribute data passed into a resource callback function for CUPTI_CBID_RESOURCE_STREAM_ATTRIBUTE_CHANGED callback.

CUpti_SubscriberParams
Params for cuptiSubscribe_v2.

CUpti_SynchronizeData
Data passed into a synchronize callback function.


## 6.2.2. Macros


CUPTI_CALLBACK_STRUCT_SIZECUPTI_OLD_SUBSCRIBER_NAME_MIN_LEN
The minimum size of the of the old subscriber name in bytes.

CUPTI_SUBSCRIBER_NAME_MAX_LEN
The max size of the CUPTI subscriber name in bytes.

CUpti_SubscriberParams_STRUCT_SIZE

## 6.2.3. Enumerations


CUpti_ApiCallbackSite
Specifies the point in an API call that a callback is issued.

CUpti_CallbackDomain
Callback domains.

CUpti_CallbackIdResource
Callback IDs for resource domain.

CUpti_CallbackIdState
Callback IDs for state domain.

CUpti_CallbackIdSync
Callback IDs for synchronization domain.


## 6.2.4. Functions


CUptiResult cuptiEnableAllDomains(uint32_t enable, CUpti_SubscriberHandle subscriber)
Enable or disable all callbacks in all domains.

CUptiResult cuptiEnableCallback(uint32_t enable, CUpti_SubscriberHandle subscriber, CUpti_CallbackDomain domain, CUpti_CallbackId cbid)
Enable or disabled callbacks for a specific domain and callback ID.

CUptiResult cuptiEnableDomain(uint32_t enable, CUpti_SubscriberHandle subscriber, CUpti_CallbackDomain domain)
Enable or disabled all callbacks for a specific domain.

CUptiResult cuptiGetCallbackName(CUpti_CallbackDomain domain, uint32_t cbid, const char name)
Get the name of a callback for a specific domain and callback ID.

CUptiResult cuptiGetCallbackState(uint32_t *enable, CUpti_SubscriberHandle subscriber, CUpti_CallbackDomain domain, CUpti_CallbackId cbid)
Get the current enabled/disabled state of a callback for a specific domain and function ID.

CUptiResult cuptiSubscribe(CUpti_SubscriberHandle *subscriber, CUpti_CallbackFunc callback, void *userdata)
Initialize a callback subscriber with a callback function and user data.

CUptiResult cuptiSubscribe_v2(CUpti_SubscriberHandle *subscriber, CUpti_CallbackFunc callback, void *userdata, CUpti_SubscriberParams *pParams)
Initialize a callback subscriber with a callback function and user data.

CUptiResult cuptiSupportedDomains(size_t *domainCount, CUpti_DomainTable *domainTable)
Get the available callback domains.

CUptiResult cuptiUnsubscribe(CUpti_SubscriberHandle subscriber)
Unregister a callback subscriber.


## 6.2.5. Typedefs


CUpti_CallbackFunc
Function type for a callback.

CUpti_CallbackId
An ID for a driver API, runtime API, resource or synchronization callback.

CUpti_DomainTable
Pointer to an array of callback domains.

CUpti_SubscriberHandle
A callback subscriber.


## 6.2.6. Macros


CUPTI_CALLBACK_STRUCT_SIZE(type_, lastfield_)CUPTI_OLD_SUBSCRIBER_NAME_MIN_LEN
The minimum size of the of the old subscriber name in bytes.


CUPTI_SUBSCRIBER_NAME_MAX_LEN
The max size of the CUPTI subscriber name in bytes.
The total size of the CUPTI subscriber name is 64 bytes. CUPTI adds a 10 byte prefix and a null terminator, leaving 53 bytes for the user supplied subscriber name.


CUpti_SubscriberParams_STRUCT_SIZE

## 6.2.7. Enumerations


enum CUpti_ApiCallbackSite
Specifies the point in an API call that a callback is issued.
Specifies the point in an API call that a callback is issued. This value is communicated to the callback function via CUpti_CallbackData::callbackSite.
Values:

enumerator CUPTI_API_ENTER
The callback is at the entry of the API call.

enumerator CUPTI_API_EXIT
The callback is at the exit of the API call.

enumerator CUPTI_API_CBSITE_FORCE_INT


enum CUpti_CallbackDomain
Callback domains.
Callback domains. Each domain represents callback points for a group of related API functions or CUDA driver activity.
Values:

enumerator CUPTI_CB_DOMAIN_INVALID
Invalid domain.

enumerator CUPTI_CB_DOMAIN_DRIVER_API
Domain containing callback points for all driver API functions.

enumerator CUPTI_CB_DOMAIN_RUNTIME_API
Domain containing callback points for all runtime API functions.

enumerator CUPTI_CB_DOMAIN_RESOURCE
Domain containing callback points for CUDA resource tracking.

enumerator CUPTI_CB_DOMAIN_SYNCHRONIZE
Domain containing callback points for CUDA synchronization.

enumerator CUPTI_CB_DOMAIN_NVTX
Domain containing callback points for NVTX API functions.

enumerator CUPTI_CB_DOMAIN_STATE
Domain containing callback points for various states.

enumerator CUPTI_CB_DOMAIN_SIZE

enumerator CUPTI_CB_DOMAIN_FORCE_INT


enum CUpti_CallbackIdResource
Callback IDs for resource domain.
Callback IDs for resource domain, CUPTI_CB_DOMAIN_RESOURCE. This value is communicated to the callback function via the cbid parameter.
Values:

enumerator CUPTI_CBID_RESOURCE_INVALID
Invalid resource callback ID.

enumerator CUPTI_CBID_RESOURCE_CONTEXT_CREATED
A new context has been created.

enumerator CUPTI_CBID_RESOURCE_CONTEXT_DESTROY_STARTING
A context is about to be destroyed.

enumerator CUPTI_CBID_RESOURCE_STREAM_CREATED
A new stream has been created.

enumerator CUPTI_CBID_RESOURCE_STREAM_DESTROY_STARTING
A stream is about to be destroyed.

enumerator CUPTI_CBID_RESOURCE_CU_INIT_FINISHED
The driver has finished initializing.

enumerator CUPTI_CBID_RESOURCE_MODULE_LOADED
A module has been loaded.

enumerator CUPTI_CBID_RESOURCE_MODULE_UNLOAD_STARTING
A module is about to be unloaded.

enumerator CUPTI_CBID_RESOURCE_MODULE_PROFILED
The current module which is being profiled.

enumerator CUPTI_CBID_RESOURCE_GRAPH_CREATED
CUDA graph has been created.

enumerator CUPTI_CBID_RESOURCE_GRAPH_DESTROY_STARTING
CUDA graph is about to be destroyed.

enumerator CUPTI_CBID_RESOURCE_GRAPH_CLONED
CUDA graph is cloned.

enumerator CUPTI_CBID_RESOURCE_GRAPHNODE_CREATE_STARTING
CUDA graph node is about to be created.

enumerator CUPTI_CBID_RESOURCE_GRAPHNODE_CREATED
CUDA graph node is created.

enumerator CUPTI_CBID_RESOURCE_GRAPHNODE_DESTROY_STARTING
CUDA graph node is about to be destroyed.

enumerator CUPTI_CBID_RESOURCE_GRAPHNODE_DEPENDENCY_CREATED
Dependency on a CUDA graph node is created.

enumerator CUPTI_CBID_RESOURCE_GRAPHNODE_DEPENDENCY_DESTROY_STARTING
Dependency on a CUDA graph node is destroyed.

enumerator CUPTI_CBID_RESOURCE_GRAPHEXEC_CREATE_STARTING
An executable CUDA graph is about to be created.

enumerator CUPTI_CBID_RESOURCE_GRAPHEXEC_CREATED
An executable CUDA graph is created.

enumerator CUPTI_CBID_RESOURCE_GRAPHEXEC_DESTROY_STARTING
An executable CUDA graph is about to be destroyed.

enumerator CUPTI_CBID_RESOURCE_GRAPHNODE_CLONED
CUDA graph node is cloned.

enumerator CUPTI_CBID_RESOURCE_STREAM_ATTRIBUTE_CHANGED
CUDA stream attribute is changed.

enumerator CUPTI_CBID_RESOURCE_GRAPH_NODE_UPDATED
CUDA graph node is updated.

enumerator CUPTI_CBID_RESOURCE_GRAPH_NODE_SET_PARAMS
Params are set for the CUDA graph node in the executable graph.

enumerator CUPTI_CBID_RESOURCE_SIZE

enumerator CUPTI_CBID_RESOURCE_FORCE_INT


enum CUpti_CallbackIdState
Callback IDs for state domain.
Callback IDs for state domain, CUPTI_CB_DOMAIN_STATE. This value is communicated to the callback function via the cbid parameter.
Values:

enumerator CUPTI_CBID_STATE_INVALID
Invalid state callback ID.

enumerator CUPTI_CBID_STATE_FATAL_ERROR
Notification of fatal errors - high impact, non-recoverable When encountered, CUPTI automatically invokes cuptiFinalize() User can control behavior of the application in future from receiving this callback - such as continuing without profiling, or terminating the whole application.

enumerator CUPTI_CBID_STATE_ERROR
Notification of non fatal errors - high impact, but recoverable This notification is not issued in the current release.

enumerator CUPTI_CBID_STATE_WARNING
Notification of warnings - low impact, recoverable.

enumerator CUPTI_CBID_STATE_SIZE

enumerator CUPTI_CBID_STATE_FORCE_INT


enum CUpti_CallbackIdSync
Callback IDs for synchronization domain.
Callback IDs for synchronization domain, CUPTI_CB_DOMAIN_SYNCHRONIZE. This value is communicated to the callback function via the cbid parameter.
Values:

enumerator CUPTI_CBID_SYNCHRONIZE_INVALID
Invalid synchronize callback ID.

enumerator CUPTI_CBID_SYNCHRONIZE_STREAM_SYNCHRONIZED
Stream synchronization has completed for the stream.

enumerator CUPTI_CBID_SYNCHRONIZE_CONTEXT_SYNCHRONIZED
Context synchronization has completed for the context.

enumerator CUPTI_CBID_SYNCHRONIZE_SIZE

enumerator CUPTI_CBID_SYNCHRONIZE_FORCE_INT


## 6.2.8. Functions


CUptiResult cuptiEnableAllDomains(

uint32_t enable,
CUpti_SubscriberHandle subscriber,

)
Enable or disable all callbacks in all domains.
Enable or disable all callbacks in all domains.

Note
Thread-safety: a subscriber must serialize access to cuptiGetCallbackState, cuptiEnableCallback, cuptiEnableDomain, and cuptiEnableAllDomains. For example, if cuptiGetCallbackState(sub,
d, *) and cuptiEnableAllDomains(sub) are called concurrently, the results are undefined.

Parameters:

enable – New enable state for all callbacks in all domain. Zero disables all callbacks, non-zero enables all callbacks.
subscriber – - Handle to callback subscription

Return values:

CUPTI_SUCCESS – on success
CUPTI_ERROR_NOT_INITIALIZED – if unable to initialized CUPTI
CUPTI_ERROR_INVALID_PARAMETER – if subscriber is invalid


CUptiResult cuptiEnableCallback(

uint32_t enable,
CUpti_SubscriberHandle subscriber,
CUpti_CallbackDomain domain,
CUpti_CallbackId cbid,

)
Enable or disabled callbacks for a specific domain and callback ID.
Enable or disabled callbacks for a subscriber for a specific domain and callback ID.

Note
Thread-safety: a subscriber must serialize access to cuptiGetCallbackState, cuptiEnableCallback, cuptiEnableDomain, and cuptiEnableAllDomains. For example, if cuptiGetCallbackState(sub,
d, c) and cuptiEnableCallback(sub, d, c) are called concurrently, the results are undefined.

Parameters:

enable – New enable state for the callback. Zero disables the callback, non-zero enables the callback.
subscriber – - Handle to callback subscription
domain – The domain of the callback
cbid – The ID of the callback

Return values:

CUPTI_SUCCESS – on success
CUPTI_ERROR_NOT_INITIALIZED – if unable to initialized CUPTI
CUPTI_ERROR_INVALID_PARAMETER – if subscriber, domain or cbid is invalid.


CUptiResult cuptiEnableDomain(

uint32_t enable,
CUpti_SubscriberHandle subscriber,
CUpti_CallbackDomain domain,

)
Enable or disabled all callbacks for a specific domain.
Enable or disabled all callbacks for a specific domain.

Note
Thread-safety: a subscriber must serialize access to cuptiGetCallbackState, cuptiEnableCallback, cuptiEnableDomain, and cuptiEnableAllDomains. For example, if cuptiGetCallbackEnabled(sub,
d, *) and cuptiEnableDomain(sub, d) are called concurrently, the results are undefined.

Parameters:

enable – New enable state for all callbacks in the domain. Zero disables all callbacks, non-zero enables all callbacks.
subscriber – - Handle to callback subscription
domain – The domain of the callback

Return values:

CUPTI_SUCCESS – on success
CUPTI_ERROR_NOT_INITIALIZED – if unable to initialized CUPTI
CUPTI_ERROR_INVALID_PARAMETER – if subscriber or domain is invalid


CUptiResult cuptiGetCallbackName(

CUpti_CallbackDomain domain,
uint32_t cbid,
const char name,

)
Get the name of a callback for a specific domain and callback ID.
Returns a pointer to the name c_string in name.

Note
Names are available only for the DRIVER and RUNTIME domains.

Parameters:

domain – The domain of the callback
cbid – The ID of the callback
name – Returns pointer to the name string on success, NULL otherwise

Return values:

CUPTI_SUCCESS – on success
CUPTI_ERROR_INVALID_PARAMETER – if name is NULL, or if domain or cbid is invalid.


CUptiResult cuptiGetCallbackState(

uint32_t *enable,
CUpti_SubscriberHandle subscriber,
CUpti_CallbackDomain domain,
CUpti_CallbackId cbid,

)
Get the current enabled/disabled state of a callback for a specific domain and function ID.
Returns non-zero in *enable if the callback for a domain and callback ID is enabled, and zero if not enabled.

Note
Thread-safety: a subscriber must serialize access to cuptiGetCallbackState, cuptiEnableCallback, cuptiEnableDomain, and cuptiEnableAllDomains. For example, if cuptiGetCallbackState(sub,
d, c) and cuptiEnableCallback(sub, d, c) are called concurrently, the results are undefined.

Parameters:

enable – Returns non-zero if callback enabled, zero if not enabled
subscriber – Handle to the initialize subscriber
domain – The domain of the callback
cbid – The ID of the callback

Return values:

CUPTI_SUCCESS – on success
CUPTI_ERROR_NOT_INITIALIZED – if unable to initialized CUPTI
CUPTI_ERROR_INVALID_PARAMETER – if enabled is NULL, or if subscriber, domain or cbid is invalid.


CUptiResult cuptiSubscribe(

CUpti_SubscriberHandle *subscriber,
CUpti_CallbackFunc callback,
void *userdata,

)
Initialize a callback subscriber with a callback function and user data.
Initializes a callback subscriber with a callback function and (optionally) a pointer to user data. The returned subscriber handle can be used to enable and disable the callback for specific domains and callback IDs.

Note
Only a single subscriber can be registered at a time. To ensure that no other CUPTI client interrupts the profiling session, it’s the responsibility of all the CUPTI clients to call this function before starting the profling session. In case profiling session is already started by another CUPTI client, this function returns the error code CUPTI_ERROR_MULTIPLE_SUBSCRIBERS_NOT_SUPPORTED. Note that this function returns the same error when application is launched using NVIDIA tools like Nsight Systems, Nsight Compute, cuda-gdb and cuda-memcheck.

Note
This function does not enable any callbacks.

Note
Thread-safety: this function is thread safe.

Note
While this API is fully supported and remains available, we recommend transitioning to the new API cuptiSubscribe_v2 moving forward.

Parameters:

subscriber – Returns handle to initialize subscriber
callback – The callback function
userdata – A pointer to user data. This data will be passed to the callback function via the userdata parameter.

Return values:

CUPTI_SUCCESS – on success
CUPTI_ERROR_NOT_INITIALIZED – if unable to initialize CUPTI
CUPTI_ERROR_MULTIPLE_SUBSCRIBERS_NOT_SUPPORTED – if there is already a CUPTI subscriber, or if the application is launched with NVIDIA tools like Nsight Systems, Nsight Compute, cuda-gdb and cuda-memcheck.
CUPTI_ERROR_INVALID_PARAMETER – if subscriber is NULL


CUptiResult cuptiSubscribe_v2(

CUpti_SubscriberHandle *subscriber,
CUpti_CallbackFunc callback,
void *userdata,
CUpti_SubscriberParams *pParams,

)
Initialize a callback subscriber with a callback function and user data.
Initializes a callback subscriber with a callback function and (optionally) a pointer to user data. The returned subscriber handle can be used to enable and disable the callback for specific domains and callback IDs.

Note
Only a single subscriber can be registered at a time. To ensure that no other CUPTI client interrupts the profiling session, it’s the responsibility of all the CUPTI clients to call this function before starting the profling session. In case profiling session is already started by another CUPTI client, this function returns the error code CUPTI_ERROR_MULTIPLE_SUBSCRIBERS_NOT_SUPPORTED. Note that this function returns the same error when application is launched using NVIDIA tools like Nsight Systems, Nsight Compute, cuda-gdb and cuda-memcheck.

Note
This function does not enable any callbacks.

Note
Thread-safety: this function is thread safe.

Parameters:

subscriber – Returns handle to initialize subscriber
callback – The callback function
userdata – A pointer to user data. This data will be passed to the callback function via the userdata parameter.
pParams – A pointer to CUpti_SubscriberParams. Can be NULL.

Return values:

CUPTI_SUCCESS – on success
CUPTI_ERROR_NOT_INITIALIZED – if unable to initialize CUPTI
CUPTI_ERROR_MULTIPLE_SUBSCRIBERS_NOT_SUPPORTED – if there is already a CUPTI subscriber, or if the application is launched with NVIDIA tools like Nsight Systems, Nsight Compute, cuda-gdb and cuda-memcheck.
CUPTI_ERROR_INVALID_PARAMETER – if:
pParams.structSize is not filled with the size of the structure


CUptiResult cuptiSupportedDomains(

size_t *domainCount,
CUpti_DomainTable *domainTable,

)
Get the available callback domains.
Returns in *domainTable an array of size *domainCount of all the available callback domains.

Note
Thread-safety: this function is thread safe.

Parameters:

domainCount – Returns number of callback domains
domainTable – Returns pointer to array of available callback domains

Return values:

CUPTI_SUCCESS – on success
CUPTI_ERROR_NOT_INITIALIZED – if unable to initialize CUPTI
CUPTI_ERROR_INVALID_PARAMETER – if domainCount or domainTable are NULL


CUptiResult cuptiUnsubscribe(CUpti_SubscriberHandle subscriber)
Unregister a callback subscriber.
Removes a callback subscriber so that no future callbacks will be issued to that subscriber.

Note
Thread-safety: this function is thread safe.

Parameters:
subscriber – Handle to the initialize subscriber

Return values:

CUPTI_SUCCESS – on success
CUPTI_ERROR_NOT_INITIALIZED – if unable to initialized CUPTI
CUPTI_ERROR_INVALID_PARAMETER – if subscriber is NULL or not initialized


## 6.2.9. Typedefs


typedef void (*CUpti_CallbackFunc)(void *userdata, CUpti_CallbackDomain domain, CUpti_CallbackId cbid, const void *cbdata)
Function type for a callback.
Function type for a callback. The type of the data passed to the callback in cbdata depends on the domain. If domain is CUPTI_CB_DOMAIN_DRIVER_API or CUPTI_CB_DOMAIN_RUNTIME_API the type of cbdata will be CUpti_CallbackData. If domain is CUPTI_CB_DOMAIN_RESOURCE the type of cbdata will be CUpti_ResourceData. If domain is CUPTI_CB_DOMAIN_SYNCHRONIZE the type of cbdata will be CUpti_SynchronizeData. If domain is CUPTI_CB_DOMAIN_NVTX the type of cbdata will be CUpti_NvtxData.

Param userdata:
User data supplied at subscription of the callback

Param domain:
The domain of the callback

Param cbid:
The ID of the callback

Param cbdata:
Data passed to the callback.


typedef uint32_t CUpti_CallbackId
An ID for a driver API, runtime API, resource or synchronization callback.
An ID for a driver API, runtime API, resource or synchronization callback. Within a driver API callback this should be interpreted as a CUpti_driver_api_trace_cbid value (these values are defined in cupti_driver_cbid.h). Within a runtime API callback this should be interpreted as a CUpti_runtime_api_trace_cbid value (these values are defined in cupti_runtime_cbid.h). Within a resource API callback this should be interpreted as a CUpti_CallbackIdResource value. Within a synchronize API callback this should be interpreted as a CUpti_CallbackIdSync value.


typedef CUpti_CallbackDomain *CUpti_DomainTable
Pointer to an array of callback domains.


typedef struct CUpti_Subscriber_st *CUpti_SubscriberHandle
A callback subscriber.