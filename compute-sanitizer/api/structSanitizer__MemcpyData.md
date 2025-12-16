# Sanitizer_MemcpyData


struct Sanitizer_MemcpyData
Data passed into a memcpy callback function.
Data passed into a launch callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_MEMCPY. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

CUcontext apiContext
The context on which the operation was requested.

CUstream apiStream
The stream on which the operation was requested.

uint64_t depth

Sanitizer_MemcpyDirection direction
The direction of the transfer.

uint64_t dstAddress
The destination allocation address.

CUcontext dstContext
The context where the destination allocation is located.

uint64_t dstPitch
The destination allocation pitch.

CUstream dstStream
The stream where the memcpy is executed on the destination context.

Sanitizer_StreamHandle hApiStream
Unique handle for the API stream.

Sanitizer_StreamHandle hDstStream
Unique handle for the destination context stream.

uint64_t height

Sanitizer_StreamHandle hSrcStream
Unique handle for the source context stream.

uint32_t isAsync
Boolean value indicating if the transfer is asynchronous.

uint64_t size
Size of the transfer in bytes.

uint64_t srcAddress
The source allocation address.

CUcontext srcContext
The context where the source allocation is located.

uint64_t srcPitch
The source allocation pitch.

CUstream srcStream
The stream where the memcpy is executed on the source context.

uint64_t width
Memcpy size configuration.