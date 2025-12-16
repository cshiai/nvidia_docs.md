# 7.21. CUpti_ActivityDeviceGraphTrace


struct CUpti_ActivityDeviceGraphTrace
The activity record for trace of device graph execution.
This activity record represents execution for a device launched graph without giving visibility about the execution of its nodes. This is intended to reduce overheads in tracing each node. The activity kind is CUPTI_ACTIVITY_KIND_DEVICE_GRAPH_TRACE

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_DEVICE_GRAPH_TRACE.

uint32_t deviceId
The ID of the device where the first node of the graph is executed.

uint64_t start
The start timestamp for the graph execution, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the graph.

uint64_t end
The end timestamp for the graph execution, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the graph.

uint32_t graphId
The unique ID of the graph that is launched.

uint32_t launcherGraphId
The unique ID of the graph that has launched this graph.

uint32_t deviceLaunchMode
The type of launch.
See CUpti_DeviceGraphLaunchMode

uint32_t contextId
The ID of the context where the first node of the graph is executed.

uint64_t streamId
The ID of the stream where the graph is being launched.

void *reserved
This field is reserved for internal use.