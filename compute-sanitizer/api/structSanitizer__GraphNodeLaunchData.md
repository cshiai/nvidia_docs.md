# Sanitizer_GraphNodeLaunchData


struct Sanitizer_GraphNodeLaunchData
Data passed into a graph node launch callback function.
Data passed into a graphs callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_GRAPHS and cbid equal to SANITIZER_CBID_GRAPHS_LAUNCH_NODE_BEGIN or SANITIZER_CBID_GRAPHS_LAUNCH_NODE_END. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

union Sanitizer_GraphNodeLaunchData::[anonymous] [anonymous]
Data for this node launch.

CUgraphExec graphExec
Instance of the CUDA graph being launched.

uint32_t isGraphUpload
Boolean value indicating if the node launch callback is part of a graph upload.

Sanitizer_LaunchData launchData
This is only valid if nodeType is CU_GRAPH_NODE_TYPE_KERNEL.

uint32_t launchId
Launch ID for this CUDA graph instance.

Sanitizer_ResourceMemoryData memAllocData
This is only valid if nodeType is CU_GRAPH_NODE_TYPE_MEM_ALLOC.

Sanitizer_MemcpyData memcpyData
This is only valid if nodeType is CU_GRAPH_NODE_TYPE_MEMCPY.

uint64_t memFreeAddress
The freed device pointer This is only valid if nodeType is CU_GRAPH_NODE_TYPE_MEM_FREE.

Sanitizer_MemsetData memsetData
This is only valid if nodeType is CU_GRAPH_NODE_TYPE_MEMSET.

CUgraphNode node
CUDA graphs node being launched.

CUgraphNodeType nodeType
CUDA graphs node type.