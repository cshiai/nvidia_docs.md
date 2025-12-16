# 7.6. CUpti_ActivityCdpKernel


struct CUpti_ActivityCdpKernel
The activity record for CDP (CUDA Dynamic Parallelism) kernel.
This activity record represents a CDP kernel execution.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_CDP_KERNEL.

uint8_t requested
The cache configuration requested by the kernel.
The value is one of the CUfunc_cache enumeration values from cuda.h.

uint8_t executed
The cache configuration used for the kernel.
The value is one of the CUfunc_cache enumeration values from cuda.h.

uint8_t sharedMemoryConfig
The shared memory configuration used for the kernel.
The value is one of the CUsharedconfig enumeration values from cuda.h.

uint16_t registersPerThread
The number of registers required for each thread executing the kernel.

uint64_t start
The start timestamp for the kernel execution, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the kernel.

uint64_t end
The end timestamp for the kernel execution, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the kernel.

uint32_t deviceId
The ID of the device where the kernel is executing.

uint32_t contextId
The ID of the context where the kernel is executing.

uint32_t streamId
The ID of the stream where the kernel is executing.

int32_t gridX
The X-dimension grid size for the kernel.

int32_t gridY
The Y-dimension grid size for the kernel.

int32_t gridZ
The Z-dimension grid size for the kernel.

int32_t blockX
The X-dimension block size for the kernel.

int32_t blockY
The Y-dimension block size for the kernel.

int32_t blockZ
The Z-dimension grid size for the kernel.

int32_t staticSharedMemory
The static shared memory allocated for the kernel, in bytes.

int32_t dynamicSharedMemory
The dynamic shared memory reserved for the kernel, in bytes.

uint32_t localMemoryPerThread
The amount of local memory reserved for each thread, in bytes.

uint32_t localMemoryTotal
The total amount of local memory reserved for the kernel, in bytes.

uint32_t correlationId
The correlation ID of the kernel.
Each kernel execution is assigned a unique correlation ID that is identical to the correlation ID in the driver API activity record that launched the kernel.

int64_t gridId
The grid ID of the kernel.
Each kernel execution is assigned a unique grid ID.

int64_t parentGridId
The grid ID of the parent kernel.

uint64_t queued
The timestamp when kernel is queued up, in ns.
A value of CUPTI_TIMESTAMP_UNKNOWN indicates that the queued time is unknown.

uint64_t submitted
The timestamp when kernel is submitted to the gpu, in ns.
A value of CUPTI_TIMESTAMP_UNKNOWN indicates that the submission time is unknown.

uint64_t completed
The timestamp when kernel is marked as completed, in ns.
A value of CUPTI_TIMESTAMP_UNKNOWN indicates that the completion time is unknown.

uint32_t parentBlockX
The X-dimension of the parent block.

uint32_t parentBlockY
The Y-dimension of the parent block.

uint32_t parentBlockZ
The Z-dimension of the parent block.

uint32_t pad
Undefined.
Reserved for internal use.

const char *name
The name of the kernel.
This name is shared across all activity records representing the same kernel, and so should not be modified.