# Image Morphological Operations — npp 13.1 documentation

>


# Image Morphological Operations


Morphological image operations.


Morphological operations are classified as [Neighborhood Operations](introduction.html#nppi_conventions_lb_1neighborhood_operations).


These functions can be found in the nppim library. Linking to only the sub-libraries that you use can significantly save link time, application load time, and CUDA runtime startup time when using dynamic libraries.


## Dilation Functions


### Image Dilate


#### Dilation


Dilation computes the output pixel as the maximum pixel value of the pixels under the mask. Pixels who’s corresponding mask values are zero do not participate in the maximum search.


It is the user’s responsibility to avoid [Sampling Beyond Image Boundaries](introduction.html#nppi_conventions_lb_1sampling_beyond_image_boundaries).


##### Common parameters for nppiDilate functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMask
Pointer to the start address of the mask array

param oMaskSize
Width and Height mask array.

param oAnchor
X and Y offsets of the mask origin frame of reference w.r.t the source pixel.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiDilate_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single-channel 8-bit unsigned integer dilation.
For common parameter descriptions, see Common parameters for nppiDilate functions:.


NppStatus nppiDilate_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned integer dilation.
For common parameter descriptions, see Common parameters for nppiDilate functions:.


NppStatus nppiDilate_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer dilation.
For common parameter descriptions, see Common parameters for nppiDilate functions:.


NppStatus nppiDilate_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer dilation, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiDilate functions:.


NppStatus nppiDilate_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single-channel 16-bit unsigned integer dilation.
For common parameter descriptions, see Common parameters for nppiDilate functions:.


NppStatus nppiDilate_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned integer dilation.
For common parameter descriptions, see Common parameters for nppiDilate functions:.


NppStatus nppiDilate_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer dilation.
For common parameter descriptions, see Common parameters for nppiDilate functions:.


NppStatus nppiDilate_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer dilation, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiDilate functions:.


NppStatus nppiDilate_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single-channel 32-bit floating-point dilation.
For common parameter descriptions, see Common parameters for nppiDilate functions:.


NppStatus nppiDilate_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating-point dilation.
For common parameter descriptions, see Common parameters for nppiDilate functions:.


NppStatus nppiDilate_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point dilation.
For common parameter descriptions, see Common parameters for nppiDilate functions:.


NppStatus nppiDilate_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point dilation, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiDilate functions:.


### Image Dilate Border


#### Dilation with border control


Dilation computes the output pixel as the maximum pixel value of the pixels under the mask. Pixels who’s corresponding mask values are zero do not participate in the maximum search. For gray scale dilation the mask contains signed mask values which are added to the corresponding source image sample value before determining the maximun value after clamping.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiDilateBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
Source image starting point relative to pSrc.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMask
Pointer to the start address of the mask array

param oMaskSize
Width and Height mask array.

param oAnchor
X and Y offsets of the mask origin frame of reference w.r.t the source pixel.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiDilateBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 8-bit unsigned integer dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiDilateBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned integer dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiDilateBorder_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiDilateBorder_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer dilation with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiDilateBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 16-bit unsigned integer dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiDilateBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned integer dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiDilateBorder_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiDilateBorder_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer dilation with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiDilateBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 32-bit floating-point dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiDilateBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating-point dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiDilateBorder_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiDilateBorder_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point dilation with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiGrayDilateBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 8-bit unsigned integer gray scale dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


NppStatus nppiGrayDilateBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 32-bit floating point gray scale dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilateBorder functions:.


### Image Dilate 3x3


#### Dilate3x3


Dilation using a 3x3 mask with the anchor at its center pixel.


It is the user’s responsibility to avoid [Sampling Beyond Image Boundaries](introduction.html#nppi_conventions_lb_1sampling_beyond_image_boundaries).


##### Common parameters for nppiDilate3x3 functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiDilate3x3_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single-channel 8-bit unsigned integer 3x3 dilation.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


NppStatus nppiDilate3x3_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned integer 3x3 dilation.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


NppStatus nppiDilate3x3_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer 3x3 dilation.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


NppStatus nppiDilate3x3_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer 3x3 dilation, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


NppStatus nppiDilate3x3_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single-channel 16-bit unsigned integer 3x3 dilation.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


NppStatus nppiDilate3x3_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned integer 3x3 dilation.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


NppStatus nppiDilate3x3_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer 3x3 dilation.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


NppStatus nppiDilate3x3_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer 3x3 dilation, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


NppStatus nppiDilate3x3_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single-channel 32-bit floating-point 3x3 dilation.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


NppStatus nppiDilate3x3_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating-point 3x3 dilation.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


NppStatus nppiDilate3x3_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point 3x3 dilation.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


NppStatus nppiDilate3x3_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point 3x3 dilation, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


NppStatus nppiDilate3x3_64f_C1R_Ctx(const Npp64f *pSrc, Npp32s nSrcStep, Npp64f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single-channel 64-bit floating-point 3x3 dilation.
For common parameter descriptions, see Common parameters for nppiDilate3x3 functions:.


### Image Dilate 3x3 Border


#### Dilate3x3Border


Dilation using a 3x3 mask with the anchor at its center pixel with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiDilate3x3Border functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
Source image starting point relative to pSrc.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiDilate3x3Border_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 8-bit unsigned integer 3x3 dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilate3x3Border functions:.


NppStatus nppiDilate3x3Border_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned integer 3x3 dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilate3x3Border functions:.


NppStatus nppiDilate3x3Border_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer 3x3 dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilate3x3Border functions:.


NppStatus nppiDilate3x3Border_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer 3x3 dilation with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiDilate3x3Border functions:.


NppStatus nppiDilate3x3Border_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 16-bit unsigned integer 3x3 dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilate3x3Border functions:.


NppStatus nppiDilate3x3Border_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned integer 3x3 dilation with border control.


NppStatus nppiDilate3x3Border_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer 3x3 dilation with border control.


NppStatus nppiDilate3x3Border_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer 3x3 dilation with border control, ignoring alpha-channel.


NppStatus nppiDilate3x3Border_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 32-bit floating-point 3x3 dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilate3x3Border functions:.


NppStatus nppiDilate3x3Border_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating-point 3x3 dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilate3x3Border functions:.


NppStatus nppiDilate3x3Border_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point 3x3 dilation with border control.
For common parameter descriptions, see Common parameters for nppiDilate3x3Border functions:.


NppStatus nppiDilate3x3Border_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point 3x3 dilation with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiDilate3x3Border functions:.


## Erosion Functions


### Image Erode


#### Erode


Erosion computes the output pixel as the minimum pixel value of the pixels under the mask. Pixels who’s corresponding mask values are zero do not participate in the maximum search.


It is the user’s responsibility to avoid [Sampling Beyond Image Boundaries](introduction.html#nppi_conventions_lb_1sampling_beyond_image_boundaries).


##### Common parameters for nppiErode functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMask
Pointer to the start address of the mask array

param oMaskSize
Width and Height mask array.

param oAnchor
X and Y offsets of the mask origin frame of reference w.r.t the source pixel.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiErode_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single-channel 8-bit unsigned integer erosion.
For common parameter descriptions, see Common parameters for nppiErode functions:.


NppStatus nppiErode_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned integer erosion.
For common parameter descriptions, see Common parameters for nppiErode functions:.


NppStatus nppiErode_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer erosion.
For common parameter descriptions, see Common parameters for nppiErode functions:.


NppStatus nppiErode_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer erosion, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiErode functions:.


NppStatus nppiErode_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single-channel 16-bit unsigned integer erosion.
For common parameter descriptions, see Common parameters for nppiErode functions:.


NppStatus nppiErode_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned integer erosion.


NppStatus nppiErode_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer erosion.
For common parameter descriptions, see Common parameters for nppiErode functions:.


NppStatus nppiErode_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer erosion, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiErode functions:.


NppStatus nppiErode_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single-channel 32-bit floating-point erosion.
For common parameter descriptions, see Common parameters for nppiErode functions:.


NppStatus nppiErode_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating-point erosion.
For common parameter descriptions, see Common parameters for nppiErode functions:.


NppStatus nppiErode_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point erosion.
For common parameter descriptions, see Common parameters for nppiErode functions:.


NppStatus nppiErode_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point erosion, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiErode functions:.


### Image Erode Border


#### Erosion with border control


Erosion computes the output pixel as the minimum pixel value of the pixels under the mask. Pixels who’s corresponding mask values are zero do not participate in the minimum search. For gray scale erosion the mask contains signed mask values which are added to the corresponding source image sample value before determining the minimum value after clamping.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiErodeBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
Source image starting point relative to pSrc.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMask
Pointer to the start address of the mask array

param oMaskSize
Width and Height mask array.

param oAnchor
X and Y offsets of the mask origin frame of reference w.r.t the source pixel.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiErodeBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 8-bit unsigned integer erosion with border control.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiErodeBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned integer erosion with border control.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiErodeBorder_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer erosion with border control.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiErodeBorder_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer erosion with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiErodeBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 16-bit unsigned integer erosion with border control.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiErodeBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned integer erosion with border control.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiErodeBorder_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer erosion with border control.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiErodeBorder_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer erosion with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiErodeBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 32-bit floating-point erosion with border control.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiErodeBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating-point erosion with border control.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiErodeBorder_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point erosion with border control.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiErodeBorder_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point erosion with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiGrayErodeBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 8-bit unsigned integer gray scale erosion with border control.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


NppStatus nppiGrayErodeBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pMask, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 32-bit floating point gray scale erosion with border control.
For common parameter descriptions, see Common parameters for nppiErodeBorder functions:.


### Image Erode 3x3


#### Erode3x3


Erosion using a 3x3 mask with the anchor at its center pixel.


It is the user’s responsibility to avoid [Sampling Beyond Image Boundaries](introduction.html#nppi_conventions_lb_1sampling_beyond_image_boundaries).


##### Common parameters for nppiErode3x3 functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiErode3x3_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single-channel 8-bit unsigned integer 3x3 erosion.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


NppStatus nppiErode3x3_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned integer 3x3 erosion.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


NppStatus nppiErode3x3_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer 3x3 erosion.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


NppStatus nppiErode3x3_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer 3x3 erosion, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


NppStatus nppiErode3x3_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single-channel 16-bit unsigned integer 3x3 erosion.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


NppStatus nppiErode3x3_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned integer 3x3 erosion.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


NppStatus nppiErode3x3_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer 3x3 erosion.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


NppStatus nppiErode3x3_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer 3x3 erosion, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


NppStatus nppiErode3x3_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single-channel 32-bit floating-point 3x3 erosion.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


NppStatus nppiErode3x3_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating-point 3x3 erosion.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


NppStatus nppiErode3x3_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point 3x3 erosion.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


NppStatus nppiErode3x3_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point 3x3 erosion, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


NppStatus nppiErode3x3_64f_C1R_Ctx(const Npp64f *pSrc, Npp32s nSrcStep, Npp64f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single-channel 64-bit floating-point 3x3 erosion.
For common parameter descriptions, see Common parameters for nppiErode3x3 functions:.


### Image Erode 3x3 Border


#### Erode3x3Border


Erosion using a 3x3 mask with the anchor at its center pixel with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiErode3x3Border functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
Source image starting point relative to pSrc.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiErode3x3Border_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 8-bit unsigned integer 3x3 erosion with border control.
For common parameter descriptions, see Common parameters for nppiErode3x3Border functions:.


NppStatus nppiErode3x3Border_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three-channel 8-bit unsigned integer 3x3 erosion with border control.
For common parameter descriptions, see Common parameters for nppiErode3x3Border functions:.


NppStatus nppiErode3x3Border_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer 3x3 erosion with border control.
For common parameter descriptions, see Common parameters for nppiErode3x3Border functions:.


NppStatus nppiErode3x3Border_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 8-bit unsigned integer 3x3 erosion with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiErode3x3Border functions:.


NppStatus nppiErode3x3Border_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 16-bit unsigned integer 3x3 erosion with border control.
For common parameter descriptions, see Common parameters for nppiErode3x3Border functions:.


NppStatus nppiErode3x3Border_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three-channel 16-bit unsigned integer 3x3 erosion with border control.
For common parameter descriptions, see Common parameters for nppiErode3x3Border functions:.


NppStatus nppiErode3x3Border_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer 3x3 erosion with border control.
For common parameter descriptions, see Common parameters for nppiErode3x3Border functions:.


NppStatus nppiErode3x3Border_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 16-bit unsigned integer 3x3 erosion with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiErode3x3Border functions:.


NppStatus nppiErode3x3Border_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single-channel 32-bit floating-point 3x3 erosion with border control.
For common parameter descriptions, see Common parameters for nppiErode3x3Border functions:.


NppStatus nppiErode3x3Border_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three-channel 32-bit floating-point 3x3 erosion with border control.
For common parameter descriptions, see Common parameters for nppiErode3x3Border functions:.


NppStatus nppiErode3x3Border_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point 3x3 erosion with border control.
For common parameter descriptions, see Common parameters for nppiErode3x3Border functions:.


NppStatus nppiErode3x3Border_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four-channel 32-bit floating-point 3x3 erosion with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiErode3x3Border functions:.


## Image Complex Morphphological Operations


### Image Morph


#### ComplexImageMorphology


Complex image morphological operations.


### Image Morph Get Buffer Size


#### MorphGetBufferSize


Before calling any of the MorphCloseBorder, MorphOpenBorder, MorphTopHatBorder, MorphBlackHatBorder, or MorphGradientBorder functions the application first needs to call the corresponding MorphGetBufferSize to determine the amount of device memory to allocate as a working buffer. The application allocated device memory is then passed as the pBuffer parameter to the corresponding MorphXXXBorder function.


##### Common parameters for nppiMorphGetBufferSize functions:




param oSizeROI
Region-Of-Interest (ROI).

param hpBufferSize
Required buffer size in bytes.


Functions


NppStatus nppiMorphGetBufferSize_8u_C1R(NppiSize oSizeROI, int *hpBufferSize)
Calculate scratch buffer size needed for 1 channel 8-bit unsigned integer MorphCloseBorder, MorphOpenBorder, MorphTopHatBorder, MorphBlackHatBorder, or MorphGradientBorder function based on destination image oSizeROI width and height.
For common parameter descriptions, see Common parameters for nppiMorphGetBufferSize functions:.


NppStatus nppiMorphGetBufferSize_8u_C3R(NppiSize oSizeROI, int *hpBufferSize)
Calculate scratch buffer size needed for 3 channel 8-bit unsigned integer MorphCloseBorder, MorphOpenBorder, MorphTopHatBorder, MorphBlackHatBorder or MorphGradientBorder function based on destination image oSizeROI width and height.
For common parameter descriptions, see Common parameters for nppiMorphGetBufferSize functions:.


NppStatus nppiMorphGetBufferSize_8u_C4R(NppiSize oSizeROI, int *hpBufferSize)
Calculate scratch buffer size needed for 4 channel 8-bit unsigned integer MorphCloseBorder, MorphOpenBorder, MorphTopHatBorder, MorphBlackHatBorder, or MorphGradientBorder function based on destination image oSizeROI width and height.
For common parameter descriptions, see Common parameters for nppiMorphGetBufferSize functions:.


NppStatus nppiMorphGetBufferSize_16u_C1R(NppiSize oSizeROI, int *hpBufferSize)
Calculate scratch buffer size needed for 1 channel 16-bit unsigned integer MorphCloseBorder, MorphOpenBorder, MorphTopHatBorder, MorphBlackHatBorder, or MorphGradientBorder function based on destination image oSizeROI width and height.
For common parameter descriptions, see Common parameters for nppiMorphGetBufferSize functions:.


NppStatus nppiMorphGetBufferSize_16s_C1R(NppiSize oSizeROI, int *hpBufferSize)
Calculate scratch buffer size needed for 1 channel 16-bit signed integer MorphCloseBorder, MorphOpenBorder, MorphTopHatBorder, MorphBlackHatBorder, or MorphGradientBorder function based on destination image oSizeROI width and height.
For common parameter descriptions, see Common parameters for nppiMorphGetBufferSize functions:.


NppStatus nppiMorphGetBufferSize_32f_C1R(NppiSize oSizeROI, int *hpBufferSize)
Calculate scratch buffer size needed for 1 channel 32-bit floating point MorphCloseBorder, MorphOpenBorder, MorphTopHatBorder, MorphBlackHatBorder, or MorphGradientBorder function based on destination image oSizeROI width and height.
For common parameter descriptions, see Common parameters for nppiMorphGetBufferSize functions:.


NppStatus nppiMorphGetBufferSize_32f_C3R(NppiSize oSizeROI, int *hpBufferSize)
Calculate scratch buffer size needed for 3 channel 32-bit floating point MorphCloseBorder, MorphOpenBorder, MorphTopHatBorder, MorphBlackHatBorder, or MorphGradientBorder function based on destination image oSizeROI width and height.
For common parameter descriptions, see Common parameters for nppiMorphGetBufferSize functions:.


NppStatus nppiMorphGetBufferSize_32f_C4R(NppiSize oSizeROI, int *hpBufferSize)
Calculate scratch buffer size needed for 4 channel 32-bit floating point MorphCloseBorder, MorphOpenBorder, MorphTopHatBorder, MorphBlackHatBorder, or MorphGradientBorder function based on destination image oSizeROI width and height.
For common parameter descriptions, see Common parameters for nppiMorphGetBufferSize functions:.


### Image Morph Close Border


#### MorphCloseBorder


Dilation followed by Erosion with border control.


Morphological close computes the output pixel as the maximum pixel value of the pixels under the mask followed by a second pass using the result of the first pass as input which outputs the minimum pixel value of the pixels under the same mask. Pixels who’s corresponding mask values are zero do not participate in the maximum or minimum search.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image. The mask is centered over the source image pixel being tested.


Before calling any of the MorphCloseBorder functions the application first needs to call the corresponding MorphGetBufferSize to determine the amount of device memory to allocate as a working buffer. The allocated device memory is then passed as the pBuffer parameter to the corresponding MorphCloseBorder function.


Use the oSrcOffset and oSrcSize parameters to control where the border control operation is applied to the source image ROI borders.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiMorphCloseBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
Source image starting point relative to pSrc.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMask
Pointer to the start address of the mask array

param oMaskSize
Width and Height mask array.

param oAnchor
X and Y offsets of the mask origin frame of reference w.r.t the source pixel.

param pBuffer
Pointer to device memory scratch buffer at least as large as value returned by the corresponding MorphGetBufferSize call.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiMorphCloseBorder_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer morphological close with border control.
For common parameter descriptions, see Common parameters for nppiMorphCloseBorder functions:.


NppStatus nppiMorphCloseBorder_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer morphological close with border control.
For common parameter descriptions, see Common parameters for nppiMorphCloseBorder functions:.


NppStatus nppiMorphCloseBorder_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned integer morphological close with border control.
For common parameter descriptions, see Common parameters for nppiMorphCloseBorder functions:.


NppStatus nppiMorphCloseBorder_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned integer morphological close with border control.
For common parameter descriptions, see Common parameters for nppiMorphCloseBorder functions:.


NppStatus nppiMorphCloseBorder_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit signed integer morphological close with border control.
For common parameter descriptions, see Common parameters for nppiMorphCloseBorder functions:.


NppStatus nppiMorphCloseBorder_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point morphological close with border control.
For common parameter descriptions, see Common parameters for nppiMorphCloseBorder functions:.


NppStatus nppiMorphCloseBorder_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point morphological close with border control.
For common parameter descriptions, see Common parameters for nppiMorphCloseBorder functions:.


NppStatus nppiMorphCloseBorder_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point morphological close with border control.
For common parameter descriptions, see Common parameters for nppiMorphCloseBorder functions:.


### Image Morph Open Border


#### MorphOpenBorder


Erosion followed by Dilation with border control.


Morphological open computes the output pixel as the minimum pixel value of the pixels under the mask followed by a second pass using the result of the first pass as input which outputs the maximum pixel value of the pixels under the same mask. Pixels who’s corresponding mask values are zero do not participate in the minimum or maximum search.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image. The mask is centered over the source image pixel being tested.


Before calling any of the MorphOpenBorder functions the application first needs to call the corresponding MorphGetBufferSize to determine the amount of device memory to allocate as a working buffer. The allocated device memory is then passed as the pBuffer parameter to the corresponding MorphOpenBorder function.


Use the oSrcOffset and oSrcSize parameters to control where the border control operation is applied to the source image ROI borders.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiMorphOpenBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
Source image starting point relative to pSrc.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMask
Pointer to the start address of the mask array

param oMaskSize
Width and Height mask array.

param oAnchor
X and Y offsets of the mask origin frame of reference w.r.t the source pixel.

param pBuffer
Pointer to device memory scratch buffer at least as large as value returned by the corresponding MorphGetBufferSize call.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiMorphOpenBorder_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer morphological open with border control.
For common parameter descriptions, see Common parameters for nppiMorphOpenBorder functions:.


NppStatus nppiMorphOpenBorder_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer morphological open with border control.
For common parameter descriptions, see Common parameters for nppiMorphOpenBorder functions:.


NppStatus nppiMorphOpenBorder_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned integer morphological open with border control.
For common parameter descriptions, see Common parameters for nppiMorphOpenBorder functions:.


NppStatus nppiMorphOpenBorder_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned integer morphological open with border control.
For common parameter descriptions, see Common parameters for nppiMorphOpenBorder functions:.


NppStatus nppiMorphOpenBorder_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit signed integer morphological open with border control.
For common parameter descriptions, see Common parameters for nppiMorphOpenBorder functions:.


NppStatus nppiMorphOpenBorder_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point morphological open with border control.
For common parameter descriptions, see Common parameters for nppiMorphOpenBorder functions:.


NppStatus nppiMorphOpenBorder_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point morphological open with border control.
For common parameter descriptions, see Common parameters for nppiMorphOpenBorder functions:.


NppStatus nppiMorphOpenBorder_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point morphological open with border control.
For common parameter descriptions, see Common parameters for nppiMorphOpenBorder functions:.


### Image Morph Top Hat Border


#### MorphToHatBorder


Source pixel minus the morphological open pixel result with border control.


Morphological top hat computes the output pixel as the source pixel minus the morphological open result of the pixels under the mask. Pixels who’s corresponding mask values are zero do not participate in the maximum or minimum search.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image. The mask is centered over the source image pixel being tested.


Before calling any of the MorphTopHatBorder functions the application first needs to call the corresponding MorphGetBufferSize to determine the amount of device memory to allocate as a working buffer. The allocated device memory is then passed as the pBuffer parameter to the corresponding MorphTopHatBorder function.


Use the oSrcOffset and oSrcSize parameters to control where the border control operation is applied to the source image ROI borders.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiMorphTopHatBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
Source image starting point relative to pSrc.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMask
Pointer to the start address of the mask array

param oMaskSize
Width and Height mask array.

param oAnchor
X and Y offsets of the mask origin frame of reference w.r.t the source pixel.

param pBuffer
Pointer to device memory scratch buffer at least as large as value returned by the corresponding MorphGetBufferSize call.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiMorphTopHatBorder_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer morphological top hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphTopHatBorder functions:.


NppStatus nppiMorphTopHatBorder_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer morphological top hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphTopHatBorder functions:.


NppStatus nppiMorphTopHatBorder_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned integer morphological top hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphTopHatBorder functions:.


NppStatus nppiMorphTopHatBorder_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned integer morphological top hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphTopHatBorder functions:.


NppStatus nppiMorphTopHatBorder_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit signed integer morphological top hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphTopHatBorder functions:.


NppStatus nppiMorphTopHatBorder_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point morphological top hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphTopHatBorder functions:.


NppStatus nppiMorphTopHatBorder_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point morphological top hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphTopHatBorder functions:.


NppStatus nppiMorphTopHatBorder_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point morphological top hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphTopHatBorder functions:.


### Image Morph Black Hat Border


#### MorphBlackHatBorder


Morphological close pixel result minus source pixel with border control.


Morphological black hat computes the output pixel as the morphological close pixel value of the pixels under the mask minus the source pixel value. Pixels who’s corresponding mask values are zero do not participate in the maximum or minimum search.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image. The mask is centered over the source image pixel being tested.


Before calling any of the MorphBlackHatBorder functions the application first needs to call the corresponding MorphGetBufferSize to determine the amount of device memory to allocate as a working buffer. The allocated device memory is then passed as the pBuffer parameter to the corresponding MorphBlackHatBorder function.


Use the oSrcOffset and oSrcSize parameters to control where the border control operation is applied to the source image ROI borders.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiMorphBlackHatBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
Source image starting point relative to pSrc.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMask
Pointer to the start address of the mask array

param oMaskSize
Width and Height mask array.

param oAnchor
X and Y offsets of the mask origin frame of reference w.r.t the source pixel.

param pBuffer
Pointer to device memory scratch buffer at least as large as value returned by the corresponding MorphGetBufferSize call.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiMorphBlackHatBorder_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer morphological black hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphBlackHatBorder functions:.


NppStatus nppiMorphBlackHatBorder_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer morphological black hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphBlackHatBorder functions:.


NppStatus nppiMorphBlackHatBorder_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned integer morphological black hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphBlackHatBorder functions:.


NppStatus nppiMorphBlackHatBorder_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned integer morphological black hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphBlackHatBorder functions:.


NppStatus nppiMorphBlackHatBorder_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit signed integer morphological black hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphBlackHatBorder functions:.


NppStatus nppiMorphBlackHatBorder_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point morphological black hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphBlackHatBorder functions:.


NppStatus nppiMorphBlackHatBorder_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point morphological black hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphBlackHatBorder functions:.


NppStatus nppiMorphBlackHatBorder_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point morphological black hat with border control.
For common parameter descriptions, see Common parameters for nppiMorphBlackHatBorder functions:.


### Image Morph Gradient Border


#### MorphGradientBorder


Morphological dilated pixel result minus morphological eroded pixel result with border control.


Morphological gradient computes the output pixel as the morphological dilated pixel value of the pixels under the mask minus the morphological eroded pixel value of the pixels under the mask. Pixels who’s corresponding mask values are zero do not participate in the maximum or minimum search.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image. The mask is centered over the source image pixel being tested.


Before calling any of the MorphGradientBorder functions the application first needs to call the corresponding MorphGetBufferSize to determine the amount of device memory to allocate as a working buffer. The allocated device memory is then passed as the pBuffer parameter to the corresponding MorphGradientBorder function.


Use the oSrcOffset and oSrcSize parameters to control where the border control operation is applied to the source image ROI borders.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiMorphGradientBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
Source image starting point relative to pSrc.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pMask
Pointer to the start address of the mask array

param oMaskSize
Width and Height mask array.

param oAnchor
X and Y offsets of the mask origin frame of reference w.r.t the source pixel.

param pBuffer
Pointer to device memory scratch buffer at least as large as value returned by the corresponding MorphGetBufferSize call.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiMorphGradientBorder_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer morphological gradient with border control.
For common parameter descriptions, see Common parameters for nppiMorphGradientBorder functions:.


NppStatus nppiMorphGradientBorder_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer morphological gradient with border control.
For common parameter descriptions, see Common parameters for nppiMorphGradientBorder functions:.


NppStatus nppiMorphGradientBorder_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned integer morphological gradient with border control.
For common parameter descriptions, see Common parameters for nppiMorphGradientBorder functions:.


NppStatus nppiMorphGradientBorder_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned integer morphological gradient with border control.
For common parameter descriptions, see Common parameters for nppiMorphGradientBorder functions:.


NppStatus nppiMorphGradientBorder_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit signed integer morphological gradient with border control.
For common parameter descriptions, see Common parameters for nppiMorphGradientBorder functions:.


NppStatus nppiMorphGradientBorder_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point morphological gradient with border control.
For common parameter descriptions, see Common parameters for nppiMorphGradientBorder functions:.


NppStatus nppiMorphGradientBorder_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point morphological gradient with border control.
For common parameter descriptions, see Common parameters for nppiMorphGradientBorder functions:.


NppStatus nppiMorphGradientBorder_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pMask, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point morphological gradient with border control.
For common parameter descriptions, see Common parameters for nppiMorphGradientBorder functions:.