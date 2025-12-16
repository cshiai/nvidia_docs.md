# CUDA Runtime API

[< Previous](structcudaPitchedPtr.html) | [Next >](structcudaPos.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.62. cudaPointerAttributes Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA pointer attributes


### Public Variables


int  devicevoid
                           * devicePointervoid
                           * hostPointerlong  reserved[8]enumcudaMemoryType type

### Variables


int  cudaPointerAttributes::device [inherited]
The device against which the memory was allocated or registered. If the memory type is cudaMemoryTypeDevice then this identifies the device on which the memory referred physically resides. If the memory type is cudaMemoryTypeHostor::cudaMemoryTypeManaged then this identifies the device which was current when the memory was allocated or registered (and if that device is deinitialized
                                 then this allocation will vanish with that device's state).

void
                              * cudaPointerAttributes::devicePointer [inherited]
The address which may be dereferenced on the current device to access the memory or NULL if no such address exists.

void
                              * cudaPointerAttributes::hostPointer [inherited]
The address which may be dereferenced on the host to access the memory or NULL if no such address exists.

Note:CUDA doesn't check if unregistered memory is allocated so this field may contain invalid pointer if an invalid pointer has
                                       been passed to CUDA.

long  cudaPointerAttributes::reserved[8] [inherited]
Must be zero

enumcudaMemoryTypecudaPointerAttributes::type [inherited]
The type of memory - cudaMemoryTypeUnregistered, cudaMemoryTypeHost, cudaMemoryTypeDevice or cudaMemoryTypeManaged.


---