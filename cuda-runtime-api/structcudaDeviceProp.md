# CUDA Runtime API

[< Previous](structcudaConditionalNodeParams.html) | [Next >](structcudaDevResource.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.9. cudaDeviceProp Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA device properties


### Public Variables


int  ECCEnabledint  accessPolicyMaxWindowSizeint  asyncEngineCountint  canMapHostMemoryint  canUseHostPointerForRegisteredMemint  clusterLaunchint  computePreemptionSupportedint  concurrentKernelsint  concurrentManagedAccessint  cooperativeLaunchint  deferredMappingCudaArraySupportedint  deviceNumaConfigint  deviceNumaIdint  directManagedMemAccessFromHostint  globalL1CacheSupportedunsigned int  gpuDirectRDMAFlushWritesOptionsint  gpuDirectRDMASupportedint  gpuDirectRDMAWritesOrderingunsigned int  gpuPciDeviceIDunsigned int  gpuPciSubsystemIDint  hostNativeAtomicSupportedint  hostNumaIdint  hostNumaMultinodeIpcSupportedint  hostRegisterReadOnlySupportedint  hostRegisterSupportedint  integratedint  ipcEventSupportedint  isMultiGpuBoardint  l2CacheSizeint  localL1CacheSupportedchar  luid[8]unsigned int  luidDeviceNodeMaskint  majorint  managedMemoryint  maxBlocksPerMultiProcessorint  maxGridSize[3]int  maxSurface1Dint  maxSurface1DLayered[2]int  maxSurface2D[2]int  maxSurface2DLayered[3]int  maxSurface3D[3]int  maxSurfaceCubemapint  maxSurfaceCubemapLayered[2]int  maxTexture1Dint  maxTexture1DLayered[2]int  maxTexture1DMipmapint  maxTexture2D[2]int  maxTexture2DGather[2]int  maxTexture2DLayered[3]int  maxTexture2DLinear[3]int  maxTexture2DMipmap[2]int  maxTexture3D[3]int  maxTexture3DAlt[3]int  maxTextureCubemapint  maxTextureCubemapLayered[2]int  maxThreadsDim[3]int  maxThreadsPerBlockint  maxThreadsPerMultiProcessorsize_t  memPitchint  memoryBusWidthunsigned int  memoryPoolSupportedHandleTypesint  memoryPoolsSupportedint  minorint  mpsEnabledint  multiGpuBoardGroupIDint  multiProcessorCountchar  name[256]int  pageableMemoryAccessint  pageableMemoryAccessUsesHostPageTablesint  pciBusIDint  pciDeviceIDint  pciDomainIDint  persistingL2CacheMaxSizeint  regsPerBlockint  regsPerMultiprocessorint  reserved[56]size_t  reservedSharedMemPerBlocksize_t  sharedMemPerBlocksize_t  sharedMemPerBlockOptinsize_t  sharedMemPerMultiprocessorint  sparseCudaArraySupportedint  streamPrioritiesSupportedsize_t  surfaceAlignmentint  tccDriversize_t  textureAlignmentsize_t  texturePitchAlignmentint  timelineSemaphoreInteropSupportedsize_t  totalConstMemsize_t  totalGlobalMemint  unifiedAddressingint  unifiedFunctionPointerscudaUUID_t  uuidint  warpSize

### Variables


int  cudaDeviceProp::ECCEnabled [inherited]
Device has ECC support enabled

int  cudaDeviceProp::accessPolicyMaxWindowSize [inherited]
The maximum value of cudaAccessPolicyWindow::num_bytes.

int  cudaDeviceProp::asyncEngineCount [inherited]
Number of asynchronous engines

int  cudaDeviceProp::canMapHostMemory [inherited]
Device can map host memory with cudaHostAlloc/cudaHostGetDevicePointer

int  cudaDeviceProp::canUseHostPointerForRegisteredMem [inherited]
Device can access host registered memory at the same virtual address as the CPU

int  cudaDeviceProp::clusterLaunch [inherited]
Indicates device supports cluster launch

int  cudaDeviceProp::computePreemptionSupported [inherited]
Device supports Compute Preemption

int  cudaDeviceProp::concurrentKernels [inherited]
Device can possibly execute multiple kernels concurrently

int  cudaDeviceProp::concurrentManagedAccess [inherited]
Device can coherently access managed memory concurrently with the CPU

int  cudaDeviceProp::cooperativeLaunch [inherited]
Device supports launching cooperative kernels via cudaLaunchCooperativeKernel

int  cudaDeviceProp::deferredMappingCudaArraySupported [inherited]
1 if the device supports deferred mapping CUDA arrays and CUDA mipmapped arrays

int  cudaDeviceProp::deviceNumaConfig [inherited]
NUMA configuration of a device: value is of type cudaDeviceNumaConfig enum

int  cudaDeviceProp::deviceNumaId [inherited]
NUMA node ID of the GPU memory

int  cudaDeviceProp::directManagedMemAccessFromHost [inherited]
Host can directly access managed memory on the device without migration.

int  cudaDeviceProp::globalL1CacheSupported [inherited]
Device supports caching globals in L1

unsigned int  cudaDeviceProp::gpuDirectRDMAFlushWritesOptions [inherited]
Bitmask to be interpreted according to the cudaFlushGPUDirectRDMAWritesOptions enum

int  cudaDeviceProp::gpuDirectRDMASupported [inherited]
1 if the device supports GPUDirect RDMA APIs, 0 otherwise

int  cudaDeviceProp::gpuDirectRDMAWritesOrdering [inherited]
See the cudaGPUDirectRDMAWritesOrdering enum for numerical values

unsigned int  cudaDeviceProp::gpuPciDeviceID [inherited]
The combined 16-bit PCI device ID and 16-bit PCI vendor ID

unsigned int  cudaDeviceProp::gpuPciSubsystemID [inherited]
The combined 16-bit PCI subsystem ID and 16-bit PCI subsystem vendor ID

int  cudaDeviceProp::hostNativeAtomicSupported [inherited]
Link between the device and the host supports native atomic operations

int  cudaDeviceProp::hostNumaId [inherited]
NUMA ID of the host node closest to the device or -1 when system does not support NUMA

int  cudaDeviceProp::hostNumaMultinodeIpcSupported [inherited]
1 if the device supports HostNuma location IPC between nodes in a multi-node system.

int  cudaDeviceProp::hostRegisterReadOnlySupported [inherited]
Device supports using the cudaHostRegister flag cudaHostRegisterReadOnly to register memory that must be mapped as read-only to the GPU

int  cudaDeviceProp::hostRegisterSupported [inherited]
Device supports host memory registration via cudaHostRegister.

int  cudaDeviceProp::integrated [inherited]
Device is integrated as opposed to discrete

int  cudaDeviceProp::ipcEventSupported [inherited]
Device supports IPC Events.

int  cudaDeviceProp::isMultiGpuBoard [inherited]
Device is on a multi-GPU board

int  cudaDeviceProp::l2CacheSize [inherited]
Size of L2 cache in bytes

int  cudaDeviceProp::localL1CacheSupported [inherited]
Device supports caching locals in L1

char  cudaDeviceProp::luid[8] [inherited]
8-byte locally unique identifier. Value is undefined on TCC and non-Windows platforms

unsigned int  cudaDeviceProp::luidDeviceNodeMask [inherited]
LUID device node mask. Value is undefined on TCC and non-Windows platforms

int  cudaDeviceProp::major [inherited]
Major compute capability

int  cudaDeviceProp::managedMemory [inherited]
Device supports allocating managed memory on this system

int  cudaDeviceProp::maxBlocksPerMultiProcessor [inherited]
Maximum number of resident blocks per multiprocessor

int  cudaDeviceProp::maxGridSize[3] [inherited]
Maximum size of each dimension of a grid

int  cudaDeviceProp::maxSurface1D [inherited]
Maximum 1D surface size

int  cudaDeviceProp::maxSurface1DLayered[2] [inherited]
Maximum 1D layered surface dimensions

int  cudaDeviceProp::maxSurface2D[2] [inherited]
Maximum 2D surface dimensions

int  cudaDeviceProp::maxSurface2DLayered[3] [inherited]
Maximum 2D layered surface dimensions

int  cudaDeviceProp::maxSurface3D[3] [inherited]
Maximum 3D surface dimensions

int  cudaDeviceProp::maxSurfaceCubemap [inherited]
Maximum Cubemap surface dimensions

int  cudaDeviceProp::maxSurfaceCubemapLayered[2] [inherited]
Maximum Cubemap layered surface dimensions

int  cudaDeviceProp::maxTexture1D [inherited]
Maximum 1D texture size

int  cudaDeviceProp::maxTexture1DLayered[2] [inherited]
Maximum 1D layered texture dimensions

int  cudaDeviceProp::maxTexture1DMipmap [inherited]
Maximum 1D mipmapped texture size

int  cudaDeviceProp::maxTexture2D[2] [inherited]
Maximum 2D texture dimensions

int  cudaDeviceProp::maxTexture2DGather[2] [inherited]
Maximum 2D texture dimensions if texture gather operations have to be performed

int  cudaDeviceProp::maxTexture2DLayered[3] [inherited]
Maximum 2D layered texture dimensions

int  cudaDeviceProp::maxTexture2DLinear[3] [inherited]
Maximum dimensions (width, height, pitch) for 2D textures bound to pitched memory

int  cudaDeviceProp::maxTexture2DMipmap[2] [inherited]
Maximum 2D mipmapped texture dimensions

int  cudaDeviceProp::maxTexture3D[3] [inherited]
Maximum 3D texture dimensions

int  cudaDeviceProp::maxTexture3DAlt[3] [inherited]
Maximum alternate 3D texture dimensions

int  cudaDeviceProp::maxTextureCubemap [inherited]
Maximum Cubemap texture dimensions

int  cudaDeviceProp::maxTextureCubemapLayered[2] [inherited]
Maximum Cubemap layered texture dimensions

int  cudaDeviceProp::maxThreadsDim[3] [inherited]
Maximum size of each dimension of a block

int  cudaDeviceProp::maxThreadsPerBlock [inherited]
Maximum number of threads per block

int  cudaDeviceProp::maxThreadsPerMultiProcessor [inherited]
Maximum resident threads per multiprocessor

size_t  cudaDeviceProp::memPitch [inherited]
Maximum pitch in bytes allowed by memory copies

int  cudaDeviceProp::memoryBusWidth [inherited]
Global memory bus width in bits

unsigned int  cudaDeviceProp::memoryPoolSupportedHandleTypes [inherited]
Bitmask of handle types supported with mempool-based IPC

int  cudaDeviceProp::memoryPoolsSupported [inherited]
1 if the device supports using the cudaMallocAsync and cudaMemPool family of APIs, 0 otherwise

int  cudaDeviceProp::minor [inherited]
Minor compute capability

int  cudaDeviceProp::mpsEnabled [inherited]
Indicates if contexts created on this device will be shared via MPS

int  cudaDeviceProp::multiGpuBoardGroupID [inherited]
Unique identifier for a group of devices on the same multi-GPU board

int  cudaDeviceProp::multiProcessorCount [inherited]
Number of multiprocessors on device

char  cudaDeviceProp::name[256] [inherited]
ASCII string identifying device

int  cudaDeviceProp::pageableMemoryAccess [inherited]
Device supports coherently accessing pageable memory without calling cudaHostRegister on it

int  cudaDeviceProp::pageableMemoryAccessUsesHostPageTables [inherited]
Device accesses pageable memory via the host's page tables

int  cudaDeviceProp::pciBusID [inherited]
PCI bus ID of the device

int  cudaDeviceProp::pciDeviceID [inherited]
PCI device ID of the device

int  cudaDeviceProp::pciDomainID [inherited]
PCI domain ID of the device

int  cudaDeviceProp::persistingL2CacheMaxSize [inherited]
Device's maximum l2 persisting lines capacity setting in bytes

int  cudaDeviceProp::regsPerBlock [inherited]
32-bit registers available per block

int  cudaDeviceProp::regsPerMultiprocessor [inherited]
32-bit registers available per multiprocessor

int  cudaDeviceProp::reserved[56] [inherited]
Reserved for future use

size_t  cudaDeviceProp::reservedSharedMemPerBlock [inherited]
Shared memory reserved by CUDA driver per block in bytes

size_t  cudaDeviceProp::sharedMemPerBlock [inherited]
Shared memory available per block in bytes

size_t  cudaDeviceProp::sharedMemPerBlockOptin [inherited]
Per device maximum shared memory per block usable by special opt in

size_t  cudaDeviceProp::sharedMemPerMultiprocessor [inherited]
Shared memory available per multiprocessor in bytes

int  cudaDeviceProp::sparseCudaArraySupported [inherited]
1 if the device supports sparse CUDA arrays and sparse CUDA mipmapped arrays, 0 otherwise

int  cudaDeviceProp::streamPrioritiesSupported [inherited]
Device supports stream priorities

size_t  cudaDeviceProp::surfaceAlignment [inherited]
Alignment requirements for surfaces

int  cudaDeviceProp::tccDriver [inherited]
1 if device is a Tesla device using TCC driver, 0 otherwise

size_t  cudaDeviceProp::textureAlignment [inherited]
Alignment requirement for textures

size_t  cudaDeviceProp::texturePitchAlignment [inherited]
Pitch alignment requirement for texture references bound to pitched memory

int  cudaDeviceProp::timelineSemaphoreInteropSupported [inherited]
External timeline semaphore interop is supported on the device

size_t  cudaDeviceProp::totalConstMem [inherited]
Constant memory available on device in bytes

size_t  cudaDeviceProp::totalGlobalMem [inherited]
Global memory available on device in bytes

int  cudaDeviceProp::unifiedAddressing [inherited]
Device shares a unified address space with the host

int  cudaDeviceProp::unifiedFunctionPointers [inherited]
Indicates device supports unified pointers

cudaUUID_t  cudaDeviceProp::uuid [inherited]
16-byte unique identifier

int  cudaDeviceProp::warpSize [inherited]
Warp size in threads


---