# CUPTI


The API reference for CUPTI, the CUDA Profiling Tools Interface. The CUPTI API


## Overview


The *CUDA Profiling Tools Interface* (CUPTI) provides a C-based interface for creating profiling and tracing tools designed for CUDA applications. CUPTI provides the following APIs: the *Activity API*, the *Callback API*, the *Host Profiling API*, the *Range Profiling API*, the *PC Sampling API*, the *SASS Metric API*, the *PM Sampling API*, the *Checkpoint API* and the *Profiling API*. Using these APIs, you can develop profiling tools that offer insights into the CPU and GPU behavior of CUDA applications. The CUPTI installation includes several [samples](main/main.html#samples) that demonstrate the use of these APIs. For a step-by-step guide on API usage, refer to the [tutorial](tutorial/tutorial.html) section. CUPTI is delivered as a dynamic library on all platforms supported by CUDA. On Linux (x86_64) and ARM Server (arm64 SBSA), a static library is also provided.


In this CUPTI document, Tracing refers to the collection of timestamps and additional information for CUDA activities such as CUDA APIs, kernel launches and memory copies during the execution of a CUDA application. Tracing helps in identifying performance issues for the CUDA code by telling you which parts of a program require the most time. Tracing information can be collected using the *Activity* and *Callback* APIs.


In this CUPTI document, Profiling refers to the collection of GPU performance metrics for individual kernels or a set of kernels in isolation. This process may involve multiple replays of the kernels or the entire application to gather comprehensive GPU performance data. These metrics can be collected using CUPTI *Range* and *Host* Profiling APIs. Refer to the section [Evolution of the profiling APIs](main/main.html#evolution-of-the-profiling-apis) for more details. The *SASS Metric* API collects kernel performance metrics at the source level. The *PM Sampling* API collects metrics by sampling the GPU’s performance monitors (PM) periodically at fixed intervals. And periodic sampling of the warp program counter and warp scheduler state is captured using the *PC Sampling* API.


| CUPTI API | Feature Description | Header |
| --- | --- | --- |
| Activity | Asynchronously record CUDA activities, e.g. CUDA API, Kernel, memory copy | cupti_activity.h |
| Callback | CUDA event callback mechanism to notify subscriber that a specific CUDA event executed
e.g. “Entering CUDA runtime memory copy” | cupti_callbacks.h |
| Host Profiling | Host APIs for enumeration, configuration and evaluation of performance metrics | cupti_profiler_host.h |
| Range Profiling | Target APIs for collection of performance metrics for a range of execution | cupti_range_profiler.h |
| PC Sampling | Sampling of the warp program counter and warp scheduler state (stall reasons) | cupti_pcsampling.h |
| SASS Metrics | Collect kernel performance metrics at the source level using SASS patching | cupti_sass_metrics.h |
| PM Sampling | Collect hardware metrics by sampling the GPU performance monitors (PM) periodically at fixed intervals | cupti_pmsampling.h |
| Profiling | Target APIs for collection of performance metrics for a range of execution.
Host operations - enumeration, configuration and evaluation of metrics are supported by the Perfworks Metrics API.
The Profiling API is deprecated in the CUDA 13.0 release, it is recommended to use the Range Profiling API. | cupti_profiler_target.h
nvperf_host.h |
| Checkpoint | Provides support for automatically saving and restoring the functional state of the CUDA device | cupti_checkpoint.h |


CUPTI Python


CUPTI Python is a library that provides Python APIs for creating profiling and tracing tools specifically designed for CUDA Python applications. The current release supports a subset of CUPTI C Activity and Callback APIs. It’s important to note that this library is available only for Linux (x86_64) and Linux (aarch64 sbsa) platforms. For developers interested in utilizing CUPTI Python, it’s recommended to refer to the official documentation at [https://pypi.org/project/cupti-python/](https://pypi.org/project/cupti-python/) for more detailed information on its capabilities and usage instructions.


CUPTI Profiling API vs. NVIDIA Nsight Perf SDK


[CUPTI Profiling API](main/main.html#cupti-profiling-api) and [CUPTI Range Profiling API](main/main.html#range-profiling-api) support profiling of CUDA kernels and these allow collection of GPU performance metrics for a particular kernel or range of kernels at the CUDA context level. [NVIDIA Nsight Perf SDK](https://developer.nvidia.com/nsight-perf-sdk) supports graphics APIs (i.e. DirectX, Vulkan, OpenGL) allowing collection of GPU performance metrics at graphics device, context and queue levels. Both NVIDIA Nsight PerfSDK and CUPTI Profiling API share the host APIs (i.e. metrics enumeration, configuration and evaluation) but differ in which GPU APIs they target on the device.


CUPTI Installation


The CUPTI SDK is part of the CUDA Toolkit, and will be installed along all the other CUDA libraries.


The default installation locations for the CUPTI library are:


 - Linux: /usr/local/cuda-<version>/extras/CUPTI/
 - Windows: C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA<version>\extras\CUPTI


Note that these libraries are not added to the PATH or LD_LIBRARY_PATH on Windows and Linux platforms, respectively. To dynamically link to CUPTI, add the appropriate path to the PATH (on Windows) or LD_LIBRARY_PATH (on Linux) environment variables.