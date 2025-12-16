# CUDA Driver API

[< Previous](structCUdevResource.html) | [Next >](structCUdevWorkqueueConfigResource.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.54. CUdevSmResource Struct Reference


## [[Green Contexts](group__CUDA__GREEN__CONTEXTS.html#group__CUDA__GREEN__CONTEXTS)]


Data for SM-related resources All parameters in this structure are OUTPUT only. Do not write to any of the fields in this structure.


### Public Variables


unsigned int  flagsunsigned int  minSmPartitionSizeunsigned int  smCoscheduledAlignmentunsigned int  smCount

### Variables


unsigned int  CUdevSmResource::flags [inherited]
The flags set on this SM resource. For possible values see CUdevSmResourceGroup_flags.

unsigned int  CUdevSmResource::minSmPartitionSize [inherited]
The minimum number of streaming multiprocessors required to partition this resource.

unsigned int  CUdevSmResource::smCoscheduledAlignment [inherited]
The number of streaming multiprocessors in this resource that are guaranteed to be co-scheduled on the same GPU processing
                                 cluster. smCount will be a multiple of this value, unless the backfill flag is set.

unsigned int  CUdevSmResource::smCount [inherited]
The amount of streaming multiprocessors available in this resource.


---