# Sanitizer_ExternalMemoryData


struct Sanitizer_ExternalMemoryData
Data passed into an external memory callback function.
Data passed into an event callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal tp SANITIZER_CB_DOMAIN_EXTERNAL_MEMORY. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

uint64_t address
Address of the mapped memory.
This field is only valid for SANITIZER_CBID_EXTERNAL_MEMORY_MAPPED.

CUcontext context
Context containing the external memory.

CUdevice device
Device containing the external memory.

CUexternalMemory extMemory
External memory object.

uint64_t size
Size of the memory imported or mapped.
This field is only valid for SANITIZER_CBID_EXTERNAL_MEMORY_IMPORT and SANITIZER_CBID_EXTERNAL_MEMORY_MAPPED.