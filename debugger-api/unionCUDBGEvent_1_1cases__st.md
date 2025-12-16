# Debugger API

[< Previous](structCUDBGEvent.html) | [Next >](structCUDBGEvent_1_1cases__st_1_1contextCreate__st.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 4.4. CUDBGEvent::cases_st Union Reference




### Public Variables


struct CUDBGEvent::​cases_st::​contextCreate_st contextCreate
Information about the context being created.

struct CUDBGEvent::​cases_st::​contextDestroy_st contextDestroy
Information about the context being destroyed.

struct CUDBGEvent::​cases_st::​contextPop_st contextPop
Information about the context being popped.

struct CUDBGEvent::​cases_st::​contextPush_st contextPush
Information about the context being pushed.

struct CUDBGEvent::​cases_st::​elfImageLoaded_st elfImageLoaded
Information about the loaded ELF image.

struct CUDBGEvent::​cases_st::​internalError_st internalError
Information about internal erros.

struct CUDBGEvent::​cases_st::​kernelFinished_st kernelFinished
Information about the kernel that just terminated.

struct CUDBGEvent::​cases_st::​kernelReady_st kernelReady
Information about the kernel ready to be launched.


### Variables


struct CUDBGEvent::​cases_st::​contextCreate_stCUDBGEvent::​cases_st::contextCreate [inherited]
Information about the context being created.

struct CUDBGEvent::​cases_st::​contextDestroy_stCUDBGEvent::​cases_st::contextDestroy [inherited]
Information about the context being destroyed.

struct CUDBGEvent::​cases_st::​contextPop_stCUDBGEvent::​cases_st::contextPop [inherited]
Information about the context being popped.

struct CUDBGEvent::​cases_st::​contextPush_stCUDBGEvent::​cases_st::contextPush [inherited]
Information about the context being pushed.

struct CUDBGEvent::​cases_st::​elfImageLoaded_stCUDBGEvent::​cases_st::elfImageLoaded [inherited]
Information about the loaded ELF image.

struct CUDBGEvent::​cases_st::​internalError_stCUDBGEvent::​cases_st::internalError [inherited]
Information about internal erros.

struct CUDBGEvent::​cases_st::​kernelFinished_stCUDBGEvent::​cases_st::kernelFinished [inherited]
Information about the kernel that just terminated.

struct CUDBGEvent::​cases_st::​kernelReady_stCUDBGEvent::​cases_st::kernelReady [inherited]
Information about the kernel ready to be launched.


---