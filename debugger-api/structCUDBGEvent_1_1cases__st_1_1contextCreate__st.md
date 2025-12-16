# Debugger API

[< Previous](unionCUDBGEvent_1_1cases__st.html) | [Next >](structCUDBGEvent_1_1cases__st_1_1contextDestroy__st.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 4.5. CUDBGEvent::cases_st::contextCreate_st Struct Reference




### Public Variables


uint64_t  context
the context being created.

uint32_t  dev
device index of the context.

uint32_t  tid
host thread id (or LWP id) of the thread hosting the context (Linux only).


### Variables


uint64_t  CUDBGEvent::​cases_st::​contextCreate_st::context [inherited]
the context being created.

uint32_t  CUDBGEvent::​cases_st::​contextCreate_st::dev [inherited]
device index of the context.

uint32_t  CUDBGEvent::​cases_st::​contextCreate_st::tid [inherited]
host thread id (or LWP id) of the thread hosting the context (Linux only).


---