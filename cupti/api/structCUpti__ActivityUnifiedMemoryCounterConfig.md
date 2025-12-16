# 7.111. CUpti_ActivityUnifiedMemoryCounterConfig


struct CUpti_ActivityUnifiedMemoryCounterConfig
Unified Memory counters configuration structure.
This structure controls the enable/disable of the various Unified Memory counters consisting of scope, kind and other parameters. See function cuptiActivityConfigureUnifiedMemoryCounter

Public Members

CUpti_ActivityUnifiedMemoryCounterScope scope
Unified Memory counter Counter scope.
(deprecated in CUDA 7.0)

CUpti_ActivityUnifiedMemoryCounterKind kind
Unified Memory counter Counter kind.

uint32_t deviceId
Device id of the target device.
This is relevant only for single device scopes. (deprecated in CUDA 7.0)

uint32_t enable
Control to enable/disable the counter.
To enable the counter set it to non-zero value while disable is indicated by zero.