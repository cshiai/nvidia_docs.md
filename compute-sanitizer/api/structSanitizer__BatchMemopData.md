# Sanitizer_BatchMemopData


struct Sanitizer_BatchMemopData
Data passed into a batch memop callback function.
Data passed into a batch memop callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_BATCH_MEMOP. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

uint64_t address
The address of the operation.

Sanitizer_BatchMemopAtomicOp atomicOperation
The operation used for the atomic reduction.
Only valid for SANITIZER_CBID_BATCH_MEMOP_ATOMIC_REDUCTION.

CUcontext context
The context where the allocation is located.

Sanitizer_StreamHandle hStream
Unique handle for the stream.

CUstream stream
The stream where the batch memop is executed.

Sanitizer_BatchMemopType type
Size of the value used in the operation.

uint64_t value
The value used in the operation.