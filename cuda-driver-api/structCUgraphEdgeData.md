# CUDA Driver API

[< Previous](structCUextent3D__v1.html) | [Next >](structCUgraphExecUpdateResultInfo__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.61. CUgraphEdgeData Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Optional annotation for edges in a CUDA graph. Note, all edges implicitly have annotations and default to a zero-initialized value if not specified. A zero-initialized struct indicates a standard full serialization of two nodes with memory visibility.


### Public Variables


unsigned char  from_portunsigned char  reserved[5]unsigned char  to_portunsigned char  type

### Variables


unsigned char  CUgraphEdgeData::from_port [inherited]
This indicates when the dependency is triggered from the upstream node on the edge. The meaning is specfic to the node type.
                                 A value of 0 in all cases means full completion of the upstream node, with memory visibility to the downstream node or portion
                                 thereof (indicated by to_port).
                                 Only kernel nodes define non-zero ports. A kernel node can use the following output port types: CU_GRAPH_KERNEL_NODE_PORT_DEFAULT, CU_GRAPH_KERNEL_NODE_PORT_PROGRAMMATIC, or CU_GRAPH_KERNEL_NODE_PORT_LAUNCH_ORDER.

unsigned char  CUgraphEdgeData::reserved[5] [inherited]
These bytes are unused and must be zeroed. This ensures compatibility if additional fields are added in the future.

unsigned char  CUgraphEdgeData::to_port [inherited]
This indicates what portion of the downstream node is dependent on the upstream node or portion thereof (indicated by from_port). The meaning is specific to the node type. A value of 0 in all cases means the entirety of the downstream node is dependent
                                 on the upstream work.
                                 Currently no node types define non-zero ports. Accordingly, this field must be set to zero.

unsigned char  CUgraphEdgeData::type [inherited]
This should be populated with a value from CUgraphDependencyType. (It is typed as char due to compiler-specific layout of bitfields.) See CUgraphDependencyType.


---