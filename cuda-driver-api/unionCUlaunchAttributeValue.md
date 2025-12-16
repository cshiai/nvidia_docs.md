# CUDA Driver API

[< Previous](structCUlaunchAttribute.html) | [Next >](structCUlaunchConfig.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.67. CUlaunchAttributeValue Union Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Launch attributes union; used as value field of [CUlaunchAttribute](structCUlaunchAttribute.html#structCUlaunchAttribute)


### Public Variables


struct CUaccessPolicyWindow accessPolicyWindowCUlaunchAttributeValue::@6  clusterDimCUclusterSchedulingPolicy clusterSchedulingPolicyPreferenceint  cooperativeCUlaunchAttributeValue::@10  deviceUpdatableKernelNodeCUlaunchAttributeValue::@8  launchCompletionEventCUlaunchMemSyncDomain memSyncDomainstruct CUlaunchMemSyncDomainMap memSyncDomainMapCUlaunchAttributeValue::@9  preferredClusterDimint  priorityCUlaunchAttributeValue::@7  programmaticEventint  programmaticStreamSerializationAllowedunsigned int  sharedMemCarveoutCUsynchronizationPolicy  syncPolicy

### Variables


struct CUaccessPolicyWindowCUlaunchAttributeValue::accessPolicyWindow [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_ACCESS_POLICY_WINDOW.

CUlaunchAttributeValue::@6  CUlaunchAttributeValue::clusterDim [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_CLUSTER_DIMENSION that represents the desired cluster dimensions for the kernel. Opaque type with the following fields:


x - The X dimension of the cluster, in blocks. Must be a divisor of the grid X dimension.


y - The Y dimension of the cluster, in blocks. Must be a divisor of the grid Y dimension.


z - The Z dimension of the cluster, in blocks. Must be a divisor of the grid Z dimension.

CUclusterSchedulingPolicyCUlaunchAttributeValue::clusterSchedulingPolicyPreference [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_CLUSTER_SCHEDULING_POLICY_PREFERENCE. Cluster scheduling policy preference for the kernel.

int  CUlaunchAttributeValue::cooperative [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_COOPERATIVE. Nonzero indicates a cooperative kernel (see cuLaunchCooperativeKernel).

CUlaunchAttributeValue::@10  CUlaunchAttributeValue::deviceUpdatableKernelNode [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_DEVICE_UPDATABLE_KERNEL_NODE. with the following fields:


int deviceUpdatable - Whether or not the resulting kernel node should be device-updatable.


CUgraphDeviceNode devNode - Returns a handle to pass to the various device-side update functions.

CUlaunchAttributeValue::@8  CUlaunchAttributeValue::launchCompletionEvent [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_LAUNCH_COMPLETION_EVENT with the following fields:


CUevent event - Event to fire when the last block launches


int flags; - Event record flags, see cuEventRecordWithFlags. Does not accept CU_EVENT_RECORD_EXTERNAL.

CUlaunchMemSyncDomainCUlaunchAttributeValue::memSyncDomain [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_MEM_SYNC_DOMAIN. See::CUlaunchMemSyncDomain

struct CUlaunchMemSyncDomainMapCUlaunchAttributeValue::memSyncDomainMap [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_MEM_SYNC_DOMAIN_MAP. See CUlaunchMemSyncDomainMap.

CUlaunchAttributeValue::@9  CUlaunchAttributeValue::preferredClusterDim [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_PREFERRED_CLUSTER_DIMENSION that represents the desired preferred cluster dimensions for the kernel. Opaque type with the following fields:


x - The X dimension of the preferred cluster, in blocks. Must be a divisor of the grid X dimension, and must be a multiple
                                          of the x field of CUlaunchAttributeValue::clusterDim.


y - The Y dimension of the preferred cluster, in blocks. Must be a divisor of the grid Y dimension, and must be a multiple
                                          of the y field of CUlaunchAttributeValue::clusterDim.


z - The Z dimension of the preferred cluster, in blocks. Must be equal to the z field of CUlaunchAttributeValue::clusterDim.

int  CUlaunchAttributeValue::priority [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_PRIORITY. Execution priority of the kernel.

CUlaunchAttributeValue::@7  CUlaunchAttributeValue::programmaticEvent [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_PROGRAMMATIC_EVENT with the following fields:


CUevent event - Event to fire when all blocks trigger it.


Event record flags, see cuEventRecordWithFlags. Does not accept :CU_EVENT_RECORD_EXTERNAL.


triggerAtBlockStart - If this is set to non-0, each block launch will automatically trigger the event.

int  CUlaunchAttributeValue::programmaticStreamSerializationAllowed [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_PROGRAMMATIC_STREAM_SERIALIZATION.

unsigned int  CUlaunchAttributeValue::sharedMemCarveout [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_PREFERRED_SHARED_MEMORY_CARVEOUT.

CUsynchronizationPolicy  CUlaunchAttributeValue::syncPolicy [inherited]
Value of launch attribute CU_LAUNCH_ATTRIBUTE_SYNCHRONIZATION_POLICY. CUsynchronizationPolicy for work queued up in this stream


---