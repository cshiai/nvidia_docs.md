# Debugger API

[< Previous](structCUDBGAPI__st.html) | [Next >](structCUDBGEvent.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 4.2. CUDBGCudaLogMessage Struct Reference


## [[General](group__GENERAL.html#group__GENERAL)]




### Public Variables


CUDBGCudaLogLevel logLevel
The log severity level of the message.

char  message[CUDBG_MAX_LOG_LEN]
The log message string.

uint32_t  osThreadId
The OS thread ID of the thread that generated the log message.

uint64_t  unixTimestampNs
The timestamp the log message was received at, in nanoseconds since the Unix epoch.


### Variables


CUDBGCudaLogLevelCUDBGCudaLogMessage::logLevel [inherited]
The log severity level of the message.

char  CUDBGCudaLogMessage::message[CUDBG_MAX_LOG_LEN] [inherited]
The log message string.

uint32_t  CUDBGCudaLogMessage::osThreadId [inherited]
The OS thread ID of the thread that generated the log message.

uint64_t  CUDBGCudaLogMessage::unixTimestampNs [inherited]
The timestamp the log message was received at, in nanoseconds since the Unix epoch.


---