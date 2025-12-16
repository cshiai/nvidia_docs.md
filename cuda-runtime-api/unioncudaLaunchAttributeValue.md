# CUDA Runtime API

[< Previous](structcudaLaunchAttribute.html) | [Next >](structcudaLaunchConfig__t.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.43. cudaLaunchAttributeValue Union Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Launch attributes union; used as value field of [cudaLaunchAttribute](structcudaLaunchAttribute.html#structcudaLaunchAttribute)


### Public Variables


struct cudaAccessPolicyWindow accessPolicyWindowcudaLaunchAttributeValue::@29  clusterDimenumcudaClusterSchedulingPolicy clusterSchedulingPolicyPreferenceint  cooperativecudaLaunchAttributeValue::@33  deviceUpdatableKernelNodecudaLaunchAttributeValue::@32  launchCompletionEventcudaLaunchMemSyncDomain memSyncDomainstruct cudaLaunchMemSyncDomainMap memSyncDomainMapunsigned int  nvlinkUtilCentricSchedulingcudaLaunchAttributeValue::@31  preferredClusterDimint  prioritycudaLaunchAttributeValue::@30  programmaticEventint  programmaticStreamSerializationAllowedunsigned int  sharedMemCarveoutenum cudaSynchronizationPolicy  syncPolicy

### Variables


struct cudaAccessPolicyWindowcudaLaunchAttributeValue::accessPolicyWindow [inherited]
Value of launch attribute cudaLaunchAttributeAccessPolicyWindow.

cudaLaunchAttributeValue::@29  cudaLaunchAttributeValue::clusterDim [inherited]
Value of launch attribute cudaLaunchAttributeClusterDimension that represents the desired cluster dimensions for the kernel. Opaque type with the following fields:


x - The X dimension of the cluster, in blocks. Must be a divisor of the grid X dimension.


y - The Y dimension of the cluster, in blocks. Must be a divisor of the grid Y dimension.


z - The Z dimension of the cluster, in blocks. Must be a divisor of the grid Z dimension.

enumcudaClusterSchedulingPolicycudaLaunchAttributeValue::clusterSchedulingPolicyPreference [inherited]
Value of launch attribute cudaLaunchAttributeClusterSchedulingPolicyPreference. Cluster scheduling policy preference for the kernel.

int  cudaLaunchAttributeValue::cooperative [inherited]
Value of launch attribute cudaLaunchAttributeCooperative. Nonzero indicates a cooperative kernel (see cudaLaunchCooperativeKernel).

cudaLaunchAttributeValue::@33  cudaLaunchAttributeValue::deviceUpdatableKernelNode [inherited]
Value of launch attribute cudaLaunchAttributeDeviceUpdatableKernelNode with the following fields:


int deviceUpdatable - Whether or not the resulting kernel node should be device-updatable.


cudaGraphDeviceNode_t devNode - Returns a handle to pass to the various device-side update functions.

cudaLaunchAttributeValue::@32  cudaLaunchAttributeValue::launchCompletionEvent [inherited]
Value of launch attribute cudaLaunchAttributeLaunchCompletionEvent with the following fields:


cudaEvent_t event - Event to fire when the last block launches.


int flags - Event record flags, see cudaEventRecordWithFlags. Does not accept cudaEventRecordExternal.

cudaLaunchMemSyncDomaincudaLaunchAttributeValue::memSyncDomain [inherited]
Value of launch attribute cudaLaunchAttributeMemSyncDomain. See cudaLaunchMemSyncDomain.

struct cudaLaunchMemSyncDomainMapcudaLaunchAttributeValue::memSyncDomainMap [inherited]
Value of launch attribute cudaLaunchAttributeMemSyncDomainMap. See cudaLaunchMemSyncDomainMap.

unsigned int  cudaLaunchAttributeValue::nvlinkUtilCentricScheduling [inherited]
Value of launch attribute cudaLaunchAttributeNvlinkUtilCentricScheduling.

cudaLaunchAttributeValue::@31  cudaLaunchAttributeValue::preferredClusterDim [inherited]
Value of launch attribute cudaLaunchAttributePreferredClusterDimension that represents the desired preferred cluster dimensions for the kernel. Opaque type with the following fields:


x - The X dimension of the preferred cluster, in blocks. Must be a divisor of the grid X dimension, and must be a multiple
                                          of the x field of cudaLaunchAttributeValue::clusterDim.


y - The Y dimension of the preferred cluster, in blocks. Must be a divisor of the grid Y dimension, and must be a multiple
                                          of the y field of cudaLaunchAttributeValue::clusterDim.


z - The Z dimension of the preferred cluster, in blocks. Must be equal to the z field of cudaLaunchAttributeValue::clusterDim.

int  cudaLaunchAttributeValue::priority [inherited]
Value of launch attribute cudaLaunchAttributePriority. Execution priority of the kernel.

cudaLaunchAttributeValue::@30  cudaLaunchAttributeValue::programmaticEvent [inherited]
Value of launch attribute cudaLaunchAttributeProgrammaticEvent with the following fields:


cudaEvent_t event - Event to fire when all blocks trigger it.


int flags; - Event record flags, see cudaEventRecordWithFlags. Does not accept cudaEventRecordExternal.


int triggerAtBlockStart - If this is set to non-0, each block launch will automatically trigger the event.

int  cudaLaunchAttributeValue::programmaticStreamSerializationAllowed [inherited]
Value of launch attribute cudaLaunchAttributeProgrammaticStreamSerialization.

unsigned int  cudaLaunchAttributeValue::sharedMemCarveout [inherited]
Value of launch attribute cudaLaunchAttributePreferredSharedMemoryCarveout.

enum cudaSynchronizationPolicy  cudaLaunchAttributeValue::syncPolicy [inherited]
Value of launch attribute cudaLaunchAttributeSynchronizationPolicy. cudaSynchronizationPolicy for work queued up in this stream.


---