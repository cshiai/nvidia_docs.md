# Sanitizer_GraphExecData


struct Sanitizer_GraphExecData
Data passed into a graphexec creation callback function.
Data passed into a graphs callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_GRAPHS and cbid equal to SANITIZER_CBID_GRAPHS_GRAPHEXEC_CREATING. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

uint32_t containsDeviceGraphLaunches
Boolean value indicating if the graphexec may launch device graphs.
Only valid in the SANITIZER_CBID_GRAPHS_GRAPHEXEC_CREATED callback with driver version of 535 or newer.

CUcontext deviceGraphLaunchesContext
Context where the graphexec can launch device graphs.
NULL if the graphExec doesn’t launch device graphs. Only valid in the SANITIZER_CBID_GRAPHS_GRAPHEXEC_CREATED callback with driver version of 535 or newer.

CUgraph graph
CUDA graph being instantiated.

CUgraphExec graphExec
Instance of the CUDA graph.
Can be NULL for device graph launches in the SANITIZER_CBID_GRAPHS_GRAPHEXEC_CREATING callback.

uint32_t isDeviceLaunch
Boolean value indicating if the graphexec is for a device graph launch.