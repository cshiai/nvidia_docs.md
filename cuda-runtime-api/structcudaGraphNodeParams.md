# CUDA Runtime API

[< Previous](structcudaGraphKernelNodeUpdate.html) | [Next >](structcudaHostNodeParams.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.35. cudaGraphNodeParams Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Graph node parameters. See [cudaGraphAddNode](group__CUDART__GRAPH.html#group__CUDART__GRAPH_1gcc58bff104c12fb02a048bf2bb6a1e6f).


### Public Variables


struct cudaMemAllocNodeParamsV2 allocstruct cudaConditionalNodeParams conditionalstruct cudaEventRecordNodeParams eventRecordstruct cudaEventWaitNodeParams eventWaitstruct cudaExternalSemaphoreSignalNodeParamsV2 extSemSignalstruct cudaExternalSemaphoreWaitNodeParamsV2 extSemWaitstruct cudaMemFreeNodeParams freestruct cudaChildGraphNodeParams graphstruct cudaHostNodeParamsV2 hoststruct cudaKernelNodeParamsV2 kernelstruct cudaMemcpyNodeParams memcpystruct cudaMemsetParamsV2 memsetint  reserved0[3]long long  reserved1[29]long long  reserved2enumcudaGraphNodeType type

### Variables


struct cudaMemAllocNodeParamsV2cudaGraphNodeParams::alloc [inherited]
Memory allocation node parameters.

struct cudaConditionalNodeParamscudaGraphNodeParams::conditional [inherited]
Conditional node parameters.

struct cudaEventRecordNodeParamscudaGraphNodeParams::eventRecord [inherited]
Event record node parameters.

struct cudaEventWaitNodeParamscudaGraphNodeParams::eventWait [inherited]
Event wait node parameters.

struct cudaExternalSemaphoreSignalNodeParamsV2cudaGraphNodeParams::extSemSignal [inherited]
External semaphore signal node parameters.

struct cudaExternalSemaphoreWaitNodeParamsV2cudaGraphNodeParams::extSemWait [inherited]
External semaphore wait node parameters.

struct cudaMemFreeNodeParamscudaGraphNodeParams::free [inherited]
Memory free node parameters.

struct cudaChildGraphNodeParamscudaGraphNodeParams::graph [inherited]
Child graph node parameters.

struct cudaHostNodeParamsV2cudaGraphNodeParams::host [inherited]
Host node parameters.

struct cudaKernelNodeParamsV2cudaGraphNodeParams::kernel [inherited]
Kernel node parameters.

struct cudaMemcpyNodeParamscudaGraphNodeParams::memcpy [inherited]
Memcpy node parameters.

struct cudaMemsetParamsV2cudaGraphNodeParams::memset [inherited]
Memset node parameters.

int  cudaGraphNodeParams::reserved0[3] [inherited]
Reserved. Must be zero.

long long  cudaGraphNodeParams::reserved1[29] [inherited]
Padding. Unused bytes must be zero.

long long  cudaGraphNodeParams::reserved2 [inherited]
Reserved bytes. Must be zero.

enumcudaGraphNodeTypecudaGraphNodeParams::type [inherited]
Type of the node


---