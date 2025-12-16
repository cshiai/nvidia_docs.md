# Image Statistics Functions — npp 13.1 documentation

>


# Image Statistics Functions


Primitives for computing the statistical properties of an image.


Some statistical primitives also require scratch buffer during the computation. For details, please refer to [Scratch Buffer and Host Pointer](introduction.html#general_conventions_lb_1general_scratch_buffer).


These functions can be found in the nppist library. Linking to only the sub-libraries that you use can significantly save link time, application load time, and CUDA runtime startup time when using dynamic libraries.


## CommonGetBufferHostSizeParameters


Common parameters for nppiGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.

return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


## Image Sum


### Sum


Primitives for computing the sum of all the pixel values in an image.


Sum


Given an image \(pSrc\) with width \(W\) and height \(H\), the sum will be computed as



  \[Sum = \sum_{j=0}^{H-1}\sum_{i=0}^{W-1}pSrc(j,i)\] All the results are stored in a 64-bit double precision format, except for two primitives [nppiSum_8u64s_C1R_Ctx](image_statistics_functions.html#group__image__sum_1ga2e0254ca94d44a4080a201e7107945ca) and [nppiSum_8u64s_C4R_Ctx](image_statistics_functions.html#group__image__sum_1ga2d3cca17a193e01bd3bfd7b4d552f96e). The sum functions require additional scratch buffer for computations.
### Common parameters for nppiSum functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pDeviceBuffer
Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppiSumGetBufferHostSize_XX_XXX to determine the minium number of bytes required.

param pSum
Pointer to the computed sum.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSum_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pSum, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image sum.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_8u64s_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64s *pSum, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image sum.
The result is 64-bit long long integer.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pSum, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image sum.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pSum, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image sum.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pSum, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image sum.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aSum[3], NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image sum.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aSum[3], NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image sum.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aSum[3], NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image sum.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aSum[3], NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image sum.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aSum[3], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image sum ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aSum[3], NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image sum ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aSum[3], NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image sum ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aSum[3], NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image sum ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aSum[4], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image sum.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_8u64s_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64s aSum[4], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image sum.
The result is 64-bit long long integer.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aSum[4], NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image sum.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aSum[4], NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image sum.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


NppStatus nppiSum_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aSum[4], NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image sum.
For common parameter descriptions, see Common parameters for nppiSum functions include:.


SumGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the sum primitives.


### CommonSumGetBufferHostSizeParameters


Common parameters for nppiSumGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiSumGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_8u_C1R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_8u64s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_8u64s_C1R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_16u_C1R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_16s_C1R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_32f_C1R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_8u_C3R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_16u_C3R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_16s_C3R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_32f_C3R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_8u_AC4R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_16u_AC4R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_16s_AC4R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_32f_AC4R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_8u64s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_8u64s_C4R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_8u_C4R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_16u_C4R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_16s_C4R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


NppStatus nppiSumGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSum_32f_C4R_Ctx.
For common parameter descriptions, see CommonSumGetBufferHostSizeParameters.


## Image Min


### Min


Primitives for computing the minimal pixel value of an image.


Min


The scratch buffer is required by the min functions.


### Common parameters for nppiMin functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pDeviceBuffer
Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppiMinGetBufferHostSize_XX_XXX to determine the minium number of bytes required.

param pMin
Pointer to the computed min.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiMin_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pMin, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image min.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u *pMin, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image min.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s *pMin, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image min.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f *pMin, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image min.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u aMin[3], NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image min.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u aMin[3], NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image min.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s aMin[3], NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image min.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f aMin[3], NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image min.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u aMin[4], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image min.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u aMin[4], NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image min.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s aMin[4], NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image min.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f aMin[4], NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image min.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u aMin[3], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image min ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u aMin[3], NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image min ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s aMin[3], NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image min ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


NppStatus nppiMin_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f aMin[3], NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image min ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMin functions include:.


MinGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the min primitives.


### CommonMinGetBufferHostSizeParameters


Common parameters for nppiMinGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiMinGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_8u_C1R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_16u_C1R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_16s_C1R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_32f_C1R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_8u_C3R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_16u_C3R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_16s_C3R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_32f_C3R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_8u_C4R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_16u_C4R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_16s_C4R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_32f_C4R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_8u_AC4R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_16u_AC4R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_16s_AC4R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


NppStatus nppiMinGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMin_32f_AC4R_Ctx.
For common parameter descriptions, see CommonMinGetBufferHostSizeParameters.


## Image Min Index


### MinIndx


Primitives for computing the minimal value and its indices (X and Y coordinates) of an image.


MinIndx


If there are several minima in the selected ROI, the function returns one on the top leftmost position.


The scratch buffer is required by the functions.


### Common parameters for nppiMinIndx functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pDeviceBuffer
Pointer to the required device memory allocation, Scratch Buffer and Host Pointer Use nppiMinIndxGetBufferHostSize_XX_XXX to determine the minium number of bytes required.

param pMin
Pointer to the computed min result.

param pIndexX
Pointer to the X coordinate of the image min value.

param pIndexY
Ppointer to the Y coordinate of the image min value.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiMinIndx_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pMin, int *pIndexX, int *pIndexY, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image MinIndx.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:>.


NppStatus nppiMinIndx_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u *pMin, int *pIndexX, int *pIndexY, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image MinIndx.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s *pMin, int *pIndexX, int *pIndexY, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image MinIndx.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f *pMin, int *pIndexX, int *pIndexY, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image MinIndx.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u aMin[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image MinIndx.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u aMin[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image MinIndx.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s aMin[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image MinIndx.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f aMin[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image MinIndx.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u aMin[4], int aIndexX[4], int aIndexY[4], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image MinIndx.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u aMin[4], int aIndexX[4], int aIndexY[4], NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image MinIndx.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s aMin[4], int aIndexX[4], int aIndexY[4], NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image MinIndx.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f aMin[4], int aIndexX[4], int aIndexY[4], NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image MinIndx.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u aMin[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image MinIndx ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u aMin[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image MinIndx ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s aMin[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image MinIndx ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


NppStatus nppiMinIndx_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f aMin[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image MinIndx ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMinIndx functions include:.


MinIndxGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the MinIndx primitives.


### CommonMinIndxGetBufferHostSizeParameters


Common parameters for nppiMinIndxGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiMinIndxGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_8u_C1R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_16u_C1R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_16s_C1R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_32f_C1R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_8u_C3R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_16u_C3R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_16s_C3R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_32f_C3R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_8u_C4R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_16u_C4R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_16s_C4R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_32f_C4R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_8u_AC4R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_8u_AC4R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_16u_AC4R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


NppStatus nppiMinIndxGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMinIndx_32f_AC4R_Ctx.
For common parameter descriptions, see CommonMinIndxGetBufferHostSizeParameters.


## Image Max


### Max


Primitives for computing the maximal pixel value of an image.


#### Common parameters for nppiMax functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pDeviceBuffer
Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppiMaxGetBufferHostSize_XX_XXX to determine the minium number of bytes required.

param pMax
Pointer to the computed max.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Max


The scratch buffer is required by the functions.


NppStatus nppiMax_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pMax, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image Max.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u *pMax, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image Max.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s *pMax, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image Max.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f *pMax, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image Max.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u aMax[3], NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image Max.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u aMax[3], NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image Max.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s aMax[3], NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image Max.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f aMax[3], NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image Max.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u aMax[4], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image Max.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u aMax[4], NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image Max.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s aMax[4], NppStreamContext nppStreamCtx)
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f aMax[4], NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image Max.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u aMax[3], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image Max ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u aMax[3], NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image Max ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s aMax[3], NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image Max ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


NppStatus nppiMax_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f aMax[3], NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image Max ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMax functions include:.


MaxGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the Max primitives.


### CommonMaxGetBufferHostSizeParameters


Common parameters for nppiMaxGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiMaxGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_8u_C1R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_16u_C1R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_16s_C1R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_32f_C1R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_8u_C3R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_16u_C3R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_16s_C3R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_32f_C3R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_8u_C4R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_16u_C4R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_16s_C4R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_32f_C4R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_8u_AC4R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_16u_AC4R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_16s_AC4R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


NppStatus nppiMaxGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMax_32f_AC4R_Ctx.
For common parameter descriptions, see CommonMaxGetBufferHostSizeParameters.


## Image Max Index


### MaxIndx


Primitives for computing the maximal value and its indices (X and Y coordinates) of an image.


MaxIndx


If there are several maxima in the selected region of interest, the function returns one on the top leftmost position.


The scratch buffer is required by the functions.


### Common parameters for nppiMaxIndx functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pDeviceBuffer
Pointer to the required device memory allocation, Scratch Buffer and Host Pointer Use nppiMaxIndxGetBufferHostSize_XX_XXX to determine the minium number of bytes required.

param pMax
Pointer to the computed max result.

param pIndexX
Pointer to the X coordinate of the image max value.

param pIndexY
Ppointer to the Y coordinate of the image max value.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiMaxIndx_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pMax, int *pIndexX, int *pIndexY, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image MaxIndx.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u *pMax, int *pIndexX, int *pIndexY, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image MaxIndx.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s *pMax, int *pIndexX, int *pIndexY, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image MaxIndx.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f *pMax, int *pIndexX, int *pIndexY, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image MaxIndx.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u aMax[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image MaxIndx.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u aMax[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image MaxIndx.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s aMax[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image MaxIndx.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f aMax[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image MaxIndx.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u aMax[4], int aIndexX[4], int aIndexY[4], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image MaxIndx.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u aMax[4], int aIndexX[4], int aIndexY[4], NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image MaxIndx.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s aMax[4], int aIndexX[4], int aIndexY[4], NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image MaxIndx.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f aMax[4], int aIndexX[4], int aIndexY[4], NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image MaxIndx.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u aMax[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image MaxIndx ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16u aMax[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image MaxIndx ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp16s aMax[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image MaxIndx ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


NppStatus nppiMaxIndx_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp32f aMax[3], int aIndexX[3], int aIndexY[3], NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image MaxIndx ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMaxIndx functions include:.


MaxIndxGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the MaxIndx primitives.


### CommonMaxIndxGetBufferHostSizeParameters


Common parameters for nppiMaxIndxGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiMaxIndxGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_8u_C1R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_16u_C1R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_16s_C1R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_32f_C1R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_8u_C3R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_16u_C3R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_16s_C3R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_32f_C3R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_8u_C4R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_16u_C4R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_16s_C4R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_32f_C4R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_8u_AC4R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_8u_AC4R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_16u_AC4R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


NppStatus nppiMaxIndxGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the dvice scratch buffer size (in bytes) for nppiMaxIndx_32f_AC4R_Ctx.
For common parameter descriptions, see CommonMaxIndxGetBufferHostSizeParameters.


## Image MinMax


### MinMax


Primitives for computing both the minimal and the maximal values of an image.


MinMax


The functions require the device scratch buffer.


### Common parameters for nppiMinMax functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMin
Pointer to the computed minimal result.

param pMax
Pointer to the computed maximal result.

param pDeviceBuffer
Buffer to a scratch memory. Use nppiMinMax_XX_XXX to determine the minium number of bytes required.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiMinMax_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pMin, Npp8u *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image MinMax.


NppStatus nppiMinMax_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp16u *pMin, Npp16u *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image MinMax.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp16s *pMin, Npp16s *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image MinMax.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32f *pMin, Npp32f *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image MinMax.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u aMin[3], Npp8u aMax[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image MinMax.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp16u aMin[3], Npp16u aMax[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image MinMax.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp16s aMin[3], Npp16s aMax[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image MinMax.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32f aMin[3], Npp32f aMax[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image MinMax.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u aMin[3], Npp8u aMax[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image MinMax ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp16u aMin[3], Npp16u aMax[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image MinMax ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp16s aMin[3], Npp16s aMax[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32f aMin[3], Npp32f aMax[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image MinMax ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u aMin[4], Npp8u aMax[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image MinMax.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp16u aMin[4], Npp16u aMax[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image MinMax.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp16s aMin[4], Npp16s aMax[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image MinMax.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


NppStatus nppiMinMax_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32f aMin[4], Npp32f aMax[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image MinMax.
For common parameter descriptions, see Common parameters for nppiMinMax functions include:.


MinMaxGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the MinMax primitives.


### CommonMinMaxGetBufferHostSizeParameters


Common parameters for nppiMinMaxGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiMinMaxGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_8u_C1R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_16u_C1R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_16s_C1R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_32f_C1R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_8u_C3R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_16u_C3R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_16s_C3R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_32f_C3R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_8u_AC4R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_16u_AC4R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_16s_AC4R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_32f_AC4R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_8u_C4R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_16u_C4R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMinMax_16s_C4R_Ctx.
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


NppStatus nppiMinMaxGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
For common parameter descriptions, see CommonMinMaxGetBufferHostSizeParameters.


## Image Mean


### Mean


Primitives for computing the arithmetic mean of all the pixel values in an image.


Mean


Given an image \(pSrc\) with width \(W\) and height \(H\), the arithmetic mean will be computed as



  \[Mean = \frac{1}{W\cdot H}\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}pSrc(j,i)\] The mean functions require additional scratch buffer for computations.
### Common parameters for nppiMean functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMask
Mask-Image Pointer.

param nMaskStep
Mask-Image Line Step.

param nCOI
Channel_of_Interest Number.

param pDeviceBuffer
Pointer to the required device memory allocation, Scratch Buffer and Host Pointer Use nppiMeanGetBufferHostSize_XX_XXX to determine the minium number of bytes required.

param pMean
Pointer to the computed mean result.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes, or NPP_COI_ERROR if an invalid channel of interest is specified.s


NppStatus nppiMean_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aMean[3], NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aMean[3], NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aMean[3], NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aMean[3], NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aMean[4], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aMean[4], NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aMean[4], NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aMean[4], NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aMean[3], NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image Mean ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aMean[3], NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image Mean ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aMean[3], NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image Mean ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f aMean[3], NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image Mean ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_8u_C1MR_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit unsigned image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_8s_C1MR_Ctx(const Npp8s *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit signed image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_16u_C1MR_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, NppStreamContext nppStreamCtx)
Masked one-channel 16-bit unsigned image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_32f_C1MR_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, NppStreamContext nppStreamCtx)
Masked one-channel 32-bit floating point image Mean.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_8u_C3CMR_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp8u *pDeviceBuffer, Npp64f *pMean, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit unsigned image Mean affecting only single channel.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_8s_C3CMR_Ctx(const Npp8s *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp8u *pDeviceBuffer, Npp64f *pMean, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit signed image Mean affecting only single channel.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_16u_C3CMR_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp8u *pDeviceBuffer, Npp64f *pMean, NppStreamContext nppStreamCtx)
Masked three-channel 16-bit unsigned image Mean affecting only single channel.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


NppStatus nppiMean_32f_C3CMR_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp8u *pDeviceBuffer, Npp64f *pMean, NppStreamContext nppStreamCtx)
Masked three-channel 32-bit floating point image Mean affecting only single channel.
For common parameter descriptions, see Common parameters for nppiMean functions include:.


MeanGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the Mean primitives.


### CommonMeanGetBufferHostSizeParameters


Common parameters for nppiMeanGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiMeanGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_8u_C1R_Ctx.


NppStatus nppiMeanGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_16u_C1R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_16s_C1R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_32f_C1R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_8u_C3R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_16u_C3R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_16s_C3R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_32f_C3R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_8u_AC4R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_16u_AC4R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_16s_AC4R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_32f_AC4R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_8u_C4R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_16u_C4R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_16s_C4R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_32f_C4R_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_8u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_8u_C1MR_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_8s_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_8s_C1MR_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_16u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_16u_C1MR_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_32f_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_32f_C1MR_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_8u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_8u_C3CMR_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_8s_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_8s_C3CMR_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_16u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_16u_C3CMR_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


NppStatus nppiMeanGetBufferHostSize_32f_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_32f_C3CMR_Ctx.
For common parameter descriptions, see CommonMeanGetBufferHostSizeParameters.


## Image Mean StdDev


### Mean_StdDev


Primitives for computing both the arithmetic mean and the standard deviation of an image.


Mean_StdDev


Given an image \(pSrc\) with width \(W\) and height \(H\), the mean and the standard deviation will be computed as



  \[Mean = \frac{1}{W\cdot H}\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}pSrc(j,i)\]  \[StdDev = \sqrt{\frac{1}{W\cdot H}\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}(pSrc(j,i)-Mean)^2}\] The Mean_StdDev primitives require additional scratch buffer for computations.
### Common parameters for nppiMean_StdDev functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMask
Mask-Image Pointer.

param nMaskStep
Mask-Image Line Step.

param nCOI
Channel_of_Interest Number.

param pDeviceBuffer
Pointer to the required device memory allocation, Scratch Buffer and Host Pointer Use MeanStdDevGetBufferHostSize to determine the minium number of bytes required.

param pMean
Pointer to the computed mean.

param pStdDev
Pointer to the computed standard deviation.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes, or NPP_COI_ERROR if an invalid channel of interest is specified.


NppStatus nppiMean_StdDev_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image Mean_StdDev.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_8s_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image Mean_StdDev.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image Mean_StdDev.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image Mean_StdDev.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_8u_C1MR_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit unsigned image Mean_StdDev.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_8s_C1MR_Ctx(const Npp8s *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit signed image Mean_StdDev.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_16u_C1MR_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
Masked one-channel 16-bit unsigned image Mean_StdDev.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_32f_C1MR_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
Masked one-channel 32-bit floating point image Mean_StdDev.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


Channel Mean_StdDev


See [Channel-of-Interest API](introduction.html#nppi_conventions_lb_1channel_of_interest).


NppStatus nppiMean_StdDev_8u_C3CR_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, int nCOI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image Mean_StdDev affecting only single channel.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_8s_C3CR_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSizeROI, int nCOI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image Mean_StdDev affecting only single channel.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_16u_C3CR_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, int nCOI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image Mean_StdDev affecting only single channel.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_32f_C3CR_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, int nCOI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image Mean_StdDev affecting only single channel.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_8u_C3CMR_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit unsigned image Mean_StdDev.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_8s_C3CMR_Ctx(const Npp8s *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit signed image Mean_StdDev.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_16u_C3CMR_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
Masked three-channel 16-bit unsigned image Mean_StdDev.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


NppStatus nppiMean_StdDev_32f_C3CMR_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp8u *pDeviceBuffer, Npp64f *pMean, Npp64f *pStdDev, NppStreamContext nppStreamCtx)
Masked three-channel 32-bit floating point image Mean_StdDev.
For common parameter descriptions, see Common parameters for nppiMean_StdDev functions include:.


Unnamed Group


NppStatus nppiMeanStdDevGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_8u_C1R_Ctx.

MeanStdDevGetBufferHostSize

Companion primitives for computing the device buffer size (in bytes) required by the Mean_StdDev primitives.

Common parameters for MeanStdDevGetBufferHostSize functions include:


NppStatus nppiMeanStdDevGetBufferHostSize_8s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_8s_C1R_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_16u_C1R_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_32f_C1R_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_8u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_8u_C1MR_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_8s_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_8s_C1MR_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_16u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_16u_C1MR_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_32f_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_32f_C1MR_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_8u_C3CR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_8u_C3CR_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_8s_C3CR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_8s_C3CR_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_16u_C3CR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_16u_C3CR_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_32f_C3CR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_32f_C3CR_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_8u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_8u_C3CMR_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_8s_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_8s_C3CMR_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_16u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_16u_C3CMR_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


NppStatus nppiMeanStdDevGetBufferHostSize_32f_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMean_StdDev_32f_C3CMR_Ctx.
For common parameter descriptions, see Common parameters for MeanStdDevGetBufferHostSize functions include:.


## Image Norms


### Image Norms


Primitives for computing the norms of an image, the norms of difference, and the relative errors of two images. Given an image \(pSrc\) with width \(W\) and height \(H\),


 1. The infinity norm (Norm_Inf) is defined as the largest absolute pixel value of the image.
 2. The L1 norm (Norm_L1) is defined as the sum of the absolute pixel value of the image, i.e.,

  \[Norm\_L1 = \sum_{j=0}^{H-1}\sum_{i=0}^{W-1}\left| pSrc(j,i)\right|\] .
 3. The L2 norm (Norm_L2) is defined as the square root of the sum of the squared absolute pixel value of the image, i.e.,

  \[Norm\_L2 = \sqrt{\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}\left| pSrc(j,i)\right| ^2}\] .


Given two images \(pSrc1\) and \(pSrc2\) both with width \(W\) and height \(H\),


 1. The infinity norm of differece (NormDiff_Inf) is defined as the largest absolute difference between pixels of two images.
 2. The L1 norm of differece (NormDiff_L1) is defined as the sum of the absolute difference between pixels of two images, i.e.,

  \[NormDiff\_L1 = \sum_{j=0}^{H-1}\sum_{i=0}^{W-1}\left| pSrc1(j,i)-pSrc2(j,i)\right|\] .
 3. The L2 norm of differece (NormDiff_L2) is defined as the squared root of the sum of the squared absolute difference between pixels of two images, i.e.,

  \[NormDiff\_L2 = \sqrt{\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}\left| pSrc1(j,i)-pSrc2(j,i)\right| ^2}\] .


Given two images \(pSrc1\) and \(pSrc2\) both with width \(W\) and height \(H\),


 1. The relative error for the infinity norm of differece (NormRel_Inf) is defined as NormDiff_Inf divided by the infinity norm of the second image, i.e.,

  \[NormRel\_Inf = \frac{NormDiff\_Inf}{Norm\_Inf_{src2}}\]
 2. The relative error for the L1 norm of differece (NormRel_L1) is defined as NormDiff_L1 divided by the L1 norm of the second image, i.e.,

  \[NormRel\_L1 = \frac{NormDiff\_L1}{Norm\_L1_{src2}}\]
 3. The relative error for the L2 norm of differece (NormRel_L2) is defined as NormDiff_L2 divided by the L2 norm of the second image, i.e.,

  \[NormRel\_L2 = \frac{NormDiff\_L2}{Norm\_L2_{src2}}\]


The norm functions require the addition device scratch buffer for the computations.


#### Common parameters for nppiNorm functions include:




param pSrc1
Source-Image Pointer.

param nSrc1Step
Source-Image Line Step.

param pSrc2
Source-Image Pointer.

param nSrc2Step
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMask
Mask-Image Pointer.

param nMaskStep
Mask-Image Line Step.

param nCOI
Channel_of_Interest Number.

param pNorm
Pointer to the norm value.

param pNormDiff
Pointer to the computed norm of differences.

param pNormRel
Pointer to the computed relative error for the infinity norm of two images.

param pDeviceBuffer
Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppiNormInfGetBufferHostSize_XX_XXX to compute the required size (in bytes).

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes, or NPP_COI_ERROR if an invalid channel of interest is specified, or NPP_NOT_EVEN_STEP_ERROR if an invalid floating-point image is specified.


### Image Norm Inf


#### Norm_Inf


Primitives for computing the infinity norm of an image.


Basic Norm_Inf


NppStatus nppiNorm_Inf_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_32s_C1R_Ctx(const Npp32s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit signed image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image Norm_Inf ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image Norm_Inf ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image Norm_Inf ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image Norm_Inf ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_8u_C1MR_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit unsigned image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_8s_C1MR_Ctx(const Npp8s *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit signed image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_16u_C1MR_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 16-bit unsigned image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_32f_C1MR_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 32-bit floating point image Norm_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_8u_C3CMR_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit unsigned image Norm_Inf affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_8s_C3CMR_Ctx(const Npp8s *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit signed image Norm_Inf affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_16u_C3CMR_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 16-bit unsigned image Norm_Inf affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_Inf_32f_C3CMR_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 32-bit floating point image Norm_Inf affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NormInfGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the Norm_Inf primitives.


#### CommonNormInfGetBufferHostSizeParameters


Common parameters for nppiNormInfGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiNormInfGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_8u_C1R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_16u_C1R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_16s_C1R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_32s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_32s_C1R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_32f_C1R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_8u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_8u_C1MR_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_8s_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_8s_C1MR_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_16u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_16u_C1MR_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_32f_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_32f_C1MR_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_8u_C3R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_16u_C3R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_16s_C3R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_32f_C3R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_8u_AC4R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_16u_AC4R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_16s_AC4R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_32f_AC4R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_8u_C4R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_16u_C4R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_16s_C4R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_32f_C4R_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_8u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_8u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_8s_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_8s_C3CMR_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_16u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_16u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


NppStatus nppiNormInfGetBufferHostSize_32f_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_Inf_32f_C3CMR_Ctx.
For common parameter descriptions, see CommonNormInfGetBufferHostSizeParameters.


### Image Norm L1


#### Norm_L1


Primitives for computing the L1 norm of an image.


Basic Norm_L1


NppStatus nppiNorm_L1_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image Norm_L1 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image Norm_L1 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image Norm_L1 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image Norm_L1 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_8u_C1MR_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit unsigned image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_8s_C1MR_Ctx(const Npp8s *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit signed image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_16u_C1MR_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 16-bit unsigned image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_32f_C1MR_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 32-bit floating point image Norm_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_8u_C3CMR_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit unsigned image Norm_L1 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_8s_C3CMR_Ctx(const Npp8s *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit signed image Norm_L1 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_16u_C3CMR_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 16-bit unsigned image Norm_L1 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L1_32f_C3CMR_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 32-bit floating point image Norm_L1 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NormL1GetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the Norm_L1 primitives.


#### CommonNormL1GetBufferHostSizeParameters


Common parameters for nppiNormL1GetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiNormL1GetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_8u_C1R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_16u_C1R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_16s_C1R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_32f_C1R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_8u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_8u_C1MR_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_8s_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_8s_C1MR_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_16u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_16u_C1MR_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_32f_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_32f_C1MR_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_8u_C3R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_16u_C3R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_16s_C3R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_32f_C3R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_8u_AC4R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_16u_AC4R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_16s_AC4R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_32f_AC4R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_8u_C4R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_16u_C4R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_16s_C4R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_32f_C4R_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_8u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_8u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_8s_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_8s_C3CMR_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_16u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_16u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


NppStatus nppiNormL1GetBufferHostSize_32f_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L1_32f_C3CMR_Ctx.
For common parameter descriptions, see CommonNormL1GetBufferHostSizeParameters.


### Image Norm L2


#### Norm_L2


Primitives for computing the L2 norm of an image.


Basic Norm_L2


Computes the L2 norm of an image.


NppStatus nppiNorm_L2_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image Norm_L2 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image Norm_L2 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image Norm_L2 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image Norm_L2 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp64f aNorm[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_8u_C1MR_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit unsigned image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_8s_C1MR_Ctx(const Npp8s *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit signed image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_16u_C1MR_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 16-bit unsigned image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_32f_C1MR_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 32-bit floating point image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_8u_C3CMR_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit unsigned image Norm_L2.


NppStatus nppiNorm_L2_8s_C3CMR_Ctx(const Npp8s *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit signed image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_16u_C3CMR_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 16-bit unsigned image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNorm_L2_32f_C3CMR_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 32-bit floating point image Norm_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NormL2GetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the Norm_L2 primitives.


#### CommonNormL2GetBufferHostSizeParameters


Common parameters for nppiNormL2GetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiNormL2GetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_8u_C1R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_16u_C1R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_16s_C1R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_32f_C1R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_8u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_8u_C1MR_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_8s_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_8s_C1MR_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_16u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_16u_C1MR_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_32f_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_32f_C1MR_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_8u_C3R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_16u_C3R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_16s_C3R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_32f_C3R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_8u_AC4R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_16u_AC4R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_16s_AC4R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_32f_AC4R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_8u_C4R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_16u_C4R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_16s_C4R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_32f_C4R_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_8u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_8u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_8s_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_8s_C3CMR_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_16u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_16u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


NppStatus nppiNormL2GetBufferHostSize_32f_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNorm_L2_32f_C3CMR_Ctx.
For common parameter descriptions, see CommonNormL2GetBufferHostSizeParameters.


### Image NormDiff Inf


#### NormDiff_Inf


Primitives for computing the infinity norm of difference of pixels between two images.


Basic NormDiff_Inf


NppStatus nppiNormDiff_Inf_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_16s_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image NormDiff_Inf.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aNormDiff – Array that contains computed Inf-norm of differences.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes, or NPP_NOT_EVEN_STEP_ERROR if an invalid floating-point image is specified.


NppStatus nppiNormDiff_Inf_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image NormDiff_Inf ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image NormDiff_Inf ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_16s_AC4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image NormDiff_Inf ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image NormDiff_Inf ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_16s_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_8u_C1MR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit unsigned images NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_8s_C1MR_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit signed images NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_16u_C1MR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 16-bit unsigned images NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_32f_C1MR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 32-bit floating point images NormDiff_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_8u_C3CMR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit unsigned image NormDiff_Inf affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_8s_C3CMR_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit signed image NormDiff_Inf affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_16u_C3CMR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 16-bit unsigned image NormDiff_Inf affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_Inf_32f_C3CMR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 32-bit floating point image NormDiff_Inf affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NormDiffInfGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the NormDiff_Inf primitives.


#### CommonNormDiffInfGetBufferHostSizeParameters


Common parameters for nppiNormDiffInfGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiNormDiffInfGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_8u_C1R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_16u_C1R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_16s_C1R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_32f_C1R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_8u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_8u_C1MR_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_8s_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_8s_C1MR_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_16u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_16u_C1MR_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_32f_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_32f_C1MR_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_8u_C3R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_16u_C3R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_16s_C3R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_32f_C3R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_8u_C4R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_16u_C4R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_16s_C4R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_32f_C4R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_8u_AC4R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_16u_AC4R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_16s_AC4R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_32f_AC4R_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_8u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_8u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_8s_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_8s_C3CMR_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_16u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_16u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


NppStatus nppiNormDiffInfGetBufferHostSize_32f_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiNormDiff_Inf_32f_C3CMR_Ctx.
For common parameter descriptions, see CommonNormDiffInfGetBufferHostSizeParameters.


### Image NormDiff L1


#### NormDiff_L1


Primitives for computing the L1 norm of difference of pixels between two images.


Basic NormDiff_L1


NppStatus nppiNormDiff_L1_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_16s_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image NormDiff_L1 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image NormDiff_L1 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_16s_AC4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image NormDiff_L1 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image NormDiff_L1 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_16s_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_8u_C1MR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit unsigned image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_8s_C1MR_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit signed image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_16u_C1MR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 16-bit unsigned image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_32f_C1MR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 32-bit floating point image NormDiff_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_8u_C3CMR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit unsigned image NormDiff_L1 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_8s_C3CMR_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit signed image NormDiff_L1 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_16u_C3CMR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 16-bit unsigned image NormDiff_L1 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L1_32f_C3CMR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 32-bit floating point image NormDiff_L1 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NormDiffL1GetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the NormDiff_L1 primitives.


#### CommonNormDiffL1GetBufferHostSizeParameters


Common parameters for nppiNormDiffL1GetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiNormDiffL1GetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_8u_C1R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_16u_C1R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_16s_C1R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_32f_C1R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_8u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_8u_C1MR_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_8s_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_8s_C1MR_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_16u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_16u_C1MR_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_32f_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_32f_C1MR_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_8u_C3R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_16u_C3R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_16s_C3R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_32f_C3R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_8u_C4R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_16u_C4R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_16s_C4R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_32f_C4R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_8u_AC4R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_16u_AC4R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_16s_AC4R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_32f_AC4R_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_8u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_8u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_8s_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_8s_C3CMR_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_16u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_16u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


NppStatus nppiNormDiffL1GetBufferHostSize_32f_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L1_32f_C3CMR_Ctx.
For common parameter descriptions, see CommonNormDiffL1GetBufferHostSizeParameters.


### Image NormDiff L2


#### NormDiff_L2


Primitives for computing the L2 norm of difference of pixels between two images.


Basic NormDiff_L2


NppStatus nppiNormDiff_L2_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_16s_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image NormDiff_L2 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image NormDiff_L2 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_16s_AC4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image NormDiff_L2 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image NormDiff_L2 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_16s_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormDiff[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_8u_C1MR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit unsigned image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_8s_C1MR_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit signed image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_16u_C1MR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 16-bit unsigned image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_32f_C1MR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 32-bit floating point image NormDiff_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_8u_C3CMR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit unsigned image NormDiff_L2 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_8s_C3CMR_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit signed image NormDiff_L2 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_16u_C3CMR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 16-bit unsigned image NormDiff_L2 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormDiff_L2_32f_C3CMR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormDiff, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 32-bit floating point image NormDiff_L2 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NormDiffL2GetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the NormDiff_L2 primitives.


#### CommonNormDiffL2GetBufferHostSizeParameters


Common parameters for nppiNormDiffL2GetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiNormDiffL2GetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_8u_C1R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_16u_C1R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_16s_C1R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_32f_C1R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_8u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_8u_C1MR_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_8s_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_8s_C1MR_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_16u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_16u_C1MR_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_32f_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_32f_C1MR_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_8u_C3R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_16u_C3R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_16s_C3R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_32f_C3R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_8u_C4R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_16u_C4R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_16s_C4R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_32f_C4R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_8u_AC4R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_16u_AC4R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_16s_AC4R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_32f_AC4R_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_8u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_8u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_8s_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_8s_C3CMR_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_16u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_16u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


NppStatus nppiNormDiffL2GetBufferHostSize_32f_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormDiff_L2_32f_C3CMR_Ctx.
For common parameter descriptions, see CommonNormDiffL2GetBufferHostSizeParameters.


### Image NormRel Inf


#### NormRel_Inf


Primitives for computing the relative error of infinity norm between two images.


Basic NormRel_Inf


NppStatus nppiNormRel_Inf_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_16s_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image NormRel_Inf ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image NormRel_Inf ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_16s_AC4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image NormRel_Inf ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image NormRel_Inf ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_16s_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_8u_C1MR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit unsigned image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_8s_C1MR_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit signed image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_16u_C1MR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 16-bit unsigned image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_32f_C1MR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 32-bit floating point image NormRel_Inf.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_8u_C3CMR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit unsigned image NormRel_Inf affecting only signle channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_8s_C3CMR_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit signed image NormRel_Inf affecting only signle channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_16u_C3CMR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 16-bit unsigned image NormRel_Inf affecting only signle channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_Inf_32f_C3CMR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 32-bit floating point image NormRel_Inf affecting only signle channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NormRelInfGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the NormRel_Inf primitives.


#### CommonNormRelInfGetBufferHostSizeParameters


Common parameters for nppiNormRelInfGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiNormRelInfGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_8u_C1R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_16u_C1R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_16s_C1R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_32f_C1R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_8u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_8u_C1MR_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_8s_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_8s_C1MR_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_16u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_16u_C1MR_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_32f_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_32f_C1MR_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_8u_C3R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_16u_C3R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_16s_C3R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_32f_C3R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_8u_C4R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_16u_C4R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_16s_C4R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_32f_C4R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_8u_AC4R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_16u_AC4R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_16s_AC4R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_32f_AC4R_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_8u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_8u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_8s_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_8s_C3CMR_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_16u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_16u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


NppStatus nppiNormRelInfGetBufferHostSize_32f_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_Inf_32f_C3CMR_Ctx.
For common parameter descriptions, see CommonNormRelInfGetBufferHostSizeParameters.


### Image NormRel L1


#### NormRel_L1


Primitives for computing the relative error of L1 norm between two images.


Basic NormRel_L1


NppStatus nppiNormRel_L1_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_16s_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image NormRel_L1 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image NormRel_L1 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_16s_AC4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image NormRel_L1 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image NormRel_L1 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_16s_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_8u_C1MR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_8s_C1MR_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_16u_C1MR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_32f_C1MR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image NormRel_L1.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_8u_C3CMR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit unsigned image NormRel_L1 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_8s_C3CMR_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit signed image NormRel_L1 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_16u_C3CMR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 16-bit unsigned image NormRel_L1 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L1_32f_C3CMR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 32-bit floating point image NormRel_L1 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NormRelL1GetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the NormRel_L1 primitives.


#### CommonNormRelL1GetBufferHostSizeParameters


Common parameters for nppiNormRelL1GetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiNormRelL1GetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_8u_C1R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_16u_C1R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_16s_C1R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_32f_C1R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_8u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_8u_C1MR_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_8s_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_8s_C1MR_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_16u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_16u_C1MR_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_32f_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_32f_C1MR_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_8u_C3R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_16u_C3R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_16s_C3R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_32f_C3R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_8u_C4R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_16u_C4R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_16s_C4R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_32f_C4R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_8u_AC4R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_16u_AC4R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_16s_AC4R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_32f_AC4R_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_8u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_8u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_8s_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_8s_C3CMR_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_16u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_16u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


NppStatus nppiNormRelL1GetBufferHostSize_32f_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L1_32f_C3CMR_Ctx.
For common parameter descriptions, see CommonNormRelL1GetBufferHostSizeParameters.


### Image NormRel L2


#### NormRel_L2


Primitives for computing the relative error of L2 norm between two images.


Basic NormRel_L2


NppStatus nppiNormRel_L2_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_16s_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image NormRel_L2 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image NormRel_L2 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_16s_AC4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image NormRel_L2 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image NormRel_L2 ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_16s_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aNormRel[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_8u_C1MR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit unsigned image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_8s_C1MR_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 8-bit signed image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_16u_C1MR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 16-bit unsigned image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_32f_C1MR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked one-channel 32-bit floating point image NormRel_L2.
For common parameter descriptions, see Common parameters for nppiNorm functions include: .


NppStatus nppiNormRel_L2_8u_C3CMR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit unsigned image NormRel_L2 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_8s_C3CMR_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 8-bit signed image NormRel_L2 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_16u_C3CMR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 16-bit unsigned image NormRel_L2 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NppStatus nppiNormRel_L2_32f_C3CMR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, NppiSize oSizeROI, int nCOI, Npp64f *pNormRel, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Masked three-channel 32-bit floating point image NormRel_L2 affecting only single channel.
For common parameter descriptions, see Common parameters for nppiNorm functions include:.


NormRelL2GetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the NormRel_L2 primitives.


#### CommonNormRelL2GetBufferHostSizeParameters


Common parameters for nppiNormRelL2GetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiNormRelL2GetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_8u_C1R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_16u_C1R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_16s_C1R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_32f_C1R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_8u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_8u_C1MR_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_8s_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_8s_C1MR_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_16u_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_16u_C1MR_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_32f_C1MR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_32f_C1MR_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_8u_C3R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_16u_C3R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_16s_C3R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_32f_C3R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_8u_C4R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_16u_C4R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_16s_C4R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_32f_C4R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_8u_AC4R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_16u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_16u_AC4R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_16s_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_16s_AC4R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_32f_AC4R_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_8u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_8u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_8s_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_8s_C3CMR_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_16u_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_16u_C3CMR_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


NppStatus nppiNormRelL2GetBufferHostSize_32f_C3CMR_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Computes the device scratch buffer size (in bytes) for nppiNormRel_L2_32f_C3CMR_Ctx.
For common parameter descriptions, see CommonNormRelL2GetBufferHostSizeParameters.


## Image DotProd


### DotProd


Primitives for computing the dot product of two images.


DotProd


Given two images \(pSrc1\) and \(pSrc2\) both with width \(W\) and height \(H\), the dot product will be computed as



  \[DotProd = \sum_{j=0}^{H-1}\sum_{i=0}^{W-1}[pSrc1(j,i)\cdot pSrc2(j,i)]\] The functions require additional scratch buffer for computations.
### Common parameters for nppiDotProd functions include:




param pSrc1
Source-Image Pointer.

param nSrc1Step
Source-Image Line Step.

param pSrc2
Source-Image Pointer.

param nSrc2Step
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pDp
Pointer to the computed dot product of the two images.

param pDeviceBuffer
Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDotProd_8u64f_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_8s64f_C1R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_16u64f_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_16s64f_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_32u64f_C1R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit unsigned image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_32s64f_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit signed image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_32f64f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_8u64f_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_8s64f_C3R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_16u64f_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_16s64f_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_32u64f_C3R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit unsigned image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_32s64f_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit signed image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_32f64f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_8u64f_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_8s64f_C4R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_16u64f_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_16s64f_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_32u64f_C4R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit unsigned image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_32s64f_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit signed image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_32f64f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[4], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image DotProd.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_8u64f_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image DotProd ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_8s64f_AC4R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image DotProd ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_16u64f_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image DotProd ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_16s64f_AC4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image DotProd ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_32u64f_AC4R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit unsigned image DotProd ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_32s64f_AC4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit signed image DotProd ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


NppStatus nppiDotProd_32f64f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f aDp[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image DotProd ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiDotProd functions include:.


DotProdGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the Mean_StdDev primitives.


### CommonDotProdGetBufferHostSizeParameters


Common parameters for nppiDotProdGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiDotProdGetBufferHostSize_8u64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_8u64f_C1R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_8s64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_8s64f_C1R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_16u64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_16u64f_C1R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_16s64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_16s64f_C1R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_32u64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_32u64f_C1R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_32s64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_32s64f_C1R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_32f64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_32f64f_C1R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_8u64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_8u64f_C3R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_8s64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_8s64f_C3R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_16u64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_16u64f_C3R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_16s64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_16s64f_C3R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_32u64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_32u64f_C3R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_32s64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_32s64f_C3R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_32f64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_32f64f_C3R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_8u64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_8u64f_C4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_8s64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_8s64f_C4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_16u64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_16u64f_C4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_16s64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_16s64f_C4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_32u64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_32u64f_C4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_32s64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_32s64f_C4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_32f64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_32f64f_C4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_8u64f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_8u64f_AC4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_8s64f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_8s64f_AC4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_16u64f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_16u64f_AC4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_16s64f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_16s64f_AC4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_32u64f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_32u64f_AC4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_32s64f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_32s64f_AC4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


NppStatus nppiDotProdGetBufferHostSize_32f64f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiDotProd_32f64f_AC4R_Ctx.
For common parameter descriptions, see CommonDotProdGetBufferHostSizeParameters.


## Image Count In Range


### CountInRange.


Primitives for computing the amount of pixels that fall into the specified intensity range.


CountInRange


The lower bound and the upper bound are inclusive.


The functions require additional scratch buffer for computations.


### Common parameters for nppiCountInRange functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pCounts
Pointer to the number of pixels that fall into the specified range.

param nLowerBound
Lower bound of the specified range.

param nUpperBound
Upper bound of the specified range.

param pDeviceBuffer
Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes, or NPP_RANGE_ERROR if the lower bound is larger than the upper bound.


NppStatus nppiCountInRange_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, int *pCounts, Npp8u nLowerBound, Npp8u nUpperBound, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CountInRange.
For common parameter descriptions, see Common parameters for nppiCountInRange functions include:.


NppStatus nppiCountInRange_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, int *pCounts, Npp32f nLowerBound, Npp32f nUpperBound, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image CountInRange.
For common parameter descriptions, see Common parameters for nppiCountInRange functions include:.


NppStatus nppiCountInRange_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, int aCounts[3], Npp8u aLowerBound[3], Npp8u aUpperBound[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CountInRange.
For common parameter descriptions, see Common parameters for nppiCountInRange functions include:.


NppStatus nppiCountInRange_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, int aCounts[3], Npp32f aLowerBound[3], Npp32f aUpperBound[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image CountInRange.
For common parameter descriptions, see Common parameters for nppiCountInRange functions include:.


NppStatus nppiCountInRange_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, int aCounts[3], Npp8u aLowerBound[3], Npp8u aUpperBound[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CountInRange ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiCountInRange functions include:.


NppStatus nppiCountInRange_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, int aCounts[3], Npp32f aLowerBound[3], Npp32f aUpperBound[3], Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CountInRange ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiCountInRange functions include:.


CountInRangeGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the CountInRange primitives.


### CommonCountInRangeGetBufferHostSizeParameters


Common parameters for nppiCountInRangeGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiCountInRangeGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiCountInRange_8u_C1R_Ctx.
For common parameter descriptions, see CommonCountInRangeGetBufferHostSizeParameters.


NppStatus nppiCountInRangeGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiCountInRange_32f_C1R_Ctx.
For common parameter descriptions, see CommonCountInRangeGetBufferHostSizeParameters.


NppStatus nppiCountInRangeGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiCountInRange_8u_C3R_Ctx.
For common parameter descriptions, see CommonCountInRangeGetBufferHostSizeParameters.


NppStatus nppiCountInRangeGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiCountInRange_32f_C3R_Ctx.
For common parameter descriptions, see CommonCountInRangeGetBufferHostSizeParameters.


NppStatus nppiCountInRangeGetBufferHostSize_8u_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiCountInRange_8u_AC4R_Ctx.
For common parameter descriptions, see CommonCountInRangeGetBufferHostSizeParameters.


NppStatus nppiCountInRangeGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppiCountInRange_32f_AC4R_Ctx.
For common parameter descriptions, see CommonCountInRangeGetBufferHostSizeParameters.


## Image MaxEvery


### MaxEvery


Primitives for computing the maximal value of the pixel pair from two images.


MaxEvery


The maximum is stored into the second image.


### Common parameters for nppiMaxEvery functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pSrcDst
In-Place Image Pointer.

param nSrcDstStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMaxEvery_8u_C1IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image MaxEvery.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_16u_C1IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image MaxEvery.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_16s_C1IR_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image MaxEvery.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_32f_C1IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image MaxEvery.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_8u_C3IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image MaxEvery.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_16u_C3IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image MaxEvery.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_16s_C3IR_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image MaxEvery.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_32f_C3IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image MaxEvery.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_8u_C4IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image MaxEvery.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_16u_C4IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image MaxEvery.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_16s_C4IR_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image MaxEvery.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_32f_C4IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image MaxEvery.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_8u_AC4IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image MaxEvery ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_16u_AC4IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image MaxEvery ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_16s_AC4IR_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image MaxEvery ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


NppStatus nppiMaxEvery_32f_AC4IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image MaxEvery ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMaxEvery functions include:.


## Image MinEvery


### MinEvery


Primitives for computing the minimal value of the pixel pair from two images.


MinEvery


The minimum is stored into the second image.


### Common parameters for nppiMinEvery functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pSrcDst
In-Place Image Pointer.

param nSrcDstStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMinEvery_8u_C1IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image MinEvery.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_16u_C1IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image MinEvery.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_16s_C1IR_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image MinEvery.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_32f_C1IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image MinEvery.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_8u_C3IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image MinEvery.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_16u_C3IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image MinEvery.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_16s_C3IR_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image MinEvery.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_32f_C3IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image MinEvery.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_8u_C4IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image MinEvery.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_16u_C4IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image MinEvery.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_16s_C4IR_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image MinEvery.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_32f_C4IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image MinEvery.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_8u_AC4IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image MinEvery ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_16u_AC4IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image MinEvery ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_16s_AC4IR_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image MinEvery ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


NppStatus nppiMinEvery_32f_AC4IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image MinEvery ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiMinEvery functions include:.


## Image Integral


### Integral


Primitives for computing the integral image of a given image.


Integral


Given an input image \(pSrc\) and the specified value \(nVal\), the pixel value of the integral image \(pDst\) at coordinate (i, j) will be computed as



  \[pDst(j,i) = nVal + \sum_{l=0}^{j-1}\sum_{k=0}^{i-1}pSrc(l,k)\] If the size of the input image is \(W \times H\), the size of the integral image will be \((W+1) \times (H+1)\).
NppStatus nppiIntegral_8u32s_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp32s *pDst, int nDstStep, NppiSize oROI, Npp32s nVal, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image Integral with 32-bit signed output.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oROI – Region-Of-Interest (ROI).
nVal – The value to add to pDst image pixels
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiIntegral_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oROI, Npp32f nVal, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image Integral with 32-bit floating point output.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oROI – Region-Of-Interest (ROI).
nVal – The value to add to pDst image pixels
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


## Image Square Integral


### SqrIntegral


Primitives for computing both the integral and the squared integral images of a given image.


SqrIntegral


Given an input image \(pSrc\) and the specified value \(nVal\), the pixel value of the integral image \(pDst\) at coordinate (i, j) will be computed as



  \[pDst(j,i) = nVal + \sum_{l=0}^{j-1}\sum_{k=0}^{i-1}pSrc(l,k)\] Given an input image \(pSrc\) and the specified value \(nValSqr\), the pixel value of the squared integral image \(pSqr\) at coordinate (i, j) will be computed as  \[pSqr(j,i) = nValSqr + \sum_{l=0}^{j-1}\sum_{k=0}^{i-1}{pSrc(l,k)}^2\] If the size of the input image is \(W \times H\), the size of the squared integral image will be \((W+1) \times (H+1)\).
NppStatus nppiSqrIntegral_8u32s_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp32s *pDst, int nDstStep, Npp32s *pSqr, int nSqrStep, NppiSize oSrcROI, Npp32s nVal, Npp32s nValSqr, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image SqrIntegral.
Destination integral image and square integral image are 32-bit signed int.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
pSqr – Destination-Image Pointer.
nSqrStep – Destination-Image Line Step.
oSrcROI – Region-Of-Interest (ROI).
nVal – The value to add to pDst image pixels
nValSqr – The value to add to pSqr image pixels
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSqrIntegral_8u32s64f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp32s *pDst, int nDstStep, Npp64f *pSqr, int nSqrStep, NppiSize oSrcROI, Npp32s nVal, Npp64f nValSqr, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image SqrIntegral.
Destination integral image is 32-bit signed int. Destination square integral image is 64-bit double floating point.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
pSqr – Destination-Image Pointer.
nSqrStep – Destination-Image Line Step.
oSrcROI – Region-Of-Interest (ROI).
nVal – The value to add to pDst image pixels
nValSqr – The value to add to pSqr image pixels
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSqrIntegral_8u32f64f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, Npp64f *pSqr, int nSqrStep, NppiSize oSrcROI, Npp32f nVal, Npp64f nValSqr, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image SqrIntegral.
Destination integral image is 32-bit floating point. Destination square integral image is 64-bit double floating point.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
pSqr – Destination-Image Pointer.
nSqrStep – Destination-Image Line Step.
oSrcROI – Region-Of-Interest (ROI).
nVal – The value to add to pDst image pixels
nValSqr – The value to add to pSqr image pixels
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


## Image RectStdDev


### RectStdDev


Primitives for computing the stansdard deviation of the integral images. The function computes the standard deviation of the pixel in the rectangular window with the integral image \(pSrc\) and the squared integral image \(pSqr\), which can be obtained by calling [Integral](image_statistics_functions.html#group__image__integral_1image_integral) and [SqrIntegral](image_statistics_functions.html#group__image__sqrintegral_1image_sqrintegral).


The standard deviation of the pixel \((j, i)\) can be computed using the formula:

  \[pDst(j, i) = \sqrt{max(0, \frac{\sum(SqrIntegral)\cdot N - (\sum(Integral))^2}{N^2})}\] where \(\sum(SqrIntegral) = pSqr[j+oRect.y+oRect.height, i+oRect.x+oRect.width] - pSqr[j+oRect.y,i+oRect.x+oRect.width] - pSqr[j+oRect.y+oRect.height, i+oRect.x] + pSqr[j+oRect.y, i+oRect.x]\), \(\sum(Integral) = pSrc[j+oRect.y+oRect.height, i+oRect.x+oRect.width] - pSrc[j+oRect.y,i+oRect.x+oRect.width] - pSrc[j+oRect.y+oRect.height, i+oRect.x] + pSrc[j+oRect.y, i+oRect.x]\), \(N = oRect.width \cdot oRect.height\).
The size of the \(pSrc\) and \(pSqr\) should be \((oSizeROI.width + oRect.x + oRect.width, oSizeROI.height + oRect.y + oRect.height).\)


RectStdDev


NppStatus nppiRectStdDev_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp64f *pSqr, int nSqrStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppiRect oRect, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image RectStdDev.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSqr – Destination-Image Pointer.
nSqrStep – Destination-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
oRect – rectangular window
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRectStdDev_32s_C1RSfs_Ctx(const Npp32s *pSrc, int nSrcStep, const Npp32s *pSqr, int nSqrStep, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppiRect oRect, int nScaleFactor, NppStreamContext nppStreamCtx)
One-channel 32-bit signed image RectStdDev, scaled by \(2^(-nScaleFactor)\).

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSqr – Destination-Image Pointer.
nSqrStep – Destination-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
oRect – rectangular window
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRectStdDev_32s32f_C1R_Ctx(const Npp32s *pSrc, int nSrcStep, const Npp64f *pSqr, int nSqrStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppiRect oRect, NppStreamContext nppStreamCtx)
One-channel 32-bit signed image RectStdDev.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSqr – Destination-Image Pointer.
nSqrStep – Destination-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
oRect – rectangular window
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


## Image Histogram Even


### HistogramEven


Primitives for computing the histogram of an image with evenly distributed bins.


HistogramEven


The \(nLowerLevel\) (inclusive) and \(nUpperLevel\) (exclusive) define the boundaries of the range, which are evenly segmented into \(nLevel - 1\) bins.


The computed histogram is stored in \(pHist\). The levels are calculated by another primitive [nppiEvenLevelsHost_32s](image_statistics_functions.html#group__image__histogrameven_1gaf60397e584d096dca93cb541d23fe44d) and are stored in a host pointer \(hpLevels\). The number of levels is also \(nLevel - 1\). The histogram \(pHist[k]\) is defined as the total number of pixels that fall into the range: \(hpLevels[k] <= pSrc(j, i) < hpLevels[k+1]\). The functions require additional scratch buffer for computations.


### Common parameters for nppiHistogramEven functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pHist
Pointer to array that receives the computed histogram. The array must be of size nLevels-1.

param nLevels
Number of levels.

param nLowerLevel
Lower boundary of lowest level bin.

param nUpperLevel
Upper boundary of highest level bin.

param pBuffer
Pointer to appropriately sized scratch buffer.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiEvenLevelsHost_32s(Npp32s *hpLevels, int nLevels, Npp32s nLowerLevel, Npp32s nUpperLevel)
Compute levels with even distribution.

Parameters

hpLevels – A host pointer to array which receives the levels being computed. The array needs to be of size nLevels.
nLevels – The number of levels being computed. nLevels must be at least 2.
nLowerLevel – Lower boundary value of the lowest level.
nUpperLevel – Upper boundary value of the greatest level.

Returns

image_data_error_codes, or NPP_HISTO_NUMBER_OF_LEVELS_ERROR if an invalid nLevels is specified.


NppStatus nppiHistogramEven_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist, int nLevels, Npp32s nLowerLevel, Npp32s nUpperLevel, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned HistogramEven.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramEven_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], int nLevels[3], Npp32s nLowerLevel[3], Npp32s nUpperLevel[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned HistogramEven.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramEven_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[4], int nLevels[4], Npp32s nLowerLevel[4], Npp32s nUpperLevel[4], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned HistogramEven.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramEven_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], int nLevels[3], Npp32s nLowerLevel[3], Npp32s nUpperLevel[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned HistogramEven ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramEven_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist, int nLevels, Npp32s nLowerLevel, Npp32s nUpperLevel, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned HistogramEven.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramEven_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], int nLevels[3], Npp32s nLowerLevel[3], Npp32s nUpperLevel[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned HistogramEven.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramEven_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[4], int nLevels[4], Npp32s nLowerLevel[4], Npp32s nUpperLevel[4], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned HistogramEven.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramEven_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], int nLevels[3], Npp32s nLowerLevel[3], Npp32s nUpperLevel[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned HistogramEven ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramEven_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist, int nLevels, Npp32s nLowerLevel, Npp32s nUpperLevel, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed HistogramEven.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramEven_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], int nLevels[3], Npp32s nLowerLevel[3], Npp32s nUpperLevel[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed HistogramEven.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramEven_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[4], int nLevels[4], Npp32s nLowerLevel[4], Npp32s nUpperLevel[4], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed HistogramEven.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramEven_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], int nLevels[3], Npp32s nLowerLevel[3], Npp32s nUpperLevel[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed HistogramEven ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


HistogramEvenGetBufferSize


Companion primitives for computing the device buffer size (in bytes) required by the HistogramEven primitives.


### Common parameters for nppiHistogramEvenGetBufferSize functions include:




param oSizeROI
Region-Of-Interest (ROI).

param nLevels
Number of levels in the histogram.

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes..


NppStatus nppiHistogramEvenGetBufferSize_8u_C1R_Ctx(NppiSize oSizeROI, int nLevels, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiHistogramEven_8u_C1R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramEvenGetBufferSize_8u_C3R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiHistogramEven_8u_C3R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramEvenGetBufferSize_8u_C4R_Ctx(NppiSize oSizeROI, int nLevels[4], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiHistogramEven_8u_C4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramEvenGetBufferSize_8u_AC4R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiHistogramEven_8u_AC4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramEvenGetBufferSize_16u_C1R_Ctx(NppiSize oSizeROI, int nLevels, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiHistogramEven_16u_C1R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramEvenGetBufferSize_16u_C3R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiHistogramEven_16u_C3R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramEvenGetBufferSize_16u_C4R_Ctx(NppiSize oSizeROI, int nLevels[4], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiHistogramEven_16u_C4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramEvenGetBufferSize_16u_AC4R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiHistogramEven_16u_AC4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramEvenGetBufferSize_16s_C1R_Ctx(NppiSize oSizeROI, int nLevels, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiHistogramEven_16s_C1R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramEvenGetBufferSize_16s_C3R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiHistogramEven_16s_C3R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramEvenGetBufferSize_16s_C4R_Ctx(NppiSize oSizeROI, int nLevels[4], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiHistogramEven_16s_C4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramEvenGetBufferSize_16s_AC4R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiHistogramEven_16s_AC4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


## Image Histogram Range


### HistogramRange


Primitives for computing the histogram of an image within specified ranges.


HistogramRange


The histogram is computed according to the ranges provided in \(pLevels\).


The histogram \(pHist[k]\) is defined as the total number of pixels that fall into the range: \(pLevels[k] <= pSrc(j, i) < pLevels[k+1]\). The number of the histogram bins is \(nLevel - 1\). The functions require additional scratch buffer for computations.


### Common parameters for nppiHistogramRange functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pHist
Pointer to array that receives the computed histogram. The array must be of size nLevels-1.

param pLevels
Pointer to array containing the level sizes of the bins. The array must be of size nLevels.

param nLevels
Number of levels in histogram.

param pBuffer
Pointer to appropriately sized (nppiHistogramRangeGetBufferSize_XX_XXX) scratch buffer.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiHistogramRange_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist, const Npp32s *pLevels, int nLevels, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], const Npp32s *pLevels[3], int nLevels[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[4], const Npp32s *pLevels[4], int nLevels[4], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], const Npp32s *pLevels[3], int nLevels[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned HistogramRange ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist, const Npp32s *pLevels, int nLevels, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], const Npp32s *pLevels[3], int nLevels[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[4], const Npp32s *pLevels[4], int nLevels[4], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], const Npp32s *pLevels[3], int nLevels[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned HistogramRange ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist, const Npp32s *pLevels, int nLevels, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], const Npp32s *pLevels[3], int nLevels[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[4], const Npp32s *pLevels[4], int nLevels[4], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], const Npp32s *pLevels[3], int nLevels[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist, const Npp32f *pLevels, int nLevels, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], const Npp32f *pLevels[3], int nLevels[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[4], const Npp32f *pLevels[4], int nLevels[4], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point HistogramRange.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


NppStatus nppiHistogramRange_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSizeROI, Npp32s *pHist[3], const Npp32f *pLevels[3], int nLevels[3], Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point HistogramRange ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiHistogramEven functions include:.


HistogramRangeGetBufferSize


Companion primitives for computing the device buffer size (in bytes) required by the HistogramRange primitives.


NppStatus nppiHistogramRangeGetBufferSize_8u_C1R_Ctx(NppiSize oSizeROI, int nLevels, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_8u_C1R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_8u_C3R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_8u_C3R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_8u_C4R_Ctx(NppiSize oSizeROI, int nLevels[4], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_8u_C4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_8u_AC4R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_8u_AC4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_16u_C1R_Ctx(NppiSize oSizeROI, int nLevels, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_16u_C1R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_16u_C3R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_16u_C3R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_16u_C4R_Ctx(NppiSize oSizeROI, int nLevels[4], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_16u_C4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_16u_AC4R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_16u_AC4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_16s_C1R_Ctx(NppiSize oSizeROI, int nLevels, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_16s_C1R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_16s_C3R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_16s_C3R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_16s_C4R_Ctx(NppiSize oSizeROI, int nLevels[4], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_16s_C4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_16s_AC4R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_16s_AC4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_32f_C1R_Ctx(NppiSize oSizeROI, int nLevels, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_32f_C1R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_32f_C3R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_32f_C3R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_32f_C4R_Ctx(NppiSize oSizeROI, int nLevels[4], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_32f_C4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


NppStatus nppiHistogramRangeGetBufferSize_32f_AC4R_Ctx(NppiSize oSizeROI, int nLevels[3], size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Scratch-buffer size for nppiHistogramRange_32f_AC4R_Ctx.
For common parameter descriptions, see Common parameters for nppiHistogramEvenGetBufferSize functions include:.


## Image Proximity


### Image Proximity


Primitives for computing the proximity measure between a source image and a template image.


#### General Introduction


There are basically two approaches to compute the proximity measure for template matching, Euclidean distance and the cross correlation.


 1. Euclidean distance computes the sum of the squared distance (SSD) between the corresponding pixels of the source image and the template image. The smaller the distance is, the more similar the source image and the template image is around the pixel. The anchor of the template


image is used during the computations, which always lies in the gemotric center of the image. Given a source image

 \(pSrc\) ( \(W_s \times H_s\)) and a template image \(pTpl\) ( \(W_t \times H_t\)), the Euclidean distance \(D_{st}(c,r)\) between two images at pixel in row \(r\) and column \(c\) is computed as ( \(s\) stands for source image and \(t\) for template image for short):  \[D_{st}(c,r)=\sum_{j=0}^{H_t-1}\sum_{i=0}^{W_t-1}[pTpl(j,i)-pSrc(j+c-\frac{H_t}{2}, i+r-\frac{W_t}{2})]^2 \]
 2. Cross correlation computes the sum of the product between the corresponding pixels of the source image and the template image. The cross correlation \(R_{st}(c,r)\) is calculated as:

  \[R_{st}(c,r)=\sum_{j=0}^{H_t-1}\sum_{i=0}^{W_t-1}[pTpl(j,i)\cdot pSrc(j+c-\frac{H_t}{2}, i+r-\frac{W_t}{2})] \] The larger the cross correlation value is, the more similar the source image and the template image is around the pixel.
 3. The cross correlation \(R_{st}(c,r)\) is affected by the brightness of the images which may vary due to the lighting and exposure conditions. Therefore, NPP computes the cross correlation coefficient to circumvent this dependence. This is typically done at every step by subtracting the mean from every pixel value, i.e.,

  \[\tilde{R}_{st}(c,r)=\sum_{j=0}^{H_t-1}\sum_{i=0}^{W_t-1}[pTpl(j,i)-Mean_t]\cdot [pSrc(j+c-\frac{H_t}{2}, i+r-\frac{W_t}{2})-Mean_s] \]


NPP computes the normalized values of Euclidean distance, cross correlation and the cross correlation coefficient.


 1. The normalized Euclidean distance \(\sigma_{st}(c,r)\) is defined as:

  \[\sigma_{st}(c,r) = \frac{D_{st}(c,r)}{\sqrt{R_{ss}(c,r)\cdot R_{tt}(\frac{H_t}{2},\frac{W_t}{2})}} \]
 2. The normalized cross correlation \(\rho_{st}(c,r)\) is defined as:

  \[\rho_{st}(c,r) = \frac{R_{st}(c,r)}{\sqrt{R_{ss}(c,r)\cdot R_{tt}(\frac{H_t}{2},\frac{W_t}{2})}} \] The \(R_{ss}(c,r)\) and \(R_{tt}(\frac{H_t}{2}, \frac{W_t}{2}\) denote the auto correlation of the source image and the template image individually. They are defined as:  \[R_{ss}(c,r)=\sum_{j=c-\frac{H_t}{2}}^{c+\frac{H_t}{2}}\sum_{i=r-\frac{W_t}{2}}^{r+\frac{W_t}{2}}pSrc(j, i) \]  \[R_{tt}(\frac{H_t}{2},\frac{W_t}{2})=\sum_{j=0}^{H_t-1}\sum_{i=0}^{W_t-1}pTpl(j,i) \]
 3. Similarly, the normalized cross correlation coefficient \(\gamma_{st}(c,r)\) is calculated as:

  \[\gamma_{st}(c,r) = \frac{\tilde{R}_{st}(c,r)}{\sqrt{\tilde{R}_{ss}(c,r)\cdot \tilde{R}_{tt}(\frac{H_t}{2},\frac{W_t}{2})}} \] The \(\tilde{R}_{ss}(c,r)\) and \(\tilde{R}_{tt}(\frac{H_t}{2}, \frac{W_t}{2}\) are defined as:  \[\tilde{R}_{ss}(c,r)=\sum_{j=c-\frac{H_t}{2}}^{c+\frac{H_t}{2}}\sum_{i=r-\frac{W_t}{2}}^{r+\frac{W_t}{2}}[pSrc(j, i)-Mean_s] \]  \[\tilde{R}_{tt}(\frac{H_t}{2},\frac{W_t}{2})=\sum_{j=0}^{H_t-1}\sum_{i=0}^{W_t-1}[pTpl(j,i)-Mean_t] \] where \(Mean_t\) is the template mean minus the mean of the image in the region just under the template.


#### Categorizations


The Euclidean distance and the cross correlation are categorized into three types, full, same, and valid.


 1. Full mode indicates that the anchor of the template image starts from the outside of the source image, assuming the out-of-boundary pixels are zeor-padded. The size of the destination image is \((W_s + W_t - 1) \times (H_s + H_t - 1)\).
 2. Same mode means that the anchor of the template image starts from the top left pixel of the source image. All the out-of-boundary pixels are also zero-padded. The size of the destination image is the same as the source one, i.e., \(W_s \times H_s\).
 3. Valid mode indicates that there are no out-of-boudnary readings from the source image. The anchor of the template image starts from the inside of the source image. The size of the destination image is \((W_s - W_t + 1) \times (H_s - H_t + 1)\).


## Image Square Distance Full Norm


### SqrDistanceFull_Norm


Primitives for computing the normalized Euclidean distance between two images with full mode.


SqrDistanceFull_Norm


The functions compute the \(\sigma_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with full mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


### Common parameters for nppiSqrDistanceFull functions include:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcRoiSize
Region-Of-Interest (ROI).

param pTpl
Pointer to the template image.

param nTplStep
Number of bytes between successive rows in the template image.

param oTplRoiSize
Region-Of-Interest (ROI).

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param nScaleFactor
Integer Result Scaling.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSqrDistanceFull_Norm_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image SqrDistanceFull_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image SqrDistanceFull_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_8u_C4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image SqrDistanceFull_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_8u_AC4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image SqrDistanceFull_Norm ignoring alpha channel, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image SqrDistanceFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image SqrDistanceFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image SqrDistanceFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image SqrDistanceFull_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image SqrDistanceFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image SqrDistanceFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_8u32f_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image SqrDistanceFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_8u32f_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image SqrDistanceFull_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image SqrDistanceFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_8s32f_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image SqrDistanceFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_8s32f_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image SqrDistanceFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_8s32f_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image SqrDistanceFull_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image SqrDistanceFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image SqrDistanceFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_16u32f_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image SqrDistanceFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceFull_Norm_16u32f_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image SqrDistanceFull_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


## Image Square Distance Same Norm


### SqrDistanceSame_Norm


Primitives for computing the normalized Euclidean distance between two images with same mode.


SqrDistanceSame_Norm


The functions compute the \(\sigma_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with same mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


NppStatus nppiSqrDistanceSame_Norm_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image SqrDistanceSame_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image SqrDistanceSame_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_8u_C4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image SqrDistanceSame_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_8u_AC4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image SqrDistanceSame_Norm ignoring alpha channel, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image SqrDistanceSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image SqrDistanceSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image SqrDistanceSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image SqrDistanceSame_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image SqrDistanceSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image SqrDistanceSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_8u32f_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image SqrDistanceSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_8u32f_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image SqrDistanceSame_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image SqrDistanceSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_8s32f_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image SqrDistanceSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_8s32f_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image SqrDistanceSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_8s32f_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image SqrDistanceSame_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image SqrDistanceSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image SqrDistanceSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_16u32f_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image SqrDistanceSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_16u32f_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image SqrDistanceSame_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceSame_Norm_16u32f_AC4R(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep)
Four-channel 16-bit unsigned image SqrDistanceSame_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


## Image Square Distance Valid Norm


### SqrDistanceValid_Norm


Primitives for computing the normalized Euclidean distance between two images with valid mode.


SqrDistanceValid_Norm


The functions compute the \(\sigma_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with valid mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


NppStatus nppiSqrDistanceValid_Norm_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image SqrDistanceValid_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image SqrDistanceValid_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_8u_C4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image SqrDistanceValid_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_8u_AC4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image SqrDistanceValid_Norm ignoring alpha channel, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image SqrDistanceValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image SqrDistanceValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image SqrDistanceValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image SqrDistanceValid_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image SqrDistanceValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image SqrDistanceValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_8u32f_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image SqrDistanceValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_8u32f_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image SqrDistanceValid_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image SqrDistanceValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_8s32f_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image SqrDistanceValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_8s32f_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image SqrDistanceValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_8s32f_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image SqrDistanceValid_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image SqrDistanceValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image SqrDistanceValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_16u32f_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image SqrDistanceValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiSqrDistanceValid_Norm_16u32f_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image SqrDistanceValid_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


## Image Cross Correlation Full Norm


### CrossCorrFull_Norm


Primitives for computing the normalized cross correlation between two images with full mode.


CrossCorrFull_Norm


The functions compute the \(\rho_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with full mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


NppStatus nppiCrossCorrFull_Norm_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrFull_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrFull_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_8u_C4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrFull_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_8u_AC4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrFull_Norm ignoring alpha channel, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrFull_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_64f_C1R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_64f_C3R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_64f_C4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_64f_AC4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrFull_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_8u32f_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_8u32f_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrFull_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_8s32f_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_8s32f_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_8s32f_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrFull_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_16u32f_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrFull_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_Norm_16u32f_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrFull_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


## Image Cross Correlation Same Norm


### CrossCorrSame_Norm


Primitives for computing the normalized cross correlation between two images with same mode.


CrossCorrSame_Norm


The functions compute the \(\rho_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with same mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


NppStatus nppiCrossCorrSame_Norm_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrSame_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrSame_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_8u_C4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrSame_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_8u_AC4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrSame_Norm ignoring alpha channel, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrSame_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_64f_C1R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_64f_C3R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_64f_C4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_64f_AC4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrSame_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_8u32f_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_8u32f_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrSame_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_8s32f_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_8s32f_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_8s32f_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrSame_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_16u32f_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrSame_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_Norm_16u32f_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrSame_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


## Image Cross Correlation Valid Norm


### CrossCorrValid_Norm


Primitives for computing the normalized cross correlation between two images with valid mode.


CrossCorrValid_Norm


The functions compute the \(\rho_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with valid mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


NppStatus nppiCrossCorrValid_Norm_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrValid_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrValid_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_8u_C4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrValid_Norm, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_8u_AC4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrValid_Norm ignoring alpha channel, scaled by \(2^(-nScaleFactor)\).
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrValid_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_64f_C1R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_64f_C3R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_64f_C4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_64f_AC4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrValid_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_8u32f_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_8u32f_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrValid_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_8s32f_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_8s32f_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_8s32f_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrValid_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_16u32f_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrValid_Norm.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_Norm_16u32f_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrValid_Norm ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


## Image Cross Correlation Valid


### CrossCorrValid


Primitives for computing the cross correlation between two images with valid mode.


CrossCorrValid


The functions compute the \(R_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with valid mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


NppStatus nppiCrossCorrValid_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point images CrossCorrValid.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_64f_C1R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point images CrossCorrValid.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned images CrossCorrValid.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 8-bit signed images CrossCorrValid.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned images CrossCorrValid.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


## Image Cross Correlation Full Norm Level


### CrossCorrFull_NormLevel


Primitives for computing the normalized cross correlation coefficient between two images with full mode.


CrossCorrFull_NormLevel


The functions compute the \(\gamma_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with full mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


The functions require additional scratch buffer for computations.


Note: For maximum performance oSrcRoiSize.width + oTplRoiSize.width - 1 MUST be an integer multiple of 4.


NppStatus nppiCrossCorrFull_NormLevel_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_8u_C4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_8u_AC4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrFull_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrFull_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_64f_C1R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_64f_C3R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_64f_C4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_64f_AC4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrFull_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_8u32f_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_8u32f_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrFull_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_8s32f_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_8s32f_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_8s32f_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrFull_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_16u32f_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrFull_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevel_16u32f_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrFull_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


FullNormLevelGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the CrossCorrFull_NormLevel primitives.


### CommonFullNormLevelGetBufferHostSizeParameters


Common parameters for nppiFullNormLevelGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiFullNormLevelGetBufferHostSize_8u_C1RSfs_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_8u_C1RSfs_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_8u_C3RSfs_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_8u_C3RSfs_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_8u_C4RSfs_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_8u_C4RSfs_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_8u_AC4RSfs_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_8u_AC4RSfs_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_32f_C1R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_32f_C3R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_32f_C4R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_32f_AC4R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_64f_C1R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_64f_C3R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_64f_C4R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_64f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_64f_AC4R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_8u32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_8u32f_C1R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_8u32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_8u32f_C3R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_8u32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_8u32f_C4R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_8u32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_8u32f_AC4R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_8s32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_8s32f_C1R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_8s32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_8s32f_C3R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_8s32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_8s32f_C4R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_8s32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_8s32f_AC4R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_16u32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_16u32f_C1R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_16u32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_16u32f_C3R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_16u32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_16u32f_C4R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


NppStatus nppiFullNormLevelGetBufferHostSize_16u32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevel_16u32f_AC4R_Ctx.
For common parameter descriptions, see CommonFullNormLevelGetBufferHostSizeParameters.


## Image Cross Correlation Same Norm Level


### CrossCorrSame_NormLevel


Primitives for computing the normalized cross correlation coefficient between two images with same mode.


CrossCorrSame_NormLevel


The functions compute the \(\gamma_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with same mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


The functions require additional scratch buffer for computations.


Note: For maximum performance oSrcRoiSize.width MUST be an integer multiple of 4.


NppStatus nppiCrossCorrSame_NormLevel_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_8u_C4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_8u_AC4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrSame_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrSame_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_64f_C1R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_64f_C3R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_64f_C4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_64f_AC4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrSame_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_8u32f_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_8u32f_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrSame_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_8s32f_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_8s32f_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_8s32f_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrSame_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_16u32f_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrSame_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevel_16u32f_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrSame_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


SameNormLevelGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the CrossCorrSame_NormLevel primitives.


### CommonSameNormLevelGetBufferHostSizeParameters


Common parameters for nppiSameNormLevelGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiSameNormLevelGetBufferHostSize_8u_C1RSfs_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_8u_C1RSfs.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_8u_C3RSfs_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_8u_C3RSfs_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_8u_C4RSfs_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_8u_C4RSfs_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_8u_AC4RSfs_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_8u_AC4RSfs_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_32f_C1R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_32f_C3R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_32f_C4R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_32f_AC4R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_64f_C1R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_64f_C3R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_64f_C4R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_64f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_64f_AC4R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_8u32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_8u32f_C1R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_8u32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_8u32f_C3R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_8u32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_8u32f_C4R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_8u32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_8u32f_AC4R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_8s32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_8s32f_C1R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_8s32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_8s32f_C3R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_8s32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_8s32f_C4R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_8s32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_8s32f_AC4R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_16u32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_16u32f_C1R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_16u32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_16u32f_C3R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_16u32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_16u32f_C4R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


NppStatus nppiSameNormLevelGetBufferHostSize_16u32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevel_16u32f_AC4R_Ctx.
For common parameter descriptions, see CommonSameNormLevelGetBufferHostSizeParameters.


## Image Cross Correlation Valid Norm Level


### CrossCorrValid_NormLevel


Primitives for computing the normalized cross correlation coefficient between two images with valid mode.


CrossCorrValid_NormLevel


The functions compute the \(\gamma_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with valid mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


The functions require additional scratch buffer for computations.


Note: For maximum performance oSrcRoiSize.width - oTplRoiSize + 1 MUST be an integer multiple of 4.


NppStatus nppiCrossCorrValid_NormLevel_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_8u_C4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_8u_AC4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp8u *pDst, int nDstStep, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrValid_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrValid_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_64f_C1R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_64f_C3R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_64f_C4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_64f_AC4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrValid_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_8u32f_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_8u32f_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrValid_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_8s32f_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_8s32f_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_8s32f_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrValid_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_16u32f_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrValid_NormLevel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevel_16u32f_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrValid_NormLevel ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


ValidNormLevelGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the CrossCorrValid_NormLevel primitives.


### CommonValidNormLevelGetBufferHostSizeParameters


Common parameters for nppiValidNormLevelGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiValidNormLevelGetBufferHostSize_8u_C1RSfs_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_8u_C1RSfs_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_8u_C3RSfs_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_8u_C1RSfs_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_8u_C4RSfs_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_8u_C4RSfs_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_8u_AC4RSfs_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_8u_AC4RSfs_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_32f_C1R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_32f_C3R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_32f_C4R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_32f_AC4R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_64f_C1R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_64f_C3R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_64f_C4R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_64f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_64f_AC4R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_8u32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_8u32f_C1R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_8u32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_8u32f_C3R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_8u32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_8u32f_C4R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_8u32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_8u32f_AC4R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_8s32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_8s32f_C1R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_8s32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_8s32f_C3R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_8s32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_8s32f_C4R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_8s32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_8s32f_AC4R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_16u32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_16u32f_C1R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_16u32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_16u32f_C3R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_16u32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_16u32f_C4R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


NppStatus nppiValidNormLevelGetBufferHostSize_16u32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevel_16u32f_AC4R_Ctx.
For common parameter descriptions, see CommonValidNormLevelGetBufferHostSizeParameters.


## Image Cross Correlation Full Norm Level Advanced


### CrossCorrFull_NormLevelAdvanced


Primitives for computing the normalized cross correlation coefficient between two images with full mode with large image template sizes.


CrossCorrFull_NormLevelAdvanced


The functions compute the \(\gamma_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with full mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


The functions require an additional scratch buffer and advanced scratch buffer for computations.


Note: For maximum performance oSrcRoiSize.width + oTplRoiSize.width - 1 MUST be an integer multiple of 4.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_64f_C1R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_64f_C3R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_64f_C4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_8u32f_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_8s32f_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_8s32f_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrFull_NormLevelAdvanced_16u32f_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrFull_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


FullNormLevelGetAdvancedScratchBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the CrossCorrFull_NormLevelAdvanced primitives.


NppStatus nppiCrossCorrFull_NormLevel_GetAdvancedScratchBufferSize(NppiSize oSrcRoiSize, NppiSize oTplRoiSize, int nSizeofDstData, int nSrcChannels, size_t *hpBufferSize)
Buffer size (in bytes) for nppiCrossCorrFull_NormLevelAdvanced functions.

Parameters

oSrcRoiSize – Region-Of-Interest (ROI).
oTplRoiSize – Region-Of-Interest (ROI).
nSizeofDstData – sizeof(destination data type (usually Npp32f)).
nSrcChannels – number of source image color channels.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


## Image Cross Correlation Same Norm Level Advanced


### CrossCorrSame_NormLevelAdvanced


Primitives for computing the normalized cross correlation coefficient between two images with same mode with large image template sizes.


CrossCorrSame_NormLevelAdvanced


The functions compute the \(\gamma_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with same mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


The functions require and additional scratch buffer and advanced scratch buffer for computations.


Note: For maximum performance oSrcRoiSize.width MUST be an integer multiple of 4.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_64f_C1R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_64f_C3R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_64f_C4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_8u32f_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_8s32f_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_8s32f_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrSame_NormLevelAdvanced_16u32f_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrSame_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


SameNormLevelGetAdvancedScratchBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the CrossCorrSame_NormLevelAdvanced primitives.


NppStatus nppiCrossCorrSame_NormLevel_GetAdvancedScratchBufferSize(NppiSize oSrcRoiSize, NppiSize oTplRoiSize, int nSizeofDstData, int nSrcChannels, size_t *hpBufferSize)
Buffer size (in bytes) for nppiCrossCorrSame_NormLevelAdvanced functions.

Parameters

oSrcRoiSize – Region-Of-Interest (ROI).
oTplRoiSize – Region-Of-Interest (ROI).
nSizeofDstData – sizeof(destination data type (usually Npp32f)).
nSrcChannels – number of source image color channels.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


## Image Cross Correlation Valid Norm Level Advanced


### CrossCorrValid_NormLevelAdvanced


Primitives for computing the normalized cross correlation coefficient between two images with valid mode with large template sizes.


CrossCorrValid_NormLevelAdvanced


The functions compute the \(\gamma_{st}(c,r)\) in [General Introduction](image_statistics_functions.html#group__image__proximity_1general_introduction) with valid mode (see [Categorizations](image_statistics_functions.html#group__image__proximity_1category)).


The functions require an additional scratch buffer and advanced scratch buffer for computations.


Note: For maximum performance oSrcRoiSize.width - oTplRoiSize + 1 MUST be an integer multiple of 4.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp32f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_64f_C1R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_64f_C3R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_64f_C4R_Ctx(const Npp64f *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp64f *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp64f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_8u32f_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_8s32f_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_8s32f_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_8s32f_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp8s *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


NppStatus nppiCrossCorrValid_NormLevelAdvanced_16u32f_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcRoiSize, const Npp16u *pTpl, int nTplStep, NppiSize oTplRoiSize, Npp32f *pDst, int nDstStep, Npp8u *pDeviceBuffer, Npp8u *pAdvancedScratchBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image CrossCorrValid_NormLevelAdvanced.
For common parameter descriptions, see Common parameters for nppiSqrDistanceFull functions include:.


ValidNormLevelGetAdvancedScratchBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the CrossCorrValid_NormLevelAdvanced primitives.


NppStatus nppiCrossCorrValid_NormLevel_GetAdvancedScratchBufferSize(NppiSize oSrcRoiSize, NppiSize oTplRoiSize, int nSizeofDstData, int nSrcChannels, size_t *hpBufferSize)
Buffer size (in bytes) for nppiCrossCorrValid_NormLevelAdvanced functions.

Parameters

oSrcRoiSize – Region-Of-Interest (ROI).
oTplRoiSize – Region-Of-Interest (ROI).
nSizeofDstData – sizeof(destination data type (usually Npp32f)).
nSrcChannels – number of source image color channels.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


## Image Quality Index


### Image Quality Index


Primitives for computing the image quality index of two images.


QualityIndex


Given two images \(M\) and \(N\) (both \(W \times H\)), the mathematical formula to calculate the image quality index \(Q\) between them is expressed as:



  \[Q = \frac{4\sigma_{MN}\tilde{M}\tilde{N}}{[(\tilde{M}^2)+(\tilde{N}^2)][(\sigma_M)^2+(\sigma_N)^2]} \] where  \[\tilde{M} = \frac{1}{W\cdot H}\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}M(j,i)\]  \[\tilde{N} = \frac{1}{W\cdot H}\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}N(j,i)\]  \[\sigma_{M} = \sqrt{\frac{1}{W\cdot H-1}\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}[M(j,i)-\tilde{M}]^2}\]  \[\sigma_{N} = \sqrt{\frac{1}{W\cdot H-1}\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}[N(j,i)-\tilde{N}]^2}\]  \[\sigma_{MN} = \frac{1}{W\cdot H-1}\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}[M(j,i)-\tilde{M}][N(j,i)-\tilde{N}]\] The functions require additional scratch buffer for computations.
### Common parameters for nppiQualityIndex functions include:




param pSrc1
Source-Image Pointer.

param nSrc1Step
Source-Image Line Step.

param pSrc2
Source-Image Pointer.

param nSrc2Step
Source-Image Line Step.

param oRoiSize
Region-Of-Interest (ROI).

param pDst
Pointer to the quality index.

param pDeviceBuffer
Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
Image Data Related Error Codes, ROI Related Error Codes, or NPP_QUALITY_INDEX_ERROR if pixels of either image are constant numberse.


NppStatus nppiQualityIndex_8u32f_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oRoiSize, Npp32f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image QualityIndex.
For common parameter descriptions, see Common parameters for nppiQualityIndex functions include:.


NppStatus nppiQualityIndex_16u32f_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oRoiSize, Npp32f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image QualityIndex.
For common parameter descriptions, see Common parameters for nppiQualityIndex functions include:.


NppStatus nppiQualityIndex_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oRoiSize, Npp32f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image QualityIndex.
For common parameter descriptions, see Common parameters for nppiQualityIndex functions include:.


NppStatus nppiQualityIndex_8u32f_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oRoiSize, Npp32f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image QualityIndex.
For common parameter descriptions, see Common parameters for nppiQualityIndex functions include:.


NppStatus nppiQualityIndex_16u32f_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oRoiSize, Npp32f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image QualityIndex.
For common parameter descriptions, see Common parameters for nppiQualityIndex functions include:.


NppStatus nppiQualityIndex_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oRoiSize, Npp32f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image QualityIndex.
For common parameter descriptions, see Common parameters for nppiQualityIndex functions include:.


NppStatus nppiQualityIndex_8u32f_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oRoiSize, Npp32f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image QualityIndex.
For common parameter descriptions, see Common parameters for nppiQualityIndex functions include:.


NppStatus nppiQualityIndex_16u32f_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oRoiSize, Npp32f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image QualityIndex.
For common parameter descriptions, see Common parameters for nppiQualityIndex functions include:.


NppStatus nppiQualityIndex_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oRoiSize, Npp32f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image QualityIndex.
For common parameter descriptions, see Common parameters for nppiQualityIndex functions include:.


QualityIndexGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the QualityIndex primitives.


### CommonQualityIndexGetBufferHostSizeParameters


Common parameters for nppiQualityIndexGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiQualityIndexGetBufferHostSize_8u32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiQualityIndex_8u32f_C1R_Ctx.
For common parameter descriptions, see CommonQualityIndexGetBufferHostSizeParameters.


NppStatus nppiQualityIndexGetBufferHostSize_16u32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiQualityIndex_16u32f_C1R_Ctx.
For common parameter descriptions, see CommonQualityIndexGetBufferHostSizeParameters.


NppStatus nppiQualityIndexGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiQualityIndex_32f_C1R_Ctx.
For common parameter descriptions, see CommonQualityIndexGetBufferHostSizeParameters.


NppStatus nppiQualityIndexGetBufferHostSize_8u32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiQualityIndex_8u32f_C3R_Ctx.
For common parameter descriptions, see CommonQualityIndexGetBufferHostSizeParameters.


NppStatus nppiQualityIndexGetBufferHostSize_16u32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiQualityIndex_16u32f_C3R_Ctx.
For common parameter descriptions, see CommonQualityIndexGetBufferHostSizeParameters.


NppStatus nppiQualityIndexGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiQualityIndex_32f_C3R_Ctx.
For common parameter descriptions, see CommonQualityIndexGetBufferHostSizeParameters.


NppStatus nppiQualityIndexGetBufferHostSize_8u32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiQualityIndex_8u32f_AC4R_Ctx.
For common parameter descriptions, see CommonQualityIndexGetBufferHostSizeParameters.


NppStatus nppiQualityIndexGetBufferHostSize_16u32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiQualityIndex_16u32f_AC4R_Ctx.
For common parameter descriptions, see CommonQualityIndexGetBufferHostSizeParameters.


NppStatus nppiQualityIndexGetBufferHostSize_32f_AC4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size (in bytes) for nppiQualityIndex_32f_AC4R_Ctx.
For common parameter descriptions, see CommonQualityIndexGetBufferHostSizeParameters.


## Image Maximum Error


### MaximumError


Primitives for computing the maximum error between two images. Given two images \(pSrc1\) and \(pSrc2\) both with width \(W\) and height \(H\), the maximum error is defined as the largest absolute difference between pixels of two images. If the image is in complex format, the absolute value of the complex number is provided.


### Common parameters for nppiMaximumError functions include:




param pSrc1
Source-Image Pointer.

param nSrc1Step
Source-Image Line Step.

param pSrc2
Source-Image Pointer.

param nSrc2Step
Source-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pError
Pointer to the computed error.

param pDeviceBuffer
Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes.


MaximumError


NppStatus nppiMaximumError_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_8s_C1R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_16sc_C1R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed complex image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32u_C1R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit unsigned image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit signed image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32sc_C1R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit signed complex image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32fc_C1R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point complex image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_64f_C1R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_8u_C2R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 8-bit unsigned image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_8s_C2R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 8-bit signed image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_16u_C2R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 16-bit unsigned image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_16s_C2R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 16-bit signed image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_16sc_C2R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 16-bit signed complex image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32u_C2R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit unsigned image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32s_C2R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit signed image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32sc_C2R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit signed complex image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32f_C2R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit floating point image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32fc_C2R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit floating point complex image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_64f_C2R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 64-bit floating point image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_8s_C3R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_16s_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_16sc_C3R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed complex image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32u_C3R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit unsigned image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32s_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit signed image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32sc_C3R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit signed complex image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32fc_C3R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point complex image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_64f_C3R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_8s_C4R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_16s_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_16sc_C4R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed complex image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32u_C4R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit unsigned image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32s_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit signed image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32sc_C4R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit signed complex image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_32fc_C4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point complex image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumError_64f_C4R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image Maximum_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


MaximumErrorGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the MaximumError primitives.


### CommonMaximumErrorGetBufferHostSizeParameters


Common parameters for nppiMaximumErrorGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiMaximumErrorGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_8u_C1R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_8s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_8s_C1R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_16u_C1R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_16s_C1R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_16sc_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_16sc_C1R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32u_C1R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32s_C1R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32sc_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32sc_C1R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32f_C1R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32fc_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32fc_C1R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_64f_C1R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_8u_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_8u_C2R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_8s_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_8s_C2R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_16u_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_16u_C2R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_16s_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_16s_C2R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_16sc_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_16sc_C2R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32u_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32u_C2R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32s_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32s_C2R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32sc_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32sc_C2R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32f_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32f_C2R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32fc_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32fc_C2R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_64f_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_64f_C2R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_8u_C3R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_8s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_8s_C3R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_16u_C3R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_16s_C3R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_16sc_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_16sc_C3R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32u_C3R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32s_C3R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32sc_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32sc_C3R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32f_C3R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32fc_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32fc_C3R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_64f_C3R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_8u_C4R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_8s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_8s_C4R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_16u_C4R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_16s_C4R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_16sc_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_16sc_C4R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32u_C4R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32s_C4R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32sc_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32sc_C4R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32f_C4R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_32fc_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_32fc_C4R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumErrorGetBufferHostSize_64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumError_64f_C4R_Ctx.
For common parameter descriptions, see CommonMaximumErrorGetBufferHostSizeParameters.


## Image Average Error


### AverageError


Primitives for computing the average error between two images. Given two images \(pSrc1\) and \(pSrc2\) both with width \(W\) and height \(H\), the average error is defined as:

  \[Average Error = \frac{1}{W\cdot H\cdot N}\sum_{n=0}^{N-1}\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}\left|pSrc1(j,i) - pSrc2(j,i)\right|\] where N stands for the number of channels. If the image is in complex format, the absolute value is used for computation.
AverageError


NppStatus nppiAverageError_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_8s_C1R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_16sc_C1R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed complex image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32u_C1R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit unsigned image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit signed image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32sc_C1R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit signed complex image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32fc_C1R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point complex image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_64f_C1R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_8u_C2R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 8-bit unsigned image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_8s_C2R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 8-bit signed image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_16u_C2R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 16-bit unsigned image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_16s_C2R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 16-bit signed image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_16sc_C2R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 16-bit signed complex image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32u_C2R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit unsigned image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32s_C2R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit signed image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32sc_C2R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit signed complex image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32f_C2R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit floating point image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32fc_C2R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit floating point complex image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_64f_C2R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 64-bit floating point image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_8s_C3R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_16s_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_16sc_C3R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed complex image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32u_C3R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit unsigned image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32s_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit signed image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32sc_C3R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit signed complex image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32fc_C3R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point complex image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_64f_C3R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_8s_C4R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_16s_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_16sc_C4R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed complex image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32u_C4R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit unsigned image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32s_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit signed image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32sc_C4R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit signed complex image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_32fc_C4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point complex image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageError_64f_C4R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image Average_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


AverageErrorGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the NormDiff_Inf primitives.


### CommonAverageErrorGetBufferHostSizeParameters


Common parameters for nppiSumAverageErrorBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiAverageErrorGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_8u_C1R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_8s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_8s_C1R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_16u_C1R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_16s_C1R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_16sc_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_16sc_C1R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32u_C1R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32s_C1R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32sc_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32sc_C1R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32f_C1R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32fc_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32fc_C1R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_64f_C1R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_8u_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_8u_C2R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_8s_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_8s_C2R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_16u_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_16u_C2R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_16s_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_16s_C2R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_16sc_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_16sc_C2R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32u_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32u_C2R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32s_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32s_C2R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32sc_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32sc_C2R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32f_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32f_C2R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32fc_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32fc_C2R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_64f_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_64f_C2R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_8u_C3R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_8s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_8s_C3R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_16u_C3R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_16s_C3R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_16sc_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_16sc_C3R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32u_C3R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32s_C3R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32sc_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32sc_C3R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32f_C3R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32fc_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32fc_C3R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_64f_C3R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_8u_C4R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_8s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_8s_C4R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_16u_C4R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_16s_C4R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_16sc_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_16sc_C4R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32u_C4R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32s_C4R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32sc_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32sc_C4R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32f_C4R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_32fc_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_32fc_C4R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


NppStatus nppiAverageErrorGetBufferHostSize_64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageError_64f_C4R_Ctx.
For common parameter descriptions, see CommonAverageErrorGetBufferHostSizeParameters.


## Image Maximum Relative Error


### MaximumRelativeError


Primitives for computing the maximum relative error between two images. Given two images \(pSrc1\) and \(pSrc2\) both with width \(W\) and height \(H\), the maximum relative error is defined as:

  \[MaximumRelativeError = max{\frac{\left|pSrc1(j,i) - pSrc2(j,i)\right|}{max(\left|pSrc1(j,i)\right|, \left|pSrc2(j,i)\right|)}}\] If the image is in complex format, the absolute value is used for computation. For multiple channles, the maximum relative error of all the channles is returned.
MaximumRelativeError


NppStatus nppiMaximumRelativeError_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_8s_C1R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_16sc_C1R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32u_C1R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32sc_C1R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32fc_C1R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_64f_C1R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_8u_C2R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 8-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_8s_C2R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 8-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_16u_C2R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 16-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_16s_C2R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 16-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_16sc_C2R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 16-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32u_C2R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32s_C2R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32sc_C2R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32f_C2R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32fc_C2R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit floating point complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_64f_C2R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 64-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_8s_C3R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_16s_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_16sc_C3R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32u_C3R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32s_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32sc_C3R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32fc_C3R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_64f_C3R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_8s_C4R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_16s_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_16sc_C4R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32u_C4R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32s_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32sc_C4R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_32fc_C4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiMaximumRelativeError_64f_C4R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


MaximumRelativeErrorGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the NormDiff_Inf primitives.


### CommonMaximumRelativeErrorGetBufferHostSizeParameters


Common parameters for nppiMaximumRelativeErrorGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_8u_C1R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_8s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_8s_C1R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_16u_C1R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_16s_C1R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_16sc_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_16sc_C1R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32u_C1R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32s_C1R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32sc_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32sc_C1R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32f_C1R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32fc_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32fc_C1R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_64f_C1R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_8u_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_8u_C2R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_8s_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_8s_C2R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_16u_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_16u_C2R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_16s_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_16s_C2R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_16sc_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_16sc_C2R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32u_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32u_C2R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32s_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32s_C2R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32sc_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32sc_C2R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32f_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32f_C2R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32fc_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32fc_C2R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_64f_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_64f_C2R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_8u_C3R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_8s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_8s_C3R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_16u_C3R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_16s_C3R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_16sc_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_16sc_C3R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32u_C3R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32s_C3R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32sc_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32sc_C3R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32f_C3R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32fc_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32fc_C3R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_64f_C3R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_8u_C4R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_8s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_8s_C4R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_16u_C4R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_16s_C4R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_16sc_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_16sc_C4R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32u_C4R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32s_C4R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32sc_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32sc_C4R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32f_C4R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_32fc_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_32fc_C4R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiMaximumRelativeErrorGetBufferHostSize_64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMaximumRelativeError_64f_C4R_Ctx.
For common parameter descriptions, see CommonMaximumRelativeErrorGetBufferHostSizeParameters.


## Image Average Relative Error


### AverageRelativeError


Primitives for computing the average relative error between two images. Given two images \(pSrc1\) and \(pSrc2\) both with width \(W\) and height \(H\), the maximum relative error is defined as:

  \[AverageRelativeError = \frac{1}{W\cdot H\cdot N}\sum_{n=0}^{N-1}\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}\frac{\left|pSrc1(j,i) - pSrc2(j,i)\right|}{max(\left|pSrc1(j,i)\right|, \left|pSrc2(j,i)\right|)}\] where N is the number of channels. If the image is in complex format, the absolute value is used for computation.
AverageRelativeError


NppStatus nppiAverageRelativeError_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_8s_C1R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_16sc_C1R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 16-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32u_C1R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32sc_C1R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32fc_C1R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 32-bit floating point complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_64f_C1R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 64-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_8u_C2R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 8-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_8s_C2R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 8-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_16u_C2R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 16-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_16s_C2R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 16-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_16sc_C2R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 16-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32u_C2R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32s_C2R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32sc_C2R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32f_C2R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32fc_C2R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 32-bit floating point complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_64f_C2R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Two-channel 64-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_8s_C3R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_16s_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_16sc_C3R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 16-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32u_C3R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32s_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32sc_C3R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32fc_C3R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating point complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_64f_C3R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 64-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_8s_C4R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 8-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_16s_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_16sc_C4R_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 16-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32u_C4R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit unsigned image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32s_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit signed image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32sc_C4R_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit signed complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_32fc_C4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating point complex image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


NppStatus nppiAverageRelativeError_64f_C4R_Ctx(const Npp64f *pSrc1, int nSrc1Step, const Npp64f *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp64f *pError, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four-channel 64-bit floating point image MaximumRelative_Error.
For common parameter descriptions, see Common parameters for nppiMaximumError functions include:.


AverageRelativeErrorGetBufferHostSize


Companion primitives for computing the device buffer size (in bytes) required by the NormDiff_Inf primitives.


### CommonAverageRelativeErrorGetBufferHostSizeParameters


Common parameters for nppiAverageRelativeErrorGetBufferHostSize functions include:


param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

param nppStreamCtx
Application Managed Stream Context.


return
NPP_NULL_POINTER_ERROR if hpBufferSize is 0 (NULL), ROI Related Error Codes.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_8u_C1R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_8s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_8s_C1R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_16u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_16u_C1R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_16s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_16s_C1R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_16sc_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_16sc_C1R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32u_C1R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32s_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32s_C1R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32sc_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32sc_C1R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32f_C1R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32fc_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32fc_C1R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_64f_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_64f_C1R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_8u_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_8u_C2R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_8s_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_8s_C2R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_16u_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_16u_C2R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_16s_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_16s_C2R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_16sc_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_16sc_C2R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32u_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32u_C2R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32s_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32s_C2R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32sc_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32sc_C2R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32f_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32f_C2R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32fc_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32fc_C2R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_64f_C2R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_64f_C2R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_8u_C3R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_8s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_8s_C3R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_16u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_16u_C3R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_16s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_16s_C3R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_16sc_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_16sc_C3R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32u_C3R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32s_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32s_C3R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32sc_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32sc_C3R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32f_C3R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32fc_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32fc_C3R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_64f_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_64f_C3R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_8u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_8u_C4R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_8s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_8s_C4R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_16u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_16u_C4R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_16s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_16s_C4R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_16sc_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_16sc_C4R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32u_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32u_C4R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32s_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32s_C4R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32sc_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32sc_C4R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32f_C4R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_32fc_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_32fc_C4R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


NppStatus nppiAverageRelativeErrorGetBufferHostSize_64f_C4R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiAverageRelativeError_64f_C4R_Ctx.
For common parameter descriptions, see CommonAverageRelativeErrorGetBufferHostSizeParameters.


## Image Quality Assessment IQA


### IQA


Primitives for computing the image quality between two images, such as MSE, PSNR, SSIM, and MS-SSIM.


MSE


NppStatus nppiMSE_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp32f *pMSE, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image MSE.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pMSE – Device memory pointer to the computed MSE of two images.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMSE_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp32f *pMSE, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image MSE.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pMSE – Device memory pointer to the computed MSE of two images.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


PSNR


NppStatus nppiPSNR_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp32f *pPSNR, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image PSNR_Ctx.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pPSNR – Device memory pointer to the computed PSNR of two images.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiPSNR_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp32f *pPSNR, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image PSNR_Ctx.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pPSNR – Device memory pointer to the computed PSNR of two images.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


SSIM


NppStatus nppiSSIM_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp32f *pSSIM, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image SSIM.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pSSIM – Device memory pointer to the computed SSIM of two images.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSSIM_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp32f *pSSIM, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image SSIM.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pSSIM – Device memory pointer to the computed SSIM of two images.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


MSSSIM


NppStatus nppiMSSSIM_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp32f *pMSSSIM, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image MS-SSIM*.
This function will be deprecated in a future release use the nppiWMSSSIM functions instead.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pMSSSIM – Device memory pointer to the computed MS-SSIM of two images.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


WMSSSIM


NppStatus nppiWMSSSIM_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp32f *pMSSSIM, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
One-channel 8-bit unsigned image MS-SSIM*.
This function uses the algorithm described in the paper by Wang et. al. Wang, Z., Simoncelli, E.P., Bovik, A.C. Multiscale Structural Similarity for Image Quality Assessment. In: The Thirty-Seventh Asilomar Conference on Signals, Systems & Computers, 2003, 13981402. Pacific Grove, CA, USA: IEEE,

https://doi.org/10.1109/ACSSC.2003.1292216. NOTE: this API call can only process oSizeROI dimensions 16px by 16px and above. Any oSizeROI dimensions less than 16px by 16px will result in undefined behaviour.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pMSSSIM – Device memory pointer to the computed MS-SSIM of two images.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiWMSSSIM_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, NppiSize oSizeROI, Npp32f *pMSSSIM, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned image MS-SSIM*.
This function uses the algorithm described in the paper by Wang et. al. Wang, Z., Simoncelli, E.P., Bovik, A.C. Multiscale Structural Similarity for Image Quality Assessment. In: The Thirty-Seventh Asilomar Conference on Signals, Systems & Computers, 2003, 13981402. Pacific Grove, CA, USA: IEEE,

https://doi.org/10.1109/ACSSC.2003.1292216. NOTE: this API call can only process oSizeROI dimensions 16px by 16px and above. Any oSizeROI dimensions less than 16px by 16px will result in undefined behaviour.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pMSSSIM – Device memory pointer to the computed MS-SSIM of two images.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


MSEGetBufferHostSize


NppStatus nppiMSEGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMSE_8u_C1R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiMSEGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMSE_8u_C3R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiPSNRGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiPSNR_8u_C1R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiPSNRGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiPSNR_8u_C3R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiSSIMGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSSIM_8u_C1R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiSSIMGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiSSIM_8u_C3R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiMSSSIMGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiMSSSIM_8u_C1R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiWMSSSIMGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiWMSSSIM_8u_C1R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiWMSSSIMGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for nppiWMSSSIM_8u_C3R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


## Image Batch Quality Assessment


### IQABatch


Primitives for computing the image quality for a batch of image pairs, such as MSE, PSNR, SSIM, and MS-SSIM with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input images


MSEBatch


NppStatus nppiMSEBatch_8u_C1R_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oSizeROI, Npp32f *pMSE, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned MSE for a batch of image pairs for a single ROI.
Provided oSizeROI will be used for all images passed in pSrc1BatchList and pSrc2BatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI) ROI width and height of ALL images in the batch, MUST match the ROI used when the label markers UF image was generated.
pMSE – Device memory pointer to output array of the computed MSE for nBatchSize * sizeof(Npp32f) * 1 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiMSEBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiMSEBatch_8u_C3R_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oSizeROI, Npp32f *pMSE, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned MSE for a batch of image pairs for a single ROI.
Provided oSizeROI will be used for all images passed in pSrc1BatchList and pSrc2BatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI) ROI width and height of ALL images in the batch, MUST match the ROI used when the label markers UF image was generated.
pMSE – Device memory pointer to output array of the computed MSE for nBatchSize * sizeof(Npp32f) * 3 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiMSEBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


PSNRBatch


NppStatus nppiPSNRBatch_8u_C1R_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oSizeROI, Npp32f *pPSNR, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned PSNR for a batch of image pairs for a single ROI.
Provided oSizeROI will be used for all images passed in pSrc1BatchList and pSrc2BatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI) ROI width and height of ALL images in the batch, MUST match the ROI used when the label markers UF image was generated.
pPSNR – Device memory pointer to output array of the computed PSNR for nBatchSize * sizeof(Npp32f) * 1 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiPSNRBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiPSNRBatch_8u_C3R_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oSizeROI, Npp32f *pPSNR, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned PSNR for a batch of image pairs for a single ROI.
Provided oSizeROI will be used for all images passed in pSrc1BatchList and pSrc2BatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI) ROI width and height of ALL images in the batch, MUST match the ROI used when the label markers UF image was generated.
pPSNR – Device memory pointer to output array of the computed PSNR for nBatchSize * sizeof(Npp32f) * 3 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiPSNRBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


SSIMBatch


NppStatus nppiSSIMBatch_8u_C1R_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oSizeROI, Npp32f *pSSIM, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned SSIM for a batch of image pairs for a single ROI.
Provided oSizeROI will be used for all images passed in pSrc1BatchList and pSrc2BatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI) ROI width and height of ALL images in the batch, MUST match the ROI used when the label markers UF image was generated.
pSSIM – Device memory pointer to output array of the computed SSIM for nBatchSize * sizeof(Npp32f) * 1 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiSSIMBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSSIMBatch_8u_C3R_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oSizeROI, Npp32f *pSSIM, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned SSIM for a batch of image pairs for a single ROI.
Provided oSizeROI will be used for all images passed in pSrc1BatchList and pSrc2BatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI) ROI width and height of ALL images in the batch, MUST match the ROI used when the label markers UF image was generated.
pSSIM – Device memory pointer to output array of the computed SSIM for nBatchSize * sizeof(Npp32f) * 3 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiSSIMBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


WMSSSIMBatch


NppStatus nppiWMSSSIMBatch_8u_C1R_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oSizeROI, Npp32f *pWMSSSIM, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned WMSSSIM for a batch of image pairs for a single ROI.
Provided oSizeROI will be used for all images passed in pSrc1BatchList and pSrc2BatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images. NOTE: this API call can only process oSizeROI dimensions 16 pixels by 16 pixels and above. Any oSizeROI dimensions less than 16 pixels by 16 pixels will result in undefined behaviour.

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI) ROI width and height of ALL images in the batch, MUST match the ROI used when the label markers UF image was generated.
pWMSSSIM – Device memory pointer to output array of the computed WMSSSIM for nBatchSize * sizeof(Npp32f) * 1 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiWMSSSIMBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiWMSSSIMBatch_8u_C3R_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oSizeROI, Npp32f *pWMSSSIM, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned WMSSSIM for a batch of image pairs for a single ROI.
Provided oSizeROI will be used for all images passed in pSrc1BatchList and pSrc2BatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images. NOTE: this API call can only process ROI dimensions 16 pixels by 16 pixels and above. Any ROI dimensions less than 16 pixels by 16 pixels will result in undefined behaviour.

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors, per image oSize must be initialized.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI) ROI width and height of ALL images in the batch, MUST match the ROI used when the label markers UF image was generated.
pWMSSSIM – Device memory pointer to output array of the computed WMSSSIM for nBatchSize * sizeof(Npp32f) * 3 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiWMSSSIMBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


MSEBatchGetBufferHostSize


NppStatus nppiMSEBatchGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for a single image pair in the batch of image pairs for nppiMSEBatch_8u_C1R_Ctx For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiMSEBatchGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for a single image pair in the batch of image pairs for nppiMSEBatch_8u_C3R_Ctx For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiPSNRBatchGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for a single image pair in the batch of image pairs for nppiPSNRBatch_8u_C1R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiPSNRBatchGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for a single image pair in the batch of image pairs for nppiPSNRBatch_8u_C3R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiSSIMBatchGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for a single image pair in the batch of image pairs for nppiSSIMBatch_8u_C1R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiSSIMBatchGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for a single image pair in the batch of image pairs for nppiSSIMBatch_8u_C3R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiWMSSSIMBatchGetBufferHostSize_8u_C1R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for a single image pair in the batch of image pairs for nppiWMSSSIMBatch_8u_C1R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


NppStatus nppiWMSSSIMBatchGetBufferHostSize_8u_C3R_Ctx(NppiSize oSizeROI, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Buffer size for a single image pair in the batch of image pairs for nppiWMSSSIMBatch_8u_C3R_Ctx.
For common parameter descriptions, see CommonGetBufferHostSizeParameters.


## Image Advanced Batch Quality Assessment


### IQABatchAdvanced


Primitives for computing the image quality for a batch of image pairs, such as MSE, PSNR, SSIM, and MS-SSIM with per-image [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification)


MSEBatchAdvanced


NppStatus nppiMSEBatch_8u_C1R_Advanced_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oMaxSizeROI, Npp32f *pMSE, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned MSE for a batch of image pairs with per-image ROI

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI) maximum ROI width and height of ALL images in the batch.
pMSE – Device memory pointer to output array of the computed MSE for nBatchSize * sizeof(Npp32f * 1 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiMSEBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiMSEBatch_8u_C3R_Advanced_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oMaxSizeROI, Npp32f *pMSE, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned MSE for a batch of image pairs with per-image ROI

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI) maximum ROI width and height of ALL images in the batch.
pMSE – Device memory pointer to output array of the computed MSE for nBatchSize * sizeof(Npp32f) * 3 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiMSEBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


PSNRBatchAdvanced


NppStatus nppiPSNRBatch_8u_C1R_Advanced_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oMaxSizeROI, Npp32f *pPSNR, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned PSNR for a batch of image pairs with per-image ROI

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI) maximum ROI width and height of ALL images in the batch.
pPSNR – Device memory pointer to output array of the computed PSNR for nBatchSize * sizeof(Npp32f) * 1 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiPSNRBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiPSNRBatch_8u_C3R_Advanced_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oMaxSizeROI, Npp32f *pPSNR, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned PSNR for a batch of image pairs with per-image ROI

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI) maximum ROI width and height of ALL images in the batch.
pPSNR – Device memory pointer to output array of the computed PSNR for nBatchSize * sizeof(Npp32f) * 3 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiPSNRBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


WMSSSIMBatchAdvanced


NppStatus nppiWMSSSIMBatch_8u_C1R_Advanced_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oMaxSizeROI, Npp32f *pWMSSSIM, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned WMSSSIM for a batch of image pairs with per-image ROI NOTE: It is the user’s responsibility to make sure the dimensions of per-image ROIs are 16 pixels by 16 pixels and above.
Any per-image ROI dimensions less than 16 pixels by 16 pixels will result in undefined behaviour.

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI) maximum ROI width and height of ALL images in the batch.
pWMSSSIM – Device memory pointer to output array of the computed WMSSSIM for nBatchSize * sizeof(Npp32f) * 1 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiWMSSSIMBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiWMSSSIMBatch_8u_C3R_Advanced_Ctx(const NppiImageDescriptor *pSrc1BatchList, const NppiImageDescriptor *pSrc2BatchList, int nBatchSize, NppiSize oMaxSizeROI, Npp32f *pWMSSSIM, NppiBufferDescriptor *pDeviceBufferList, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned WMSSSIM for a batch of image pairs with per-image ROI NOTE: It is the user’s responsibility to make sure the dimensions of per-image ROIs are 16 pixels by 16 pixels and above.
Any per-image ROI dimensions less than 16 pixels by 16 pixels will result in undefined behaviour.

Parameters

pSrc1BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors.
pSrc2BatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory image descriptors.
nBatchSize – Number of NppiImageDescriptor, NppiBufferDescriptor, and new max number structures/values processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI) maximum ROI width and height of ALL images in the batch.
pWMSSSIM – Device memory pointer to output array of the computed WMSSSIM for nBatchSize * sizeof(Npp32f) * 3 image pairs.
pDeviceBufferList – Device memory pointer to the list of NppiBufferDescriptor buffer descriptors specifying per image device memory buffer pointers and size as returned by at least one nppiWMSSSIMBatchGetBufferHostSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes