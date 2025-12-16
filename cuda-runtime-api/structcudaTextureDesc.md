# CUDA Runtime API

[< Previous](structcudaResourceViewDesc.html) | [Next >](structCUuuid__st.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.66. cudaTextureDesc Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA texture descriptor


### Public Variables


enumcudaTextureAddressMode addressMode[3]float  borderColor[4]int  disableTrilinearOptimizationenumcudaTextureFilterMode filterModeunsigned int  maxAnisotropyfloat  maxMipmapLevelClampfloat  minMipmapLevelClampenumcudaTextureFilterMode mipmapFilterModefloat  mipmapLevelBiasint  normalizedCoordsenumcudaTextureReadMode readModeint  sRGBint  seamlessCubemap

### Variables


enumcudaTextureAddressModecudaTextureDesc::addressMode[3] [inherited]
Texture address mode for up to 3 dimensions

float  cudaTextureDesc::borderColor[4] [inherited]
Texture Border Color

int  cudaTextureDesc::disableTrilinearOptimization [inherited]
Disable any trilinear filtering optimizations.

enumcudaTextureFilterModecudaTextureDesc::filterMode [inherited]
Texture filter mode

unsigned int  cudaTextureDesc::maxAnisotropy [inherited]
Limit to the anisotropy ratio

float  cudaTextureDesc::maxMipmapLevelClamp [inherited]
Upper end of the mipmap level range to clamp access to

float  cudaTextureDesc::minMipmapLevelClamp [inherited]
Lower end of the mipmap level range to clamp access to

enumcudaTextureFilterModecudaTextureDesc::mipmapFilterMode [inherited]
Mipmap filter mode

float  cudaTextureDesc::mipmapLevelBias [inherited]
Offset applied to the supplied mipmap level

int  cudaTextureDesc::normalizedCoords [inherited]
Indicates whether texture reads are normalized or not

enumcudaTextureReadModecudaTextureDesc::readMode [inherited]
Texture read mode

int  cudaTextureDesc::sRGB [inherited]
Perform sRGB->linear conversion during texture read

int  cudaTextureDesc::seamlessCubemap [inherited]
Enable seamless cube map filtering.


---