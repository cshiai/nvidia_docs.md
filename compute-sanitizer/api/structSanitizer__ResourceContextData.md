# Sanitizer_ResourceContextData


struct Sanitizer_ResourceContextData
Data passed into a context resource callback function.
Data passed into a context resource callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_RESOURCE and cbid equal to SANITIZER_CBID_RESOURCE_CONTEXT_CREATION_STARTING, SANITIZER_CBID_RESOURCE_CONTEXT_CREATION_FINISHED, SANITIZER_CBID_RESOURCE_CONTEXT_DESTROY_STARTING or SANITIZER_CBID_RESOURCE_CONTEXT_DESTROY_FINISHED. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

CUcontext context
The context being created or destroyed.

CUdevice device
The device on which the context is being created or destroyed.
This field is only valid for SANITIZER_CBID_RESOURCE_CONTEXT_CREATION_* callbacks.

CUgreenCtx greenContext
The green context being created or destroyed.