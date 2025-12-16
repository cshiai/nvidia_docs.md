# Sanitizer_MemsetData


struct Sanitizer_MemsetData
Data passed into a memset callback function.
Data passed into a launch callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_MEMSET. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

uint64_t address
The address of the memset start.

CUcontext context
The context where the allocation is located.

uint32_t elementSize

uint64_t height

Sanitizer_StreamHandle hStream
Unique handle for the stream.

uint32_t isAsync
Boolean value indicating if the transfer is asynchronous.

uint64_t pitch

CUstream stream
The stream where the memset is executed.

uint32_t value
Value to be written.

uint64_t width
Memset size configuration.