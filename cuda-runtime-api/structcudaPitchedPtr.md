# CUDA Runtime API

[< Previous](structcudaOffset3D.html) | [Next >](structcudaPointerAttributes.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.61. cudaPitchedPtr Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA Pitched memory pointer


See also:


[make_cudaPitchedPtr](group__CUDART__MEMORY.html#group__CUDART__MEMORY_1gc3f66f8f11f9949768ae8d10cad5a1a0)




### Public Variables


size_t  pitchvoid
                           * ptrsize_t  xsizesize_t  ysize

### Variables


size_t  cudaPitchedPtr::pitch [inherited]
Pitch of allocated memory in bytes

void
                              * cudaPitchedPtr::ptr [inherited]
Pointer to allocated memory

size_t  cudaPitchedPtr::xsize [inherited]
Logical width of allocation in elements

size_t  cudaPitchedPtr::ysize [inherited]
Logical height of allocation in elements


---