# Sanitizer_ResourceStreamData


struct Sanitizer_ResourceStreamData
Data passed into a stream resource callback function.
Data passed into a stream resource callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_RESOURCE and cbid equal to SANITIZER_CBID_RESOURCE_STREAM_CREATED, SANITIZER_CBID_RESOURCE_STREAM_DESTROY_STARTING or SANITIZER_CBID_RESOURCE_STREAM_DESTROY_FINISHED. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

CUcontext context
The context containing the stream being created or destroyed.

CUgreenCtx greenContext
The green context containing the stream being created or destroyed.

Sanitizer_StreamHandle hStream
Unique handle for the stream.

CUstream stream
The stream being created or destroyed.
This handle will be NULL for the STREAM_DESTROY_FINISHED cbid.