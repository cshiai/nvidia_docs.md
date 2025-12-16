# 7.30. CUpti_ActivityGraphHostNode


struct CUpti_ActivityGraphHostNode
Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_GRAPH_HOST_NODE.

uint32_t streamId
The ID of the stream that waits for the graph host node to finish.

uint32_t contextId
The ID of the CUDA context to which the waiting CUDA stream belongs.

uint32_t deviceId
The ID of the CUDA device to which the CUDA context and stream belong.
The graph host node is executing on the CPU, but it is associated with the CUDA device through the CUDA context and stream.

uint32_t correlationId
The correlation ID of the graph host node operation.
Each operation is assigned a unique correlation ID that is identical to the correlation ID in the driver API activity record that launched the operation.

uint32_t graphId
The unique ID of the graph that executed this host node through graph launch.

uint64_t graphNodeId
The unique ID of the graph node that executed this host node through graph launch.

uint32_t processId
The ID of the process where the host node is executing.

uint32_t threadId
The ID of the thread where the host node is executing.

uint64_t start
The start timestamp.
A value of CUPTI_TIMESTAMP_UNKNOWN indicates that the start time is unknown.

uint64_t end
The end timestamp.
A value of CUPTI_TIMESTAMP_UNKNOWN indicates that the start time is unknown.