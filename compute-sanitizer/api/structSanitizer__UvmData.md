# Sanitizer_UvmData


struct Sanitizer_UvmData
Data passed into a managed memory callback function.
Data passed into a managed memory callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_UVM. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

uint64_t address
The address of the allocation.

CUcontext context
The context where the allocation is located.

Sanitizer_StreamHandle hStream
Unique handle for the stream.

CUstream stream
The stream on which the memory is attached.
This is only valid if visibility is SANITIZER_MEMORY_VISIBILITY_STREAM.

Sanitizer_MemoryVisibility visibility
New visibility for the allocation.