# 7.31. CUpti_ActivityGraphTrace


struct CUpti_ActivityGraphTrace
The activity record for trace of graph execution.
This activity record represents execution for a graph without giving visibility about the execution of its nodes. This is intended to reduce overheads in tracing each node. The activity kind is CUPTI_ACTIVITY_KIND_GRAPH_TRACE Graph trace activity is now reported using CUpti_ActivityGraphTrace2 record.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_GRAPH_TRACE.

uint32_t correlationId
The correlation ID of the graph launch.
Each graph launch is assigned a unique correlation ID that is identical to the correlation ID in the driver API activity record that launched the graph.

uint64_t start
The start timestamp for the graph execution, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the graph.

uint64_t end
The end timestamp for the graph execution, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the graph.

uint32_t deviceId
The ID of the device where the graph execution is occurring.

uint32_t graphId
The unique ID of the graph that is launched.

uint32_t contextId
The ID of the context where the graph is being launched.

uint32_t streamId
The ID of the stream where the graph is being launched.

void *reserved
This field is reserved for internal use.