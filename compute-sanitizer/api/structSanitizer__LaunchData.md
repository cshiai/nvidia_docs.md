# Sanitizer_LaunchData


struct Sanitizer_LaunchData
Data passed into a launch callback function.
Data passed into a launch callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_LAUNCH. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Unnamed Group

uint32_t gridDim_x
Launch properties of the grid. These values are only valid for SANITIZER_CBID_LAUNCH_BEGIN and graph node launch callbacks

uint32_t gridDim_y

uint32_t gridDim_z

uint32_t blockDim_x

uint32_t blockDim_y

uint32_t blockDim_z

uint32_t clusterDim_x

uint32_t clusterDim_y

uint32_t clusterDim_z

Public Members

CUcontext apiContext
Only valid for graph node launches.
This is the context of the stream used in the graph launch API call.

CUstream apiStream
Only valid for graph node launches.
This is the stream used in the graph launch API call.

CUcontext context
The context where the grid is launched.
For graph node launches, this is the context in which the kernel will run.

CUdevice device
The device where the grid is launched.

CUfunction function
The function of the grid launch.

const char *functionName
The name of the launched function.

uint64_t gridId
Unique identifier of the grid launch.
For graph node launches, this is only unique within the graphexec launch.

Sanitizer_StreamHandle hApiStream
Unique handle for the API stream.

Sanitizer_LaunchHandle hLaunch
Handle of the grid launch.
This is only valid between the launch begin and end callbacks.

Sanitizer_StreamHandle hStream
Unique handle for the stream.

CUmodule module
The module containing the grid code.

CUstream stream
The stream where the grid is launched.