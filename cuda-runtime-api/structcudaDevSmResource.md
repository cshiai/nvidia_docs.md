# CUDA Runtime API

[< Previous](structcudaDevResource.html) | [Next >](structcudaDevSmResourceGroupParams.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.11. cudaDevSmResource Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Data for SM-related resources All parameters in this structure are OUTPUT only. Do not write to any of the fields in this structure.


### Public Variables


unsigned int  flagsunsigned int  minSmPartitionSizeunsigned int  smCoscheduledAlignmentunsigned int  smCount

### Variables


unsigned int  cudaDevSmResource::flags [inherited]
The flags set on this SM resource. For available flags see cudaDevSmResourceGroup_flags.

unsigned int  cudaDevSmResource::minSmPartitionSize [inherited]
The minimum number of streaming multiprocessors required to partition this resource.

unsigned int  cudaDevSmResource::smCoscheduledAlignment [inherited]
The number of streaming multiprocessors in this resource that are guaranteed to be co-scheduled on the same GPU processing
                                 cluster. smCount will be a multiple of this value, unless the backfill flag is set.

unsigned int  cudaDevSmResource::smCount [inherited]
The amount of streaming multiprocessors available in this resource.


---