# 7.109. CUpti_ActivityUnifiedMemoryCounter2


struct CUpti_ActivityUnifiedMemoryCounter2
The activity record for Unified Memory counters (deprecated in 12.8)
This activity record represents a Unified Memory counter (CUPTI_ACTIVITY_KIND_UNIFIED_MEMORY_COUNTER).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_UNIFIED_MEMORY_COUNTER.

CUpti_ActivityUnifiedMemoryCounterKind counterKind
The Unified Memory counter kind.

uint64_t value
Value of the counter For counterKind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_HTOD, CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_DTOH, CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THREASHING and CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_REMOTE_MAP, it is the size of the memory region in bytes.
For counterKind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_GPU_PAGE_FAULT, it is the number of page fault groups for the same page. For counterKind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_CPU_PAGE_FAULT_COUNT, it is the program counter for the instruction that caused fault.

uint64_t start
The start timestamp of the counter, in ns.
For counterKind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_HTOD and CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_DTOH, timestamp is captured when activity starts on GPU. For counterKind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_GPU_PAGE_FAULT and CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_CPU_PAGE_FAULT_COUNT, timestamp is captured when CUDA driver started processing the fault. For counterKind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THRASHING, timestamp is captured when CUDA driver detected thrashing of memory region. For counterKind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THROTTLING, timestamp is captured when throttling operation was started by CUDA driver. For counterKind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_REMOTE_MAP, timestamp is captured when CUDA driver has pushed all required operations to the processor specified by dstId.

uint64_t end
The end timestamp of the counter, in ns.
Ignore this field if counterKind is CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_CPU_PAGE_FAULT_COUNT or CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THRASHING or CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_REMOTE_MAP. For counterKind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_HTOD and CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_DTOH, timestamp is captured when activity finishes on GPU. For counterKind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_GPU_PAGE_FAULT, timestamp is captured when CUDA driver queues the replay of faulting memory accesses on the GPU For counterKind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THROTTLING, timestamp is captured when throttling operation was finished by CUDA driver

uint64_t address
This is the virtual base address of the page/s being transferred.
For cpu and gpu faults, the virtual address for the page that faulted.

uint32_t srcId
The ID of the source CPU/device involved in the memory transfer, page fault, thrashing, throttling or remote map operation.
For counterKind CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THRASHING, it is a bitwise ORing of the device IDs fighting for the memory region. Ignore this field if counterKind is CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_CPU_PAGE_FAULT_COUNT

uint32_t dstId
The ID of the destination CPU/device involved in the memory transfer or remote map operation.
Ignore this field if counterKind is CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_GPU_PAGE_FAULT or CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_CPU_PAGE_FAULT_COUNT or CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THRASHING or CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THROTTLING

uint32_t streamId
The ID of the stream causing the transfer.
This value of this field is invalid.

uint32_t processId
The ID of the process to which this record belongs to.

uint32_t flags
The flags associated with this record.
See enums CUpti_ActivityUnifiedMemoryAccessType if counterKind is CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_GPU_PAGE_FAULT and CUpti_ActivityUnifiedMemoryMigrationCause if counterKind is CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_HTOD or CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_BYTES_TRANSFER_HTOD and CUpti_ActivityUnifiedMemoryRemoteMapCause if counterKind is CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_REMOTE_MAP and CUpti_ActivityFlag if counterKind is CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THRASHING or CUPTI_ACTIVITY_UNIFIED_MEMORY_COUNTER_KIND_THROTTLING

uint32_t pad
Undefined.
Reserved for internal use.