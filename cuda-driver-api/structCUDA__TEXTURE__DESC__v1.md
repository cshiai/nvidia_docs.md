# CUDA Driver API

[< Previous](structCUDA__RESOURCE__VIEW__DESC__v1.html) | [Next >](structCUdevprop__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.51. CUDA_TEXTURE_DESC_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Texture descriptor


### Public Variables


CUaddress_mode addressMode[3]float  borderColor[4]CUfilter_mode filterModeunsigned int  flagsunsigned int  maxAnisotropyfloat  maxMipmapLevelClampfloat  minMipmapLevelClampCUfilter_mode mipmapFilterModefloat  mipmapLevelBias

### Variables


CUaddress_modeCUDA_TEXTURE_DESC_v1::addressMode[3] [inherited]
Address modes

float  CUDA_TEXTURE_DESC_v1::borderColor[4] [inherited]
Border Color

CUfilter_modeCUDA_TEXTURE_DESC_v1::filterMode [inherited]
Filter mode

unsigned int  CUDA_TEXTURE_DESC_v1::flags [inherited]
Flags

unsigned int  CUDA_TEXTURE_DESC_v1::maxAnisotropy [inherited]
Maximum anisotropy ratio

float  CUDA_TEXTURE_DESC_v1::maxMipmapLevelClamp [inherited]
Mipmap maximum level clamp

float  CUDA_TEXTURE_DESC_v1::minMipmapLevelClamp [inherited]
Mipmap minimum level clamp

CUfilter_modeCUDA_TEXTURE_DESC_v1::mipmapFilterMode [inherited]
Mipmap filter mode

float  CUDA_TEXTURE_DESC_v1::mipmapLevelBias [inherited]
Mipmap level bias


---