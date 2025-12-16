# Debugger API

[< Previous](structCUDBGEventCallbackData40.html) | [Next >](functions.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 4.15. CUDBGGridInfo Struct Reference


## [[Grid Properties](group__GRID.html)]




### Public Variables


CuDim3  blockDim
The block dimensions.

uint64_t  context
The context this grid belongs to.

uint32_t  dev
The index of the device this grid is running on.

uint64_t  function
The function corresponding to this grid.

uint64_t  functionEntry
The entry address of the function corresponding to this grid.

CuDim3  gridDim
The grid dimensions.

uint64_t  gridId64
The 64-bit grid ID of this grid.

uint64_t  module
The module this grid belongs to.

CUDBGKernelOrigin  origin
The origin of this grid, CPU or GPU.

uint64_t  parentGridId
The 64-bit grid ID that launched this grid.

uint32_t  tid
The host thread ID that launched this grid.

CUDBGKernelType  type
The type of the grid.


### Variables


CuDim3  CUDBGGridInfo::blockDim [inherited]
The block dimensions.

uint64_t  CUDBGGridInfo::context [inherited]
The context this grid belongs to.

uint32_t  CUDBGGridInfo::dev [inherited]
The index of the device this grid is running on.

uint64_t  CUDBGGridInfo::function [inherited]
The function corresponding to this grid.

uint64_t  CUDBGGridInfo::functionEntry [inherited]
The entry address of the function corresponding to this grid.

CuDim3  CUDBGGridInfo::gridDim [inherited]
The grid dimensions.

uint64_t  CUDBGGridInfo::gridId64 [inherited]
The 64-bit grid ID of this grid.

uint64_t  CUDBGGridInfo::module [inherited]
The module this grid belongs to.

CUDBGKernelOrigin  CUDBGGridInfo::origin [inherited]
The origin of this grid, CPU or GPU.

uint64_t  CUDBGGridInfo::parentGridId [inherited]
The 64-bit grid ID that launched this grid.

uint32_t  CUDBGGridInfo::tid [inherited]
The host thread ID that launched this grid.

CUDBGKernelType  CUDBGGridInfo::type [inherited]
The type of the grid.


---