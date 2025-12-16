# Sanitizer_SynchronizeData


struct Sanitizer_SynchronizeData
Data passed into a synchronization callback function.
Data passed into a synchronization callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_SYNCHRONIZE. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

CUcontext context
For SANITIZER_CBID_SYNCHRONIZE_CONTEXT_SYNCHRONIZED, this is the context being synchronized.
For SANITIZER_CBID_SYNCHRONIZE_STREAM_SYNCHRONIZED, this is the context of the stream being synchronized.

CUgreenCtx greenContext
The green context being synchronized.

Sanitizer_StreamHandle hStream
Unique handle for the stream.

CUstream stream
This field is only valid for SANITIZER_CBID_SYNCHRONIZE_STREAM_SYNCHRONIZED.
This is the stream being synchronized.