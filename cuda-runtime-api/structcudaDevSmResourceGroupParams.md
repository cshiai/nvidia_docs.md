# CUDA Runtime API

[< Previous](structcudaDevSmResource.html) | [Next >](structcudaDevWorkqueueConfigResource.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.12. cudaDevSmResourceGroupParams Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Input data for splitting SMs


### Public Variables


unsigned int  coscheduledSmCountunsigned int  flagsunsigned int  preferredCoscheduledSmCountunsigned int  reserved[12]unsigned int  smCount

### Variables


unsigned int  cudaDevSmResourceGroupParams::coscheduledSmCount [inherited]
The amount of co-scheduled SMs grouped together for locality purposes.

unsigned int  cudaDevSmResourceGroupParams::flags [inherited]
Combination of cudaDevSmResourceGroup_flags values to indicate this this group is created.

unsigned int  cudaDevSmResourceGroupParams::preferredCoscheduledSmCount [inherited]
When possible, combine co-scheduled groups together into larger groups of this size.

unsigned int  cudaDevSmResourceGroupParams::reserved[12] [inherited]
Reserved for future use - ensure this is is zero initialized.

unsigned int  cudaDevSmResourceGroupParams::smCount [inherited]
The amount of SMs available in this resource.


---