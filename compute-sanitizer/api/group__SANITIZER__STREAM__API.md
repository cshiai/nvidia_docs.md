# Sanitizer Stream API


Functions, types, and enums that implement the Sanitizer Stream API.


## Typedefs


Sanitizer_StreamHandle

## Functions


SanitizerResult sanitizerGetStream(Sanitizer_StreamHandle hStream, CUstream *stream)
Retrieve a CUstream handle from a Sanitizer_StreamHandle handle.

SanitizerResult sanitizerGetStreamHandle(CUcontext ctx, CUstream stream, Sanitizer_StreamHandle *hStream)
Retrieve a Sanitizer_StreamHandle handle from a CUstream handle.

SanitizerResult sanitizerStreamSynchronize(Sanitizer_StreamHandle stream)
Synchronize a given stream.


## Typedefs


typedef struct Sanitizer_Stream_st *Sanitizer_StreamHandle

## Functions


SanitizerResult sanitizerGetStream(

Sanitizer_StreamHandle hStream,
CUstream *stream,

)
Retrieve a CUstream handle from a Sanitizer_StreamHandle handle.

Note
Thread-safety: this function is thread safe.

Parameters:

hStream – [in] Sanitizer Stream handle.
stream – [out] Output CUstream handle.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_INVALID_PARAMETER – if hStream is not a valid Sanitizer stream handle or if stream is NULL.


SanitizerResult sanitizerGetStreamHandle(

CUcontext ctx,
CUstream stream,
Sanitizer_StreamHandle *hStream,

)
Retrieve a Sanitizer_StreamHandle handle from a CUstream handle.

Note
Thread-safety: this function is thread safe.

Parameters:

ctx – [in] Context owning the stream. If NULL, the current context will be used.
stream – [in] CUstream handle. If NULL, the NULL stream will be used.
hStream – [out] Output Sanitizer Stream handle.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_INVALID_PARAMETER – if stream is not a valid CUstream handle or if hStream is NULL.


SanitizerResult sanitizerStreamSynchronize(

Sanitizer_StreamHandle stream,

)
Synchronize a given stream.
Equivalent of cudaStreamSynchronize that can be called with a sanitizer stream handle

Note
Thread-safety: this function is thread safe.

Parameters:
stream – Stream handle. If NULL, the NULL stream will be used.