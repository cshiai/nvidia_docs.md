# 7.150. CUpti_Profiler_DeviceSupported_Params


struct CUpti_Profiler_DeviceSupported_Params
Params for cuptiProfilerDeviceSupported.

Public Members

size_t structSize
[in] Must be CUpti_Profiler_DeviceSupported_Params_STRUCT_SIZE

void *pPriv
[in] assign to NULL

CUdevice cuDevice
[in] if NULL, the current CUcontext is used

CUpti_Profiler_Support_Level isSupported
[out] overall SUPPORTED / UNSUPPORTED flag representing whether Profiling and PC Sampling APIs work on the given device and configuration. SUPPORTED if all following flags are SUPPORTED, UNSUPPORTED otherwise.

CUpti_Profiler_Support_Level architecture
[out] SUPPORTED if the device architecture level supports the Profiling API (Compute Capability >= 7.0), UNSUPPORTED otherwise

CUpti_Profiler_Support_Level sli
[out] SUPPORTED if SLI is not enabled, UNSUPPORTED otherwise

CUpti_Profiler_Support_Level vGpu
[out] SUPPORTED if vGPU is supported and profiling is enabled, DISABLED if profiling is supported but not enabled, UNSUPPORTED otherwise

CUpti_Profiler_Support_Level confidentialCompute
[out] SUPPORTED if confidential compute is not enabled, UNSUPPORTED otherwise

CUpti_Profiler_Support_Level cmp
[out] SUPPORTED if not NVIDIA Crypto Mining Processors (CMP), UNSUPPORTED otherwise

CUpti_Profiler_Support_Level wsl
[out] SUPPORTED if WSL supported, UNSUPPORTED otherwise

CUpti_Profiler_API api
[in] the CUPTI API type for which device support will be checked

CUpti_Profiler_Support_Level sku
[out] SUPPORTED if SKU supported, UNSUPPORTED otherwise