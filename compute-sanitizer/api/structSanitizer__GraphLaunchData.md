# Sanitizer_GraphLaunchData


struct Sanitizer_GraphLaunchData
Data passed into a graph launch callback function.
Data passed into a graphs callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_GRAPHS and cbid equal to SANITIZER_CBID_GRAPHS_LAUNCH_BEGIN or SANITIZER_CBID_GRAPHS_LAUNCH_END. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

CUcontext context
The context where the graph is launched.

CUgraphExec graphExec
Instance of the CUDA graph being launched.

Sanitizer_StreamHandle hStream
Unique handle for the stream.

uint32_t isGraphUpload
Boolean value indicating if the launch callback is part of a graph upload.
This field is only valid if the driver version is 510 or newer.

CUstream stream
The stream where the graph is launched.