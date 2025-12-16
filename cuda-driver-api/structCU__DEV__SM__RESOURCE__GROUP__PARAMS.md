# CUDA Driver API

[< Previous](annotated.html) | [Next >](structCUaccessPolicyWindow__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.1. CU_DEV_SM_RESOURCE_GROUP_PARAMS Struct Reference


## [[Green Contexts](group__CUDA__GREEN__CONTEXTS.html#group__CUDA__GREEN__CONTEXTS)]


Input data for splitting SMs


### Public Variables


unsigned int  coscheduledSmCountunsigned int  flagsunsigned int  preferredCoscheduledSmCountunsigned int  reserved[12]unsigned int  smCount

### Variables


unsigned int  CU_DEV_SM_RESOURCE_GROUP_PARAMS::coscheduledSmCount [inherited]
The amount of co-scheduled SMs grouped together for locality purposes.

unsigned int  CU_DEV_SM_RESOURCE_GROUP_PARAMS::flags [inherited]
Combination of CUdevSmResourceGroup_flags values to indicate this this group is created.

unsigned int  CU_DEV_SM_RESOURCE_GROUP_PARAMS::preferredCoscheduledSmCount [inherited]
When possible, combine co-scheduled groups together into larger groups of this size.

unsigned int  CU_DEV_SM_RESOURCE_GROUP_PARAMS::reserved[12] [inherited]
Reserved for future use - ensure this is is zero initialized.

unsigned int  CU_DEV_SM_RESOURCE_GROUP_PARAMS::smCount [inherited]
The amount of SMs available in this resource.


---