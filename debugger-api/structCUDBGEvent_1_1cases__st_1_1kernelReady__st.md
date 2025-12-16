# Debugger API

[< Previous](structCUDBGEvent_1_1cases__st_1_1kernelFinished__st.html) | [Next >](structCUDBGEventCallbackData.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 4.12. CUDBGEvent::cases_st::kernelReady_st Struct Reference




### Public Variables


CuDim3  blockDim
block dimensions of the kernel.

uint64_t  context
context of the kernel.

uint32_t  dev
device index of the kernel.

uint64_t  function
function of the kernel.

uint64_t  functionEntry
entry PC of the kernel.

CuDim3  gridDim
grid dimensions of the kernel.

uint64_t  gridId
grid index of the kernel.

uint64_t  module
module of the kernel.

uint64_t  parentGridId
64-bit grid index of the parent grid.

uint32_t  tid
host thread id (or LWP id) of the thread hosting the kernel (Linux only).

CUDBGKernelType  type
the type of the kernel: system or application.


### Variables


CuDim3  CUDBGEvent::​cases_st::​kernelReady_st::blockDim [inherited]
block dimensions of the kernel.

uint64_t  CUDBGEvent::​cases_st::​kernelReady_st::context [inherited]
context of the kernel.

uint32_t  CUDBGEvent::​cases_st::​kernelReady_st::dev [inherited]
device index of the kernel.

uint64_t  CUDBGEvent::​cases_st::​kernelReady_st::function [inherited]
function of the kernel.

uint64_t  CUDBGEvent::​cases_st::​kernelReady_st::functionEntry [inherited]
entry PC of the kernel.

CuDim3  CUDBGEvent::​cases_st::​kernelReady_st::gridDim [inherited]
grid dimensions of the kernel.

uint64_t  CUDBGEvent::​cases_st::​kernelReady_st::gridId [inherited]
grid index of the kernel.

uint64_t  CUDBGEvent::​cases_st::​kernelReady_st::module [inherited]
module of the kernel.

uint64_t  CUDBGEvent::​cases_st::​kernelReady_st::parentGridId [inherited]
64-bit grid index of the parent grid.

uint32_t  CUDBGEvent::​cases_st::​kernelReady_st::tid [inherited]
host thread id (or LWP id) of the thread hosting the kernel (Linux only).

CUDBGKernelType  CUDBGEvent::​cases_st::​kernelReady_st::type [inherited]
the type of the kernel: system or application.


---