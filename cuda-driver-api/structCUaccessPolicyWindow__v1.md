# CUDA Driver API

[< Previous](structCU__DEV__SM__RESOURCE__GROUP__PARAMS.html) | [Next >](structCUarrayMapInfo__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.2. CUaccessPolicyWindow_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Specifies an access policy for a window, a contiguous extent of memory beginning at base_ptr and ending at base_ptr + num_bytes. num_bytes is limited by CU_DEVICE_ATTRIBUTE_MAX_ACCESS_POLICY_WINDOW_SIZE. Partition into many segments and assign segments such that: sum of "hit segments" / window == approx. ratio. sum of "miss segments" / window == approx 1-ratio. Segments and ratio specifications are fitted to the capabilities of the architecture. Accesses in a hit segment apply the hitProp access policy. Accesses in a miss segment apply the missProp access policy.


### Public Variables


void
                           * base_ptrCUaccessProperty hitPropfloat  hitRatioCUaccessProperty missPropsize_t  num_bytes

### Variables


void
                              * CUaccessPolicyWindow_v1::base_ptr [inherited]
Starting address of the access policy window. CUDA driver may align it.

CUaccessPropertyCUaccessPolicyWindow_v1::hitProp [inherited]
CUaccessProperty set for hit.

float  CUaccessPolicyWindow_v1::hitRatio [inherited]
hitRatio specifies percentage of lines assigned hitProp, rest are assigned missProp.

CUaccessPropertyCUaccessPolicyWindow_v1::missProp [inherited]
CUaccessProperty set for miss. Must be either NORMAL or STREAMING

size_t  CUaccessPolicyWindow_v1::num_bytes [inherited]
Size in bytes of the window policy. CUDA driver may restrict the maximum size and alignment.


---