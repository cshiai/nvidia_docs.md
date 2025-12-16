# 7.108. CUpti_ActivityUnifiedMemoryCounter


struct CUpti_ActivityUnifiedMemoryCounter
The activity record for Unified Memory counters (deprecated in CUDA 7.0)
This activity record represents a Unified Memory counter (CUPTI_ACTIVITY_KIND_UNIFIED_MEMORY_COUNTER).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_UNIFIED_MEMORY_COUNTER.

CUpti_ActivityUnifiedMemoryCounterKind counterKind
The Unified Memory counter kind.
See CUpti_ActivityUnifiedMemoryCounterKind

CUpti_ActivityUnifiedMemoryCounterScope scope
Scope of the Unified Memory counter.
See CUpti_ActivityUnifiedMemoryCounterScope

uint32_t deviceId
The ID of the device involved in the memory transfer operation.
It is not relevant if the scope of the counter is global (all devices).

uint64_t value
Value of the counter.

uint64_t timestamp
The timestamp when this sample was retrieved, in ns.
A value of 0 indicates that timestamp information could not be collected

uint32_t processId
The ID of the process to which this record belongs to.
In case of global scope, processId is undefined.

uint32_t pad
Undefined.
Reserved for internal use.