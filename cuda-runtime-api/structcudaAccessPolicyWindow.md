# CUDA Runtime API

[< Previous](class____cudaOccupancyB2DHelper.html) | [Next >](structcudaArrayMemoryRequirements.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.2. cudaAccessPolicyWindow Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Specifies an access policy for a window, a contiguous extent of memory beginning at base_ptr and ending at base_ptr + num_bytes. Partition into many segments and assign segments such that. sum of "hit segments" / window == approx. ratio. sum of "miss segments" / window == approx 1-ratio. Segments and ratio specifications are fitted to the capabilities of the architecture. Accesses in a hit segment apply the hitProp access policy. Accesses in a miss segment apply the missProp access policy.


### Public Variables


void
                           * base_ptrenumcudaAccessProperty hitPropfloat  hitRatioenumcudaAccessProperty missPropsize_t  num_bytes

### Variables


void
                              * cudaAccessPolicyWindow::base_ptr [inherited]
Starting address of the access policy window. CUDA driver may align it.

enumcudaAccessPropertycudaAccessPolicyWindow::hitProp [inherited]
CUaccessProperty set for hit.

float  cudaAccessPolicyWindow::hitRatio [inherited]
hitRatio specifies percentage of lines assigned hitProp, rest are assigned missProp.

enumcudaAccessPropertycudaAccessPolicyWindow::missProp [inherited]
CUaccessProperty set for miss. Must be either NORMAL or STREAMING.

size_t  cudaAccessPolicyWindow::num_bytes [inherited]
Size in bytes of the window policy. CUDA driver may restrict the maximum size and alignment.


---