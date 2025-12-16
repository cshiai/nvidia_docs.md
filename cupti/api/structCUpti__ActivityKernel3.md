# 7.46. CUpti_ActivityKernel3


struct CUpti_ActivityKernel3
The activity record for a kernel (CUDA 6.5(with sm_52 support) onwards).
(deprecated in CUDA 9.0)
This activity record represents a kernel execution (CUPTI_ACTIVITY_KIND_KERNEL and CUPTI_ACTIVITY_KIND_CONCURRENT_KERNEL). Kernel activities are now reported using the CUpti_ActivityKernel9 activity record.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_KERNEL or CUPTI_ACTIVITY_KIND_CONCURRENT_KERNEL.

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

CUpti_ActivityPartitionedGlobalCacheConfig partitionedGlobalCacheRequested
The partitioned global caching requested for the kernel.
Partitioned global caching is required to enable caching on certain chips, such as devices with compute capability 5.2.

CUpti_ActivityPartitionedGlobalCacheConfig partitionedGlobalCacheExecuted
The partitioned global caching executed for the kernel.
Partitioned global caching is required to enable caching on certain chips, such as devices with compute capability 5.2. Partitioned global caching can be automatically disabled if the occupancy requirement of the launch cannot support caching.

uint64_t start
The start timestamp for the kernel execution, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the kernel.

uint64_t end
The end timestamp for the kernel execution, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the kernel.

uint64_t completed
The completed timestamp for the kernel execution, in ns.
It represents the completion of all it’s child kernels and the kernel itself. A value of CUPTI_TIMESTAMP_UNKNOWN indicates that the completion time is unknown.

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
Each kernel execution is assigned a unique correlation ID that is identical to the correlation ID in the driver or runtime API activity record that launched the kernel.

int64_t gridId
The grid ID of the kernel.
Each kernel is assigned a unique grid ID at runtime.

const char *name
The name of the kernel.
This name is shared across all activity records representing the same kernel, and so should not be modified.

void *reserved0
Undefined.
Reserved for internal use.