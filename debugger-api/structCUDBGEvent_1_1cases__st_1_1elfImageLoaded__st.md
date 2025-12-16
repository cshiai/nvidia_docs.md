# Debugger API

[< Previous](structCUDBGEvent_1_1cases__st_1_1contextPush__st.html) | [Next >](structCUDBGEvent_1_1cases__st_1_1internalError__st.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 4.9. CUDBGEvent::cases_st::elfImageLoaded_st Struct Reference




### Public Variables


uint64_t  context
context of the kernel.

uint32_t  dev
device index of the kernel.

uint64_t  handle
ELF image handle.

uint64_t  module
module of the kernel.

uint32_t  properties
ELF image properties.

uint64_t  size
size of the ELF image (64-bit).


### Variables


uint64_t  CUDBGEvent::​cases_st::​elfImageLoaded_st::context [inherited]
context of the kernel.

uint32_t  CUDBGEvent::​cases_st::​elfImageLoaded_st::dev [inherited]
device index of the kernel.

uint64_t  CUDBGEvent::​cases_st::​elfImageLoaded_st::handle [inherited]
ELF image handle.

uint64_t  CUDBGEvent::​cases_st::​elfImageLoaded_st::module [inherited]
module of the kernel.

uint32_t  CUDBGEvent::​cases_st::​elfImageLoaded_st::properties [inherited]
ELF image properties.

uint64_t  CUDBGEvent::​cases_st::​elfImageLoaded_st::size [inherited]
size of the ELF image (64-bit).


---