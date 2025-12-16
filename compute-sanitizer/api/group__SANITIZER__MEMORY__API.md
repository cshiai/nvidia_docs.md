# Sanitizer Memory API


Functions, types, and enums that implement the Sanitizer Memory API.


## Functions


SanitizerResult sanitizerAlloc(CUcontext ctx, void devPtr, size_t size)
Allocate memory on the device.

SanitizerResult sanitizerAllocHost(CUcontext ctx, void devPtr, size_t size)
Allocate host pinned memory.

SanitizerResult sanitizerFree(CUcontext ctx, void *devPtr)
Frees memory on the device.

SanitizerResult sanitizerFreeHost(CUcontext ctx, void *devPtr)
Frees host memory.

SanitizerResult sanitizerMemcpyDeviceToHost(void *dst, void *src, size_t count, Sanitizer_StreamHandle stream)
Copies data from device to host.

SanitizerResult sanitizerMemcpyHostToDeviceAsync(void *dst, void *src, size_t count, Sanitizer_StreamHandle stream)
Copies data from host to device.

SanitizerResult sanitizerMemset(void *devPtr, int value, size_t count, Sanitizer_StreamHandle stream)
Initializes or sets device memory to a value.


## Functions


SanitizerResult sanitizerAlloc(

CUcontext ctx,
void devPtr,
size_t size,

)
Allocate memory on the device.
Equivalent of cudaMalloc that can be called within a callback function.

Note
Thread-safety: this function is thread safe.

Parameters:

ctx – Context for the allocation. If NULL, the current context will be used.
devPtr – Pointer to allocated device memory.
size – Allocation size in bytes.


SanitizerResult sanitizerAllocHost(

CUcontext ctx,
void devPtr,
size_t size,

)
Allocate host pinned memory.
Equivalent of cudaMallocHost that can be called within a callback function.

Note
Thread-safety: this function is thread safe.

Parameters:

ctx – Context for the allocation. If NULL, the current context will be used.
devPtr – Pointer to allocated host memory.
size – Allocation size in bytes.


SanitizerResult sanitizerFree(CUcontext ctx, void *devPtr)
Frees memory on the device.
Equivalent of cudaFree that can be called within a callback function.

Note
Thread-safety: this function is thread safe.

Parameters:

ctx – Context for the allocation. If NULL, the current context will be used.
devPtr – Device pointer to memory to free.


SanitizerResult sanitizerFreeHost(CUcontext ctx, void *devPtr)
Frees host memory.
Equivalent of cudaFreeHost that can be called within a callback function.

Note
Thread-safety: this function is thread safe.

Parameters:

ctx – Context for the allocation. If NULL, the current context will be used.
devPtr – Host pointer to memory to free.


SanitizerResult sanitizerMemcpyDeviceToHost(

void *dst,
void *src,
size_t count,
Sanitizer_StreamHandle stream,

)
Copies data from device to host.
Equivalent of cudaMemcpy that can be called within a callback function. The function will return once the copy has completed.

Note
Thread-safety: this function is thread safe.

Parameters:

dst – Destination memory address.
src – Source memory address.
count – Size in bytes to copy.
stream – Stream handle. If NULL, the NULL stream will be used.


SanitizerResult sanitizerMemcpyHostToDeviceAsync(

void *dst,
void *src,
size_t count,
Sanitizer_StreamHandle stream,

)
Copies data from host to device.
Equivalent of cudaMemcpyAsync that can be called within a callback function. The function will return once the pageable buffer has been copied to the staging memory for DMA transfer to device memory, but the DMA to final destination may not have completed.

Note
Thread-safety: this function is thread safe.

Parameters:

dst – Destination memory address.
src – Source memory address.
count – Size in bytes to copy.
stream – Stream handle. If NULL, the NULL stream will be used.


SanitizerResult sanitizerMemset(

void *devPtr,
int value,
size_t count,
Sanitizer_StreamHandle stream,

)
Initializes or sets device memory to a value.
Equivalent of cudaMemset that can be called within a callback function.

Note
Thread-safety: this function is thread safe.

Parameters:

devPtr – Pointer to device memory.
value – value to set for each byte of specified memory.
count – Size in bytes to set.
stream – Stream handle. If NULL, the NULL stream will be used.