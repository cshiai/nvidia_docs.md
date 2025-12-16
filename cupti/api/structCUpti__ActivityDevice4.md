# 7.18. CUpti_ActivityDevice4


struct CUpti_ActivityDevice4
The activity record for a device.
(CUDA 11.6 onwards)
This activity record represents information about a GPU device (CUPTI_ACTIVITY_KIND_DEVICE). Device activity is now reported using the CUpti_ActivityDevice5 activity record.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_DEVICE.

CUpti_ActivityFlag flags
The flags associated with the device.

See also
CUpti_ActivityFlag

uint64_t globalMemoryBandwidth
The global memory bandwidth available on the device, in kBytes/sec.

uint64_t globalMemorySize
The amount of global memory on the device, in bytes.

uint32_t constantMemorySize
The amount of constant memory on the device, in bytes.

uint32_t l2CacheSize
The size of the L2 cache on the device, in bytes.

uint32_t numThreadsPerWarp
The number of threads per warp on the device.

uint32_t coreClockRate
The core clock rate of the device, in kHz.

uint32_t numMemcpyEngines
Number of memory copy engines on the device.

uint32_t numMultiprocessors
Number of multiprocessors on the device.

uint32_t maxIPC
The maximum “instructions per cycle” possible on each device multiprocessor.

uint32_t maxWarpsPerMultiprocessor
Maximum number of warps that can be present on a multiprocessor at any given time.

uint32_t maxBlocksPerMultiprocessor
Maximum number of blocks that can be present on a multiprocessor at any given time.

uint32_t maxSharedMemoryPerMultiprocessor
Maximum amount of shared memory available per multiprocessor, in bytes.

uint32_t maxRegistersPerMultiprocessor
Maximum number of 32-bit registers available per multiprocessor.

uint32_t maxRegistersPerBlock
Maximum number of registers that can be allocated to a block.

uint32_t maxSharedMemoryPerBlock
Maximum amount of shared memory that can be assigned to a block, in bytes.

uint32_t maxThreadsPerBlock
Maximum number of threads allowed in a block.

uint32_t maxBlockDimX
Maximum allowed X dimension for a block.

uint32_t maxBlockDimY
Maximum allowed Y dimension for a block.

uint32_t maxBlockDimZ
Maximum allowed Z dimension for a block.

uint32_t maxGridDimX
Maximum allowed X dimension for a grid.

uint32_t maxGridDimY
Maximum allowed Y dimension for a grid.

uint32_t maxGridDimZ
Maximum allowed Z dimension for a grid.

uint32_t computeCapabilityMajor
Compute capability for the device, major number.

uint32_t computeCapabilityMinor
Compute capability for the device, minor number.

uint32_t id
The device ID.

uint32_t eccEnabled
ECC enabled flag for device.

CUuuid uuid
The device UUID.
This value is the globally unique immutable alphanumeric identifier of the device.

const char *name
The device name.
This name is shared across all activity records representing instances of the device, and so should not be modified.

uint8_t isCudaVisible
Flag to indicate whether the device is visible to CUDA.
Users can set the device visibility using CUDA_VISIBLE_DEVICES environment

uint8_t isMigEnabled
MIG enabled flag for device.

uint32_t gpuInstanceId
GPU Instance id for MIG enabled devices.
If mig mode is disabled value is set to UINT32_MAX

uint32_t computeInstanceId
Compute Instance id for MIG enabled devices.
If mig mode is disabled value is set to UINT32_MAX

CUuuid migUuid
The MIG UUID.
This value is the globally unique immutable alphanumeric identifier of the device.