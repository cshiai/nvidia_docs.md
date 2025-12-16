# CUDA Driver API

[< Previous](structCUDA__TEXTURE__DESC__v1.html) | [Next >](structCUdevResource.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.52. CUdevprop_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Legacy device properties


### Public Variables


int  SIMDWidthint  clockRateint  maxGridSize[3]int  maxThreadsDim[3]int  maxThreadsPerBlockint  memPitchint  regsPerBlockint  sharedMemPerBlockint  textureAlignint  totalConstantMemory

### Variables


int  CUdevprop_v1::SIMDWidth [inherited]
Warp size in threads

int  CUdevprop_v1::clockRate [inherited]
Clock frequency in kilohertz

int  CUdevprop_v1::maxGridSize[3] [inherited]
Maximum size of each dimension of a grid

int  CUdevprop_v1::maxThreadsDim[3] [inherited]
Maximum size of each dimension of a block

int  CUdevprop_v1::maxThreadsPerBlock [inherited]
Maximum number of threads per block

int  CUdevprop_v1::memPitch [inherited]
Maximum pitch in bytes allowed by memory copies

int  CUdevprop_v1::regsPerBlock [inherited]
32-bit registers available per block

int  CUdevprop_v1::sharedMemPerBlock [inherited]
Shared memory available per block in bytes

int  CUdevprop_v1::textureAlign [inherited]
Alignment requirement for textures

int  CUdevprop_v1::totalConstantMemory [inherited]
Constant memory available on device in bytes


---