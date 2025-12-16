# CUDA Driver API

[< Previous](structCUgraphExecUpdateResultInfo__v1.html) | [Next >](structCUipcEventHandle__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.63. CUgraphNodeParams Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Graph node parameters. See [cuGraphAddNode](group__CUDA__GRAPH.html#group__CUDA__GRAPH_1ge01208e62f72a53367a2af903bf17d23).


### Public Variables


struct CUDA_MEM_ALLOC_NODE_PARAMS_v2 allocstruct CUDA_CONDITIONAL_NODE_PARAMS conditionalstruct CUDA_EVENT_RECORD_NODE_PARAMS eventRecordstruct CUDA_EVENT_WAIT_NODE_PARAMS eventWaitstruct CUDA_EXT_SEM_SIGNAL_NODE_PARAMS_v2 extSemSignalstruct CUDA_EXT_SEM_WAIT_NODE_PARAMS_v2 extSemWaitstruct CUDA_MEM_FREE_NODE_PARAMS freestruct CUDA_CHILD_GRAPH_NODE_PARAMS graphstruct CUDA_HOST_NODE_PARAMS_v2 hoststruct CUDA_KERNEL_NODE_PARAMS_v3 kernelstruct CUDA_BATCH_MEM_OP_NODE_PARAMS_v2 memOpstruct CUDA_MEMCPY_NODE_PARAMS memcpystruct CUDA_MEMSET_NODE_PARAMS_v2 memsetint  reserved0[3]long long  reserved1[29]long long  reserved2CUgraphNodeType type

### Variables


struct CUDA_MEM_ALLOC_NODE_PARAMS_v2CUgraphNodeParams::alloc [inherited]
Memory allocation node parameters.

struct CUDA_CONDITIONAL_NODE_PARAMSCUgraphNodeParams::conditional [inherited]
Conditional node parameters.

struct CUDA_EVENT_RECORD_NODE_PARAMSCUgraphNodeParams::eventRecord [inherited]
Event record node parameters.

struct CUDA_EVENT_WAIT_NODE_PARAMSCUgraphNodeParams::eventWait [inherited]
Event wait node parameters.

struct CUDA_EXT_SEM_SIGNAL_NODE_PARAMS_v2CUgraphNodeParams::extSemSignal [inherited]
External semaphore signal node parameters.

struct CUDA_EXT_SEM_WAIT_NODE_PARAMS_v2CUgraphNodeParams::extSemWait [inherited]
External semaphore wait node parameters.

struct CUDA_MEM_FREE_NODE_PARAMSCUgraphNodeParams::free [inherited]
Memory free node parameters.

struct CUDA_CHILD_GRAPH_NODE_PARAMSCUgraphNodeParams::graph [inherited]
Child graph node parameters.

struct CUDA_HOST_NODE_PARAMS_v2CUgraphNodeParams::host [inherited]
Host node parameters.

struct CUDA_KERNEL_NODE_PARAMS_v3CUgraphNodeParams::kernel [inherited]
Kernel node parameters.

struct CUDA_BATCH_MEM_OP_NODE_PARAMS_v2CUgraphNodeParams::memOp [inherited]
MemOp node parameters.

struct CUDA_MEMCPY_NODE_PARAMSCUgraphNodeParams::memcpy [inherited]
Memcpy node parameters.

struct CUDA_MEMSET_NODE_PARAMS_v2CUgraphNodeParams::memset [inherited]
Memset node parameters.

int  CUgraphNodeParams::reserved0[3] [inherited]
Reserved. Must be zero.

long long  CUgraphNodeParams::reserved1[29] [inherited]
Padding. Unused bytes must be zero.

long long  CUgraphNodeParams::reserved2 [inherited]
Reserved bytes. Must be zero.

CUgraphNodeTypeCUgraphNodeParams::type [inherited]
Type of the node


---