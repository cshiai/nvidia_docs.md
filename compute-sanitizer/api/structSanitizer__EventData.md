# Sanitizer_EventData


struct Sanitizer_EventData
Data passed into an event callback function.
Data passed into an event callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal tp SANITIZER_CB_DOMAIN_EVENTS. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

CUcontext context
For SANITIZER_CBID_EVENTS_CREATED, SANITIZER_CBID_EVENTS_DESTROYED, SANITIZER_CBID_EVENTS_SYNCHNONIZED, SANITIZER_CBID_CTX_RECORD_EVENT, SANITIZER_CBID_CTX_WAIT_EVENT this is the context containing the event.
For SANITIZER_CBID_GREEN_CTX_RECORD_EVENT, SANITIZER_CBID_GREEN_CTX_WAIT_EVENT this is the parent context for green context containing the event. For SANITIZER_CBID_EVENTS_RECORD and SANITIZER_CBID_EVENTS_STREAM_WAIT, this is the context containing the stream being recorded or waiting.

CUevent event
The event recording or being waited.

CUgreenCtx greenCtx
For SANITIZER_CBID_GREEN_CTX_RECORD_EVENT, SANITIZER_CBID_GREEN_CTX_WAIT_EVENT this is the green context containing the event.

Sanitizer_StreamHandle hStream
Unique handle for the stream.

CUstream stream
The stream being recorded or waiting.
Available if cbid is SANITIZER_CBID_EVENTS_RECORD or SANITIZER_CBID_EVENTS_STREAM_WAIT.