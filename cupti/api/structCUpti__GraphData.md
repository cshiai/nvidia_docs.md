# 7.115. CUpti_GraphData


struct CUpti_GraphData
CUDA graphs data passed into a resource callback function.
CUDA graphs data passed into a resource callback function as the cbdata argument to CUpti_CallbackFunc. The cbdata will be this type for domain equal to CUPTI_CB_DOMAIN_RESOURCE. The graph data is valid only within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of that data.

Public Members

CUgraph graph
CUDA graph.

CUgraph originalGraph
The original CUDA graph from which.

Param graph:
is cloned

CUgraphNode node
CUDA graph node.

CUgraphNode originalNode
The original CUDA graph node from which.

Param node:
is cloned

CUgraphNodeType nodeType
Type of the.

Param node:

CUgraphNode dependency
The dependent graph node.

CUgraphExec graphExec
CUDA executable graph.