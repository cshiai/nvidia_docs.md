# Image Filtering Functions — npp 13.1 documentation

>


# Image Filtering Functions


Linear and non-linear image filtering functions.


Filtering functions are classified as [Neighborhood Operations](introduction.html#nppi_conventions_lb_1neighborhood_operations). It is the user’s responsibility to avoid [Sampling Beyond Image Boundaries](introduction.html#nppi_conventions_lb_1sampling_beyond_image_boundaries) .


These functions can be found in the nppif library. Linking to only the sub-libraries that you use can significantly save link time, application load time, and CUDA runtime startup time when using dynamic libraries.


## Image 1D Linear Filters


### 1DLinearFilter


The set of 1D linear filtering functions available in the library.


### Image Filter Column


#### FilterColumn


Apply convolution filter with user specified 1D column of weights.


##### Common parameters for nppiFilterColumn functions:


Result pixel is equal to the sum of the products between the kernel coefficients (pKernel array) and corresponding neighboring column pixel values in the source image defined by nKernelDim and nAnchorY, divided by nDivisor.


param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oROI
Region-Of-Interest (ROI).

param pKernel
Pointer to the start address of the kernel coefficient array. Coefficients are expected to be stored in reverse order.

param nMaskSize
Length of the linear kernel array.

param nAnchor
Y offset of the kernel origin frame of reference relative to the source pixel.

param nDivisor
The factor by which the convolved summation from the Filter operation should be divided. If equal to the sum of coefficients, this will keep the maximum result value within full scale.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterColumn_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
8-bit unsigned single-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
8-bit unsigned three-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
8-bit unsigned four-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
8-bit unsigned four-channel 1D column convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit unsigned single-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit unsigned three-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit unsigned four-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit unsigned four-channel 1D column convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit single-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit three-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit four-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit four-channel 1D column convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
32-bit float single-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
32-bit float three-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
32-bit float four-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
32-bit float four-channel 1D column convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


NppStatus nppiFilterColumn_64f_C1R_Ctx(const Npp64f *pSrc, Npp32s nSrcStep, Npp64f *pDst, Npp32s nDstStep, NppiSize oROI, const Npp64f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
64-bit float single-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn functions:.


### Image Filter Column Border


#### FilterColumnBorder


General purpose 1D convolution column filter with border control.


Pixels under the mask are multiplied by the respective weights in the mask and the results are summed. Before writing the result pixel the sum is scaled back via division by nDivisor. If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterColumnBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pKernel
Pointer to the start address of the kernel coefficient array. Coeffcients are expected to be stored in reverse order.

param nMaskSize
Width of the kernel.

param nAnchor
X offset of the kernel origin frame of reference relative to the source pixel.

param nDivisor
The factor by which the convolved summation from the Filter operation should be divided. If equal to the sum of coefficients, this will keep the maximum result value within full scale.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterColumnBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel channel 8-bit unsigned 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned convolution 1D column filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned convolution 1D column filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel channel 16-bit 1D column unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned 1D column convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel channel 16-bit 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit 1D column convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit float 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit float 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit float 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


NppStatus nppiFilterColumnBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit float 1D column convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder functions:.


### Image Filter Column 32f


#### FilterColumn32f


FilterColumn using floating-point weights.


##### Common parameters for nppiFilterColumn32f functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oROI
Region-Of-Interest (ROI).

param pKernel
Pointer to the start address of the kernel coefficient array. Coefficients are expected to be stored in reverse order.

param nMaskSize
Length of the linear kernel array.

param nAnchor
Y offset of the kernel origin frame of reference relative to the source pixel.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterColumn32f_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
8-bit unsigned single-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn32f functions:.


NppStatus nppiFilterColumn32f_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
8-bit unsigned three-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn32f functions:.


NppStatus nppiFilterColumn32f_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
8-bit unsigned four-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn32f functions:.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFilterColumn32f_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
8-bit unsigned four-channel 1D column convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterColumn32f functions:.


NppStatus nppiFilterColumn32f_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit unsigned single-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn32f functions:.


NppStatus nppiFilterColumn32f_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit unsigned three-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn32f functions:.


NppStatus nppiFilterColumn32f_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit unsigned four-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn32f functions:.


NppStatus nppiFilterColumn32f_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit unsigned four-channel 1D column convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterColumn32f functions:.


NppStatus nppiFilterColumn32f_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit single-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn32f functions:.


NppStatus nppiFilterColumn32f_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit three-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn32f functions:.


NppStatus nppiFilterColumn32f_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit four-channel 1D column convolution.
For common parameter descriptions, see Common parameters for nppiFilterColumn32f functions:.


NppStatus nppiFilterColumn32f_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit four-channel 1D column convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterColumn32f functions:.


### Image Filter Column Border 32f


#### FilterColumnBorder32f


General purpose 1D column convolution filter using floating-point weights with border control.


Pixels under the mask are multiplied by the respective weights in the mask and the results are summed. If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterColumnBorder32f functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pKernel
Pointer to the start address of the kernel coefficient array. Coeffcients are expected to be stored in reverse order.

param nMaskSize
Width of the kernel.

param nAnchor
X offset of the kernel origin frame of reference relative to the source pixel.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterColumnBorder32f_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder32f functions:.


NppStatus nppiFilterColumnBorder32f_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder32f functions:.


NppStatus nppiFilterColumnBorder32f_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder32f functions:.


NppStatus nppiFilterColumnBorder32f_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned 1D column convolution filter with border control, ignorint alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder32f functions:.


NppStatus nppiFilterColumnBorder32f_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder32f functions:.


NppStatus nppiFilterColumnBorder32f_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder32f functions:.


NppStatus nppiFilterColumnBorder32f_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder32f functions:.


NppStatus nppiFilterColumnBorder32f_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned 1D column convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder32f functions:.


NppStatus nppiFilterColumnBorder32f_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder32f functions:.


NppStatus nppiFilterColumnBorder32f_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder32f functions:.


NppStatus nppiFilterColumnBorder32f_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit 1D column convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder32f functions:.


NppStatus nppiFilterColumnBorder32f_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit 1D column convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterColumnBorder32f functions:.


### Image Filter Row


#### FilterRow


Apply convolution filter with user specified 1D row of weights.


Result pixel is equal to the sum of the products between the kernel coefficients (pKernel array) and corresponding neighboring row pixel values in the source image defined by nKernelDim and nAnchorX, divided by nDivisor.


##### Common parameters for nppiFilterRow functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oROI
Region-Of-Interest (ROI).

param pKernel
Pointer to the start address of the kernel coefficient array. Coefficients are expected to be stored in reverse order.

param nMaskSize
Length of the linear kernel array.

param nAnchor
X offset of the kernel origin frame of reference relative to the source pixel.

param nDivisor
The factor by which the convolved summation from the Filter operation should be divided. If equal to the sum of coefficients, this will keep the maximum result value within full scale.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterRow_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
8-bit unsigned single-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
8-bit unsigned three-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
8-bit unsigned four-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
8-bit unsigned four-channel 1D row convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit unsigned single-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit unsigned three-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit unsigned four-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit unsigned four-channel 1D row convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit single-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit three-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit four-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
16-bit four-channel 1D row convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
32-bit float single-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
32-bit float three-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
32-bit float four-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
32-bit float four-channel 1D row convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


NppStatus nppiFilterRow_64f_C1R_Ctx(const Npp64f *pSrc, Npp32s nSrcStep, Npp64f *pDst, Npp32s nDstStep, NppiSize oROI, const Npp64f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
64-bit float single-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow functions:.


### Image Filter Row Border


#### FilterRowBorder


General purpose 1D convolution row filter with border control.


Pixels under the mask are multiplied by the respective weights in the mask and the results are summed. Before writing the result pixel the sum is scaled back via division by nDivisor. If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterRowBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pKernel
Pointer to the start address of the kernel coefficient array. Coeffcients are expected to be stored in reverse order.

param nMaskSize
Width of the kernel.

param nAnchor
X offset of the kernel origin frame of reference relative to the source pixel.

param nDivisor
The factor by which the convolved summation from the Filter operation should be divided. If equal to the sum of coefficients, this will keep the maximum result value within full scale.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterRowBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel channel 8-bit unsigned 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned convolution 1D row filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned convolution 1D row filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel channel 16-bit 1D row unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned 1D row convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel channel 16-bit 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, Npp32s nMaskSize, Npp32s nAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit 1D row convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit float 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit float 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit float 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


NppStatus nppiFilterRowBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit float 1D row convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder functions:.


### Image Filter Row 32f


#### FilterRow32f


FilterRow using floating-point weights.


##### Common parameters for nppiFilterRow32f functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oROI
Region-Of-Interest (ROI).

param pKernel
Pointer to the start address of the kernel coefficient array. Coefficients are expected to be stored in reverse order.

param nMaskSize
Length of the linear kernel array.

param nAnchor
X offset of the kernel origin frame of reference relative to the source pixel.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterRow32f_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
8-bit unsigned single-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow32f functions:.


NppStatus nppiFilterRow32f_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
8-bit unsigned three-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow32f functions:.


NppStatus nppiFilterRow32f_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
8-bit unsigned four-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow32f functions:.


NppStatus nppiFilterRow32f_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
8-bit unsigned four-channel 1D row convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRow32f functions:.


NppStatus nppiFilterRow32f_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit unsigned single-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow32f functions:.


NppStatus nppiFilterRow32f_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit unsigned three-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow32f functions:.


NppStatus nppiFilterRow32f_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit unsigned four-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow32f functions:.


NppStatus nppiFilterRow32f_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit unsigned four-channel 1D row convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRow32f functions:.


NppStatus nppiFilterRow32f_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit single-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow32f functions:.


NppStatus nppiFilterRow32f_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit three-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow32f functions:.


NppStatus nppiFilterRow32f_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit four-channel 1D row convolution.
For common parameter descriptions, see Common parameters for nppiFilterRow32f functions:.


NppStatus nppiFilterRow32f_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
16-bit four-channel 1D row convolution ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRow32f functions:.


### Image Filter Row Border 32f


#### FilterRowBorder32f


General purpose 1D row convolution filter using floating-point weights with border control.


Pixels under the mask are multiplied by the respective weights in the mask and the results are summed. If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterRowBorder32f functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pKernel
Pointer to the start address of the kernel coefficient array. Coeffcients are expected to be stored in reverse order.

param nMaskSize
Width of the kernel.

param nAnchor
X offset of the kernel origin frame of reference relative to the source pixel.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterRowBorder32f_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder32f functions:.


NppStatus nppiFilterRowBorder32f_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder32f functions:.


NppStatus nppiFilterRowBorder32f_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder32f functions:.


NppStatus nppiFilterRowBorder32f_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned 1D row convolution filter with border control, ignorint alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder32f functions:.


NppStatus nppiFilterRowBorder32f_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder32f functions:.


NppStatus nppiFilterRowBorder32f_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder32f functions:.


NppStatus nppiFilterRowBorder32f_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder32f functions:.


NppStatus nppiFilterRowBorder32f_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned 1D row convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder32f functions:.


NppStatus nppiFilterRowBorder32f_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder32f functions:.


NppStatus nppiFilterRowBorder32f_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder32f functions:.


NppStatus nppiFilterRowBorder32f_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit 1D row convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder32f functions:.


NppStatus nppiFilterRowBorder32f_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit 1D row convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterRowBorder32f functions:.


### Image Filter 1D Window Sum


#### 1D Window Sum


The set of 1D window sum functions available in the library.


### Image Filter 1D Window Column Sum


#### 1D Window Column Sum


1D mask Window Column Sum for 8 and 16 bit images.


##### Common parameters for nppiFilterSumWindowColumn functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oROI
Region-Of-Interest (ROI).

param nMaskSize
Length of the linear kernel array.

param nAnchor
Y offset of the kernel origin frame of reference relative to the source pixel.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiSumWindowColumn_8u32f_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
One channel 8-bit unsigned 1D (column) sum to 32f.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 1-channel 8 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumn functions:.


NppStatus nppiSumWindowColumn_8u32f_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned 1D (column) sum to 32f.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 3-channel 8 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumn functions:.


NppStatus nppiSumWindowColumn_8u32f_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned 1D (column) sum to 32f.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 4-channel 8 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumn functions:.


NppStatus nppiSumWindowColumn_16u32f_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
One channel 16-bit unsigned 1D (column) sum to 32f.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 1-channel 16 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumn functions:.


NppStatus nppiSumWindowColumn_16u32f_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned 1D (column) sum to 32f.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 3-channel 16 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumn functions:.


NppStatus nppiSumWindowColumn_16u32f_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned 1D (column) sum to 32f.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 4-channel 16 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumn functions:.


NppStatus nppiSumWindowColumn_16s32f_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
One channel 16-bit signed 1D (column) sum to 32f.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 1-channel 16 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumn functions:.


NppStatus nppiSumWindowColumn_16s32f_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit signed 1D (column) sum to 32f.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 1-channel 16 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumn functions:.


NppStatus nppiSumWindowColumn_16s32f_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit signed 1D (column) sum to 32f.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 4-channel 16 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumn functions:.


### Image Filter 1D Window Row Sum


#### 1D Window Row Sum


1D mask Window Row Sum for 8 and 16 bit images.


##### Common parameters for nppiFilterSumWindowRow functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oROI
Region-Of-Interest (ROI).

param nMaskSize
Length of the linear kernel array.

param nAnchor
X offset of the kernel origin frame of reference relative to the source pixel.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiSumWindowRow_8u32f_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
One channel 8-bit unsigned 1D (row) sum to 32f.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 1-channel 8-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRow functions:.


NppStatus nppiSumWindowRow_8u32f_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned 1D (row) sum to 32f.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 3-channel 8-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRow functions:.


NppStatus nppiSumWindowRow_8u32f_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned 1D (row) sum to 32f.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 4-channel 8-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRow functions:.


NppStatus nppiSumWindowRow_16u32f_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
One channel 16-bit unsigned 1D (row) sum to 32f.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 1-channel 16-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRow functions:.


NppStatus nppiSumWindowRow_16u32f_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned 1D (row) sum to 32f.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 3-channel 16-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRow functions:.


NppStatus nppiSumWindowRow_16u32f_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned 1D (row) sum to 32f.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 4-channel 16-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRow functions:.


NppStatus nppiSumWindowRow_16s32f_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
One channel 16-bit signed 1D (row) sum to 32f.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 1-channel 16-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRow functions:.


NppStatus nppiSumWindowRow_16s32f_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit signed 1D (row) sum to 32f.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 3-channel 16-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRow functions:.


NppStatus nppiSumWindowRow_16s32f_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit signed 1D (row) sum to 32f.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 4-channel 16-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRow functions:.


### Image Filter 1D Window Sum Border


#### 1D Window Sum with Border Control


The set of 1D window sum functions with border control available in the library.


### Image Filter 1D Window Column Sum Border


#### 1D Window Column Sum Border


1D mask Window Column Sum for 8 and 16 bit images with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterSumWindowColumnBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oROI
Region-Of-Interest (ROI).

param nMaskSize
Length of the linear kernel array.

param nAnchor
Y offset of the kernel origin frame of reference relative to the source pixel.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiSumWindowColumnBorder_8u32f_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
One channel 8-bit unsigned 1D (column) sum to 32f with border control.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 1-channel 8 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumnBorder functions:.


NppStatus nppiSumWindowColumnBorder_8u32f_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned 1D (column) sum to 32f with border control.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 3-channel 8 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumnBorder functions:.


NppStatus nppiSumWindowColumnBorder_8u32f_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned 1D (column) sum to 32f with border control.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 4-channel 8 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumnBorder functions:.


NppStatus nppiSumWindowColumnBorder_16u32f_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
One channel 16-bit unsigned 1D (column) sum to 32f with border control.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 1-channel 16 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumnBorder functions:.


NppStatus nppiSumWindowColumnBorder_16u32f_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned 1D (column) sum to 32f with border control.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 3-channel 16 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumnBorder functions:.


NppStatus nppiSumWindowColumnBorder_16u32f_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned 1D (column) sum to 32f with border control.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 4-channel 16 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumnBorder functions:.


NppStatus nppiSumWindowColumnBorder_16s32f_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
One channel 16-bit signed 1D (column) sum to 32f with border control.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 1-channel 16 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumnBorder functions:.


NppStatus nppiSumWindowColumnBorder_16s32f_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed 1D (column) sum to 32f with border control.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 1-channel 16 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumnBorder functions:.


NppStatus nppiSumWindowColumnBorder_16s32f_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed 1D (column) sum to 32f with border control.

Apply Column Window Summation filter over a 1D mask region around each source pixel for 4-channel 16 bit/pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring column pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowColumnBorder functions:.


### Image Filter 1D Window Row Sum Border


#### 1D Window Row Sum Border


1D mask Window Row Sum for 8 and 16 bit images with border control.


##### Common parameters for nppiFilterSumWindowRowBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oROI
Region-Of-Interest (ROI).

param nMaskSize
Length of the linear kernel array.

param nAnchor
X offset of the kernel origin frame of reference relative to the source pixel.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiSumWindowRowBorder_8u32f_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
One channel 8-bit unsigned 1D (row) sum to 32f with border control.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 1-channel 8-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRowBorder functions:.


NppStatus nppiSumWindowRowBorder_8u32f_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned 1D (row) sum to 32f with border control.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 3-channel 8-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRowBorder functions:.


NppStatus nppiSumWindowRowBorder_8u32f_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned 1D (row) sum to 32f with border control.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 4-channel 8-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRowBorder functions:.


NppStatus nppiSumWindowRowBorder_16u32f_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
One channel 16-bit unsigned 1D (row) sum to 32f with border control.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 1-channel 16-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRowBorder functions:.


NppStatus nppiSumWindowRowBorder_16u32f_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned 1D (row) sum to 32f with border control.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 3-channel 16-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRowBorder functions:.


NppStatus nppiSumWindowRowBorder_16u32f_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned 1D (row) sum to 32f with border control.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 4-channel 16-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRowBorder functions:.


NppStatus nppiSumWindowRowBorder_16s32f_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
One channel 16-bit signed 1D (row) sum to 32f with border control.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 1-channel 16-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRowBorder functions:.


NppStatus nppiSumWindowRowBorder_16s32f_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed 1D (row) sum to 32f with border control.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 3-channel 16-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRowBorder functions:.


NppStatus nppiSumWindowRowBorder_16s32f_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oROI, Npp32s nMaskSize, Npp32s nAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed 1D (row) sum to 32f with border control.

Apply Row Window Summation filter over a 1D mask region around each source pixel for 4-channel 16-bit pixel input images with 32-bit floating point output.
Result 32-bit floating point pixel is equal to the sum of the corresponding and neighboring row pixel values in a mask region of the source image defined by nMaskSize and nAnchor.
For common parameter descriptions, see Common parameters for nppiFilterSumWindowRowBorder functions:.


## Image Convolution


### Convolution


The set convolution functions available in the library.


### Image Filter


#### Filter


General purpose 2D convolution filter.


Pixels under the mask are multiplied by the respective weights in the mask and the results are summed. Before writing the result pixel the sum is scaled back via division by nDivisor.


##### Common parameters for nppiFilter functions:




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

param pKernel
Pointer to the start address of the kernel coefficient array. Coeffcients are expected to be stored in reverse order.

param oKernelSize
Width and Height of the rectangular kernel.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param nDivisor
The factor by which the convolved summation from the Filter operation should be divided. If equal to the sum of coefficients, this will keep the maximum result value within full scale.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilter_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
Four channel channel 8-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned convolution filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
Four channel channel 16-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned convolution filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
Single channel 16-bit convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
Three channel 16-bit convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
Four channel channel 16-bit convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppStreamContext nppStreamCtx)
Four channel 16-bit convolution filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 32-bit float convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_32f_C2R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Two channel 32-bit float convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 32-bit float convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 32-bit float convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 32-bit float convolution filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


NppStatus nppiFilter_64f_C1R_Ctx(const Npp64f *pSrc, Npp32s nSrcStep, Npp64f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp64f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 64-bit float convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter functions:.


### Image Filter 32f


#### Filter32f


General purpose 2D convolution filter using floating point weights.


Pixels under the mask are multiplied by the respective weights in the mask and the results are summed.


##### Common parameters for nppiFilter32f functions:




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

param pKernel
Pointer to the start address of the kernel coefficient array. Coeffcients are expected to be stored in reverse order.

param oKernelSize
Width and Height of the rectangular kernel.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilter32f_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8u_C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Two channel 8-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned convolution filter, ignorint alpha channel.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8s_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 8-bit signed convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8s_C2R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Two channel 8-bit signed convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8s_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 8-bit signed convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8s_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit signed convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8s_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit signed convolution filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned convolution filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 16-bit convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit convolution filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_32s_C1R_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 32-bit convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_32s_C3R_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 32-bit convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_32s_C4R_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 32-bit convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_32s_AC4R_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 32-bit convolution filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_16f_C1R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 16-bit floating point convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_16f_C3R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit floating point convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_16f_C4R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit floating point convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8u16s_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8u16s_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned to 16-bit signed convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8u16s_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned to 16-bit signed convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8u16s_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned to 16-bit signed convolution filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8s16s_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 8-bit to 16-bit signed convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8s16s_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 8-bit to 16-bit signed convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8s16s_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit to 16-bit signed convolution filter.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


NppStatus nppiFilter32f_8s16s_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit to 16-bit signed convolution filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilter32f functions:.


### Image Filter Border


#### FilterBorder


General purpose 2D convolution filter with border control.


Pixels under the mask are multiplied by the respective weights in the mask and the results are summed. Before writing the result pixel the sum is scaled back via division by nDivisor. If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pKernel
Pointer to the start address of the kernel coefficient array. Coeffcients are expected to be stored in reverse order.

param oKernelSize
Width and Height of the rectangular kernel.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param nDivisor
The factor by which the convolved summation from the Filter operation should be divided. If equal to the sum of coefficients, this will keep the maximum result value within full scale.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel channel 8-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel channel 16-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel channel 16-bit convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32s *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, Npp32s nDivisor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit float convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_32f_C2R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Two channel 32-bit float convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit float convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit float convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


NppStatus nppiFilterBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit float convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBorder functions:.


### Image Filter Border 32f


#### FilterBorder32f


General purpose 2D convolution filter using floating-point weights with border control.


Pixels under the mask are multiplied by the respective weights in the mask and the results are summed. Before writing the result pixel the sum is scaled back via division by nDivisor. If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterBorder32f functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param pKernel
Pointer to the start address of the kernel coefficient array. Coeffcients are expected to be stored in reverse order.

param oKernelSize
Width and Height of the rectangular kernel.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterBorder32f_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8u_C2R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Two channel 8-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned convolution filter with border control, ignorint alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8s_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit signed convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8s_C2R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Two channel 8-bit signed convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8s_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit signed convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8s_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit signed convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8s_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit signed convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_32s_C1R_Ctx(const Npp32s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_32s_C3R_Ctx(const Npp32s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_32s_C4R_Ctx(const Npp32s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_32s_AC4R_Ctx(const Npp32s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_16f_C1R_Ctx(const Npp16f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit floating point convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_16f_C3R_Ctx(const Npp16f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit floating point convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_16f_C4R_Ctx(const Npp16f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit floating point convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8u16s_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8u16s_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned to 16-bit signed convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8u16s_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned to 16-bit signed convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8u16s_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned to 16-bit signed convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8s16s_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit to 16-bit signed convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8s16s_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit to 16-bit signed convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8s16s_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit to 16-bit signed convolution filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


NppStatus nppiFilterBorder32f_8s16s_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pKernel, NppiSize oKernelSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit to 16-bit signed convolution filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBorder32f functions:.


## 2D Fixed Linear Filters


### 2D Fixed Linear Filters


The set of 2D fixed linear filtering functions available in the library.


### Image Filter Box


#### FilterBox


Computes the average pixel values of the pixels under a rectangular mask.


##### Common parameters for nppiFilterBox functions:




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

param oMaskSize
Width and Height of the neighborhood region for the local Avg operation.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterBox_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned box filter, ignorting alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned box filter, ignorting alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 16-bit box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit box filter, ignorting alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point box filter, ignorting alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


NppStatus nppiFilterBox_64f_C1R_Ctx(const Npp64f *pSrc, Npp32s nSrcStep, Npp64f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 64-bit floating-point box filter.
For common parameter descriptions, see Common parameters for nppiFilterBox functions:.


### Image Filter Box Border


#### FilterBoxBorder


Computes the average pixel values of the pixels under a rectangular mask with border control. If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported. *


##### Common parameters for nppiFilterBoxBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param oMaskSize
Width and Height of the neighborhood region for the local Avg operation.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterBoxBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned box filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned box filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit box filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


NppStatus nppiFilterBoxBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point box filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorder functions:.


### Image Filter Box Border Advanced


#### FilterBoxBorderAdvanced


Computes the average pixel values of the pixels under a rectangular mask with border control. If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image. These versions of the functions are intended to significantly improve performance when very large mask sizes are used.


Currently only the NPP_BORDER_REPLICATE border type operation is supported. *


##### Common parameters for nppiFilterBoxBorderAdvanced functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param oMaskSize
Width and Height of the neighborhood region for the local Avg operation.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param eBorderType
The border type operation to be applied at source image border boundaries.

param pBuffer
Pointer to device memory buffer of size hpBufferSize bytes returned by calling nppiFilterBoxBorderAdvancedGetDeviceBufferSize.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterBoxBorderAdvancedGetDeviceBufferSize(NppiSize oSizeROI, int nChannels, int *hpBufferSize)
Returns the required size of host memory buffer needed by most nppiFilterBoxBorderAdvanced functions.

Parameters

oSizeROI – Region-Of-Interest (ROI).
nChannels – The number of channels in the image to be filtered (1, 3, or 4).
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFilterBoxBorderAdvancedGetDeviceBufferSize_64(NppiSize oSizeROI, int nChannels, int *hpBufferSize)
Returns the required size of host memory buffer needed by nppiFilterBoxBorderAdvanced functions with 64-bit image data.

Parameters

oSizeROI – Region-Of-Interest (ROI).
nChannels – The number of channels in the image to be filtered (1, 3, or 4).
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFilterBoxBorderAdvanced_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


NppStatus nppiFilterBoxBorderAdvanced_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


NppStatus nppiFilterBoxBorderAdvanced_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


NppStatus nppiFilterBoxBorderAdvanced_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


NppStatus nppiFilterBoxBorderAdvanced_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


NppStatus nppiFilterBoxBorderAdvanced_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


NppStatus nppiFilterBoxBorderAdvanced_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Single channel 16-bit box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


NppStatus nppiFilterBoxBorderAdvanced_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three channel 16-bit box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


NppStatus nppiFilterBoxBorderAdvanced_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four channel 16-bit box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


NppStatus nppiFilterBoxBorderAdvanced_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


NppStatus nppiFilterBoxBorderAdvanced_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


NppStatus nppiFilterBoxBorderAdvanced_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


NppStatus nppiFilterBoxBorderAdvanced_64f_C1R_Ctx(const Npp64f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp64f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, Npp8u *pBuffer64, NppStreamContext nppStreamCtx)
Single channel 64-bit floating-point box filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBoxBorderAdvanced functions:.


### Image Filter Threshold Adaptive Box Border


#### FilterThresholdAdaptiveBoxBorder


Computes the average pixel values of the pixels under a square mask with border control. If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image. Once the neighborhood average around a source pixel is determined the souce pixel is compared to the average - nDelta and if the source pixel is greater than that average the corresponding destination pixel is set to nValGT, otherwise nValLE.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param oMaskSize
Width and Height of the neighborhood region for the local Avg operation, Width and Height must be equal and odd.

param nDelta
Neighborhood average adjustment value

param nValGT
Destination output value if source pixel is greater than average.

param nValLE
Destination output value if source pixel is less than or equal to average.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterThresholdAdaptiveBoxBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, Npp32f nDelta, Npp8u nValGT, Npp8u nValLE, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned threshold adaptive box filter with border control.


## Rank Filters


### Rank Filters


The set of functions providing min/max/median values for rectangular mask region with/without border available in the library.


### Image Filter Max


#### FilterMax


Result pixel value is the maximum of pixel values under the rectangular mask region.


##### Common parameters for nppiFilterMax functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step plus mask size width.

param oSizeROI
Region-Of-Interest (ROI).

param oMaskSize
Width and Height of the neighborhood region for the local Max operation.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterMax_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned maximum filter.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned maximum filter.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned maximum filter.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned maximum filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned maximum filter.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned maximum filter.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned maximum filter.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned maximum filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 16-bit signed maximum filter.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit signed maximum filter.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit signed maximum filter.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit signed maximum filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point maximum filter.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point maximum filter.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point maximum filter.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


NppStatus nppiFilterMax_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point maximum filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMax functions:.


### Image Filter Max Border


#### FilterMaxBorder


Result pixel value is the maximum of pixel values under the rectangular mask region with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterMaxBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param oMaskSize
Width and Height of the neighborhood region for the local Max operation.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterMaxBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned maximum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned maximum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned maximum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned maximum filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned maximum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned maximum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned maximum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned maximum filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed maximum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed maximum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed maximum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed maximum filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point maximum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point maximum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point maximum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


NppStatus nppiFilterMaxBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point maximum filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMaxBorder functions:.


### Image Filter Min


#### FilterMin


Result pixel value is the minimum of pixel values under the rectangular mask region.


##### Common parameters for nppiFilterMin functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step plus mask size width.

param oSizeROI
Region-Of-Interest (ROI).

param oMaskSize
Width and Height of the neighborhood region for the local Min operation.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterMin_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned minimum filter.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned minimum filter.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned minimum filter.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned minimum filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned minimum filter.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned minimum filter.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned minimum filter.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned minimum filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 16-bit signed minimum filter.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 16-bit signed minimum filter.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit signed minimum filter.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 16-bit signed minimum filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point minimum filter.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point minimum filter.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point minimum filter.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


NppStatus nppiFilterMin_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point minimum filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMin functions:.


### Image Filter Min Border


#### FilterMinBorder


Result pixel value is the minimum of pixel values under the rectangular mask region with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterMinBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param oMaskSize
Width and Height of the neighborhood region for the local Min operation.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterMinBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned minimum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned minimum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned minimum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned minimum filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned minimum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned minimum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned minimum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned minimum filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed minimum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed minimum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed minimum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed minimum filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point minimum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point minimum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point minimum filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


NppStatus nppiFilterMinBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point minimum filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMinBorder functions:.


### Image Filter Median


#### FilterMedian


Result pixel value is the median of pixel values under the rectangular mask region.


##### Common parameters for nppiFilterMedian functions:




##### Common parameters for nppiFilterMedianGetBufferSize functions:




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

param oMaskSize
Width and Height of the neighborhood region for the local Median operation.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param pBuffer
Pointer to the user-allocated scratch buffer required for the Median operation.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes

param oSizeROI
Region-Of-Interest (ROI).

param oMaskSize
Width and Height of the neighborhood region for the local Median operation.

param nBufferSize
Pointer to the size of the scratch buffer required for the Median operation.

return
Image Data Related Error Codes


Functions


NppStatus nppiFilterMedian_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Single channel 16-bit signed median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three channel 16-bit signed median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four channel 16-bit signed median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four channel 16-bit signed median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedian_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianGetBufferSize_8u_C1R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_8u_C3R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_8u_C4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_8u_AC4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_16u_C1R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_16u_C3R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_16u_C4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_16u_AC4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_16s_C1R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Single channel 16-bit signed median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_16s_C3R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Three channel 16-bit signed median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_16s_C4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Four channel 16-bit signed median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_16s_AC4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Four channel 16-bit signed median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_32f_C1R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_32f_C3R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_32f_C4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


NppStatus nppiFilterMedianGetBufferSize_32f_AC4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedianGetBufferSize functions:.


### Image Filter Median Border


#### FilterMedianBorder


Result pixel value is the median of pixel values under the rectangular mask region.


##### Common parameters for nppiFilterMedianBorder functions:




##### Common parameters for nppiFilterMedianBorderGetBufferSize functions:




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

param oMaskSize
Width and Height of the neighborhood region for the local Median operation.

param oAnchor
X and Y offsets of the kernel origin frame of reference relative to the source pixel.

param pBuffer
Pointer to the user-allocated scratch buffer required for the Median operation.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes

param oSizeROI
Region-Of-Interest (ROI).

param oMaskSize
Width and Height of the neighborhood region for the local Median operation.

param nBufferSize
Pointer to the size of the scratch buffer required for the Median operation.

return
Image Data Related Error Codes


Functions


NppStatus nppiFilterMedianBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point median filter.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp8u *pBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedian functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_8u_C1R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_8u_C3R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_8u_C4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_8u_AC4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_16u_C1R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_16u_C3R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_16u_C4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_16u_AC4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_16s_C1R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_16s_C3R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_16s_C4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_16s_AC4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_32f_C1R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_32f_C3R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_32f_C4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point median filter scratch memory size.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


NppStatus nppiFilterMedianBorderGetBufferSize_32f_AC4R_Ctx(NppiSize oSizeROI, NppiSize oMaskSize, Npp32u *nBufferSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point median filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterMedianBorderGetBufferSize functions:.


## Fixed Filters


### Fixed Filters


Fixed filters perform linear filtering operations (such as convolutions) with predefined kernels of fixed sizes. Note that this section also contains a few dynamic kernel filters, namely GaussAdvanced and Bilateral.


Some of the fixed filters have versions with border control. For these functions, if any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported for these functions.


### Image Filter Prewitt


#### FilterPrewitt


Filters the image using a Prewitt filter kernel.


##### Common parameters for nppiFilterPrewitt functions:




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


FilterPrewittHoriz


Filters the image using a horizontal Prewitt filter kernel:



  \[\begin{split} \left( \begin{array}{rrr} 1 & 1 & 1 \\ 0 & 0 & 0 \\ -1 & -1 & -1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterPrewittHoriz_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned horizontal Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittHoriz_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned horizontal Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittHoriz_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned horizontal Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittHoriz_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned horizontal Prewitt filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittHoriz_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 16-bit signed horizontal Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittHoriz_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 16-bit signed horizontal Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittHoriz_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed horizontal Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittHoriz_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed horizontal Prewitt filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittHoriz_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point horizontal Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittHoriz_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point horizontal Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittHoriz_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point horizontal Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittHoriz_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point horizontal Prewitt filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


FilterPrewittVert


Filters the image using a vertical Prewitt filter kernel:



  \[\begin{split} \left( \begin{array}{rrr} -1 & 0 & 1 \\ -1 & 0 & 1 \\ -1 & 0 & 1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterPrewittVert_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned vertical Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittVert_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned vertical Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittVert_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned vertical Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittVert_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned vertical Prewitt filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittVert_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 16-bit signed vertical Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittVert_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 16-bit signed vertical Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittVert_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed vertical Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittVert_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed vertical Prewitt filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittVert_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point vertical Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittVert_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point vertical Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittVert_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point vertical Prewitt filter.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


NppStatus nppiFilterPrewittVert_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point vertical Prewitt filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterPrewitt functions:.


### Image Filter Prewitt Border


#### FilterPrewittBorder


Filters the image using a Prewitt filter kernel with border control.


##### Common parameters for nppiFilterPrewittBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

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


FilterPrewittHorizBorder


Filters the image using a horizontal Prewitt filter kernel with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.



  \[\begin{split} \left( \begin{array}{rrr} 1 & 1 & 1 \\ 0 & 0 & 0 \\ -1 & -1 & -1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterPrewittHorizBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned horizontal Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittHorizBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned horizontal Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittHorizBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned horizontal Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittHorizBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned horizontal Prewitt filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittHorizBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed horizontal Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittHorizBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed horizontal Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittHorizBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed horizontal Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittHorizBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed horizontal Prewitt filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittHorizBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point horizontal Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittHorizBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point horizontal Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittHorizBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point horizontal Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittHorizBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point horizontal Prewitt filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


FilterPrewittVertBorder


Filters the image using a vertical Prewitt filter kernel with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.



  \[\begin{split} \left( \begin{array}{rrr} -1 & 0 & 1 \\ -1 & 0 & 1 \\ -1 & 0 & 1 \\ \end{array} \right); \end{split}\]
NppStatus nppiFilterPrewittVertBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned vertical Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittVertBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned vertical Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittVertBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned vertical Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittVertBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned vertical Prewitt filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittVertBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed vertical Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittVertBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed vertical Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittVertBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed vertical Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittVertBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed vertical Prewitt filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittVertBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point vertical Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittVertBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point vertical Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittVertBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point vertical Prewitt filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


NppStatus nppiFilterPrewittVertBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point vertical Prewitt filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterPrewittBorder functions:.


### Image Filter Scharr


#### FilterScharr


Filters the image using a Scharr filter kernel.


##### Common parameters for nppiFilterScharr functions:




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


FilterScharrHoriz


Filters the image using a horizontal Scharr filter kernel:



  \[\begin{split} \left( \begin{array}{rrr} 3 & 10 & 3 \\ 0 & 0 & 0 \\ -3 & -10 & -3 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterScharrHoriz_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed horizontal Scharr filter.
For common parameter descriptions, see Common parameters for nppiFilterScharr functions:.


NppStatus nppiFilterScharrHoriz_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed horizontal Scharr filter.
For common parameter descriptions, see Common parameters for nppiFilterScharr functions:.


NppStatus nppiFilterScharrHoriz_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point horizontal Scharr filter.
For common parameter descriptions, see Common parameters for nppiFilterScharr functions:.


FilterScharrVert


Filters the image using a vertical Scharr filter kernel:



  \[\begin{split} \left( \begin{array}{rrr} -3 & 0 & 3 \\ -10 & 0 & 10 \\ -3 & 0 & 3 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterScharrVert_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed vertical Scharr filter.
For common parameter descriptions, see Common parameters for nppiFilterScharr functions:.


NppStatus nppiFilterScharrVert_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed vertical Scharr filter.
For common parameter descriptions, see Common parameters for nppiFilterScharr functions:.


NppStatus nppiFilterScharrVert_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point vertical Scharr filter.
For common parameter descriptions, see Common parameters for nppiFilterScharr functions:.


### Image Filter Scharr Border


#### FilterScharrBorder


Filters the image using a Scharr filter kernel with border control.


##### Common parameters for nppiFilterScharrBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

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


FilterScharrHorizBorder


Filters the image using a horizontal Scharr filter kernel with border control:



  \[\begin{split} \left( \begin{array}{rrr} 3 & 10 & 3 \\ 0 & 0 & 0 \\ -3 & -10 & -3 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterScharrHorizBorder_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed horizontal Scharr filter kernel with border control.
For common parameter descriptions, see Common parameters for nppiFilterScharrBorder functions:.


NppStatus nppiFilterScharrHorizBorder_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed horizontal Scharr filter kernel with border control.
For common parameter descriptions, see Common parameters for nppiFilterScharrBorder functions:.


NppStatus nppiFilterScharrHorizBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point horizontal Scharr filter kernel with border control.
For common parameter descriptions, see Common parameters for nppiFilterScharrBorder functions:.


FilterScharrVertBorder


Filters the image using a vertical Scharr filter kernel kernel with border control:



  \[\begin{split} \left( \begin{array}{rrr} -3 & 0 & 3 \\ -10 & 0 & 10 \\ -3 & 0 & 3 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterScharrVertBorder_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed vertical Scharr filter kernel with border control.
For common parameter descriptions, see Common parameters for nppiFilterScharrBorder functions:.


NppStatus nppiFilterScharrVertBorder_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed vertical Scharr filter kernel with border control.
For common parameter descriptions, see Common parameters for nppiFilterScharrBorder functions:.


NppStatus nppiFilterScharrVertBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point vertical Scharr filter kernel with border control.
For common parameter descriptions, see Common parameters for nppiFilterScharrBorder functions:.


### Image Filter Sobel


#### FilterSobel


Filters the image using a Sobel filter kernel.


##### Common parameters for nppiFilterSobel functions:




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

param eMaskSize
Enumeration value specifying the mask size.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


FilterSobelHoriz


Filters the image using a horizontal Sobel filter kernel:



  \[\begin{split} \left( \begin{array}{rrr} 1 & 2 & 1 \\ 0 & 0 & 0 \\ -1 & -2 & -1 \\ \end{array} \right) \left( \begin{array}{rrrrr} 1 & 4 & 6 & 4 & 1 \\ 2 & 8 & 12 & 8 & 2 \\ 0 & 0 & 0 & 0 & 0 \\ -2 & -8 & -12 & -8 & -2 \\ -1 & -4 & -6 & -4 & -1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterSobelHoriz_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed horizontal Sobel filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 16-bit signed horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 16-bit signed horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned horizontal Sobel filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point horizontal Sobel filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHoriz_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHorizMask_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


FilterSobelVert


Filters the image using a vertical Sobel filter kernel:



  \[\begin{split} \left( \begin{array}{rrr} -1 & 0 & 1 \\ -2 & 0 & 2 \\ -1 & 0 & 1 \\ \end{array} \right) \left( \begin{array}{rrrrr} -1 & -2 & 0 & 2 & 1 \\ -4 & -8 & 0 & 8 & 4 \\ -6 & -12 & 0 & 12 & 6 \\ -4 & -8 & 0 & 8 & 4 \\ -1 & -2 & 0 & 2 & 1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterSobelVert_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed vertical Sobel filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 16-bit signed vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 16-bit signed vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned vertical Sobel filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point vertical Sobel filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVert_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVertMask_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


FilterSobelHorizSecond


Filters the image using a second derivative, horizontal Sobel filter kernel:



  \[\begin{split} \left( \begin{array}{rrr} 1 & 2 & 1 \\ -2 & -4 & -2 \\ 1 & 2 & 1 \\ \end{array} \right) \left( \begin{array}{rrrrr} 1 & 4 & 6 & 4 & 1 \\ 0 & 0 & 0 & 0 & 0 \\ -2 & -8 & -12 & -8 & -2 \\ 0 & 0 & 0 & 0 & 0 \\ 1 & 4 & 6 & 4 & 1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterSobelHorizSecond_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed second derivative, horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHorizSecond_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed second derivative, horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelHorizSecond_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point second derivative, horizontal Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


FilterSobelVertSecond


Filters the image using a second derivative, vertical Sobel filter kernel:



  \[\begin{split} \left( \begin{array}{rrr} 1 & -2 & 1 \\ 2 & -4 & 2 \\ 1 & -2 & 1 \\ \end{array} \right) \left( \begin{array}{rrrrr} 1 & 0 & -2 & 0 & 1 \\ 4 & 0 & -8 & 0 & 4 \\ 6 & 0 & -12 & 0 & 6 \\ 4 & 0 & -8 & 0 & 4 \\ 1 & 0 & -2 & 0 & 1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterSobelVertSecond_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed second derivative, vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVertSecond_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed second derivative, vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelVertSecond_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point second derivative, vertical Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


FilterSobelCross


Filters the image using a second cross derivative Sobel filter kernel:



  \[\begin{split} \left( \begin{array}{rrr} -1 & 0 & 1 \\ 0 & 0 & 0 \\ 1 & 0 & -1 \\ \end{array} \right) \left( \begin{array}{rrrrr} -1 & -2 & 0 & 2 & 1 \\ -2 & -4 & 0 & 4 & 2 \\ 0 & 0 & 0 & 0 & 0 \\ 2 & 4 & 0 & -4 & -2 \\ 1 & 2 & 0 & -2 & -1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterSobelCross_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed second cross derivative Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelCross_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed second cross derivative Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


NppStatus nppiFilterSobelCross_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point second cross derivative Sobel filter.
For common parameter descriptions, see Common parameters for nppiFilterSobel functions:.


### Image Filter Sobel Border


#### FilterSobelBorder


Filters the image using a Sobel filter kernel with border control.


##### Common parameters for nppiFilterSobelBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param eMaskSize
Enumeration value specifying the mask size.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


FilterSobelHorizBorder


Filters the image using a horizontal Sobel filter kernel with border control:



  \[\begin{split} \left( \begin{array}{rrr} 1 & 2 & 1 \\ 0 & 0 & 0 \\ -1 & -2 & -1 \\ \end{array} \right) \left( \begin{array}{rrrrr} 1 & 4 & 6 & 4 & 1 \\ 2 & 8 & 12 & 8 & 2 \\ 0 & 0 & 0 & 0 & 0 \\ -2 & -8 & -12 & -8 & -2 \\ -1 & -4 & -6 & -4 & -1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterSobelHorizBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed horizontal Sobel filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned horizontal Sobel filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point horizontal Sobel filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizBorder_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizMaskBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


FilterSobelVertBorder


Filters the image using a vertical Sobel filter kernel with border control:



  \[\begin{split} \left( \begin{array}{rrr} -1 & 0 & 1 \\ -2 & 0 & 2 \\ -1 & 0 & 1 \\ \end{array} \right) \left( \begin{array}{rrrrr} -1 & -2 & 0 & 2 & 1 \\ -4 & -8 & 0 & 8 & 4 \\ -6 & -12 & 0 & 12 & 6 \\ -4 & -8 & 0 & 8 & 4 \\ -1 & -2 & 0 & 2 & 1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterSobelVertBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed vertical Sobel filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned vertical Sobel filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point vertical Sobel filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertBorder_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertMaskBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


FilterSobelHorizSecondBorder


Filters the image using a second derivative, horizontal Sobel filter kernel with border control:



  \[\begin{split} \left( \begin{array}{rrr} 1 & 2 & 1 \\ -2 & -4 & -2 \\ 1 & 2 & 1 \\ \end{array} \right) \left( \begin{array}{rrrrr} 1 & 4 & 6 & 4 & 1 \\ 0 & 0 & 0 & 0 & 0 \\ -2 & -8 & -12 & -8 & -2 \\ 0 & 0 & 0 & 0 & 0 \\ 1 & 4 & 6 & 4 & 1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterSobelHorizSecondBorder_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed second derivative, horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizSecondBorder_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed second derivative, horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelHorizSecondBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point second derivative, horizontal Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


FilterSobelVertSecondBorder


Filters the image using a second derivative, vertical Sobel filter kernel with border control:



  \[\begin{split} \left( \begin{array}{rrr} 1 & -2 & 1 \\ 2 & -4 & 2 \\ 1 & -2 & 1 \\ \end{array} \right) \left( \begin{array}{rrrrr} 1 & 0 & -2 & 0 & 1 \\ 4 & 0 & -8 & 0 & 4 \\ 6 & 0 & -12 & 0 & 6 \\ 4 & 0 & -8 & 0 & 4 \\ 1 & 0 & -2 & 0 & 1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterSobelVertSecondBorder_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed second derivative, vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertSecondBorder_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed second derivative, vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelVertSecondBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point second derivative, vertical Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


FilterSobelCrossBorder


Filters the image using a second cross derivative Sobel filter kernel with border control:



  \[\begin{split} \left( \begin{array}{rrr} -1 & 0 & 1 \\ 0 & 0 & 0 \\ 1 & 0 & -1 \\ \end{array} \right) \left( \begin{array}{rrrrr} -1 & -2 & 0 & 2 & 1 \\ -2 & -4 & 0 & 4 & 2 \\ 0 & 0 & 0 & 0 & 0 \\ 2 & 4 & 0 & -4 & -2 \\ 1 & 2 & 0 & -2 & -1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterSobelCrossBorder_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed second cross derivative Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelCrossBorder_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed second cross derivative Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


NppStatus nppiFilterSobelCrossBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point second cross derivative Sobel filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSobelBorder functions:.


### Image Filter Roberts


#### FilterRoberts


Filters the image using a Roberts filter kernel.


##### Common parameters for nppiFilterRoberts functions:




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


FilterRobertsDown


Filters the image using a horizontal Roberts filter kernel:



  \[\begin{split} \left( \begin{array}{rrr} 0 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & -1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterRobertsDown_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned horizontal Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsDown_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned horizontal Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsDown_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned horizontal Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsDown_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned horizontal Roberts filter, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsDown_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 16-bit signed horizontal Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsDown_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 16-bit signed horizontal Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsDown_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed horizontal Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsDown_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed horizontal Roberts filter, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsDown_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point horizontal Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsDown_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point horizontal Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsDown_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point horizontal Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsDown_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point horizontal Roberts filter, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


FilterRobertsUp


Filters the image using a vertical Roberts filter kernel:



  \[\begin{split} \left( \begin{array}{rrr} 0 & 0 & 0 \\ 0 & 1 & 0 \\ -1 & 0 & 0 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterRobertsUp_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned vertical Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsUp_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned vertical Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsUp_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned vertical Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsUp_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned vertical Roberts filter, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsUp_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 16-bit signed vertical Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsUp_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 16-bit signed vertical Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsUp_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed vertical Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsUp_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed vertical Roberts filter, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsUp_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point vertical Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsUp_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point vertical Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsUp_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point vertical Roberts filter.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


NppStatus nppiFilterRobertsUp_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point vertical Roberts filter, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRoberts functions:.


### Image Filter Roberts Border


#### FilterRobertsBorder


Filters the image using a Roberts filter kernel with border control.


##### Common parameters for nppiFilterRobertsBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

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


FilterRobertsDownBorder


Filters the image using a horizontal Roberts filter kernel with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.



  \[\begin{split} \left( \begin{array}{rrr} 0 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & -1 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterRobertsDownBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned horizontal Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsDownBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned horizontal Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsDownBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned horizontal Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsDownBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned horizontal Roberts filter with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsDownBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed horizontal Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsDownBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed horizontal Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsDownBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed horizontal Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsDownBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed horizontal Roberts filter with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsDownBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point horizontal Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsDownBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point horizontal Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsDownBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point horizontal Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsDownBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point horizontal Roberts filter with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


FilterRobertsUpBorder


Filters the image using a vertical Roberts filter kernel with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.



  \[\begin{split} \left( \begin{array}{rrr} 0 & 0 & 0 \\ 0 & 1 & 0 \\ -1 & 0 & 0 \\ \end{array} \right) \end{split}\]
NppStatus nppiFilterRobertsUpBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned vertical Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsUpBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned vertical Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsUpBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned vertical Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsUpBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned vertical Roberts filter with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsUpBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed vertical Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsUpBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed vertical Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsUpBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed vertical Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsUpBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed vertical Roberts filter with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsUpBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point vertical Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsUpBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point vertical Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsUpBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point vertical Roberts filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


NppStatus nppiFilterRobertsUpBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point vertical Roberts filter with border control, ignoring alpha-channel.
For common parameter descriptions, see Common parameters for nppiFilterRobertsBorder functions:.


### Image Filter Laplace


#### FilterLaplace


Filters the image using a Laplacian filter kernel.


##### Common parameters for nppiFilterLaplace functions:



  \[\begin{split} \left( \begin{array}{rrr} -1 & -1 & -1 \\ -1 & 8 & -1 \\ -1 & -1 & -1 \\ \end{array} \right) \left( \begin{array}{rrrrr} -1 & -3 & -4 & -3 & -1 \\ -3 & 0 & 6 & 0 & -3 \\ -4 & 6 & 20 & 6 & -4 \\ -3 & 0 & 6 & 0 & -3 \\ -1 & -3 & -4 & -3 & -1 \\ \end{array} \right)\end{split}\]
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

param eMaskSize
Enumeration value specifying the mask size.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterLaplace_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned Laplace filter.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned Laplace filter.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Laplace filter.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Laplace filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 16-bit signed Laplace filter.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 16-bit signed Laplace filter.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Laplace filter.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Laplace filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point Laplace filter.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point Laplace filter.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point Laplace filter.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point Laplace filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed Laplace filter.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


NppStatus nppiFilterLaplace_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed Laplace filter.
For common parameter descriptions, see Common parameters for nppiFilterLaplace functions:.


### Image Filter Laplace Border


#### FilterLaplaceBorder


Filters the image using a Laplacian filter kernel with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterLaplaceBorder functions:



  \[\begin{split} \left( \begin{array}{rrr} -1 & -1 & -1 \\ -1 & 8 & -1 \\ -1 & -1 & -1 \\ \end{array} \right) \left( \begin{array}{rrrrr} -1 & -3 & -4 & -3 & -1 \\ -3 & 0 & 6 & 0 & -3 \\ -4 & 6 & 20 & 6 & -4 \\ -3 & 0 & 6 & 0 & -3 \\ -1 & -3 & -4 & -3 & -1 \\ \end{array} \right)\end{split}\]
param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param eMaskSize
Enumeration value specifying the mask size.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterLaplaceBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned Laplace filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned Laplace filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Laplace filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Laplace filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed Laplace filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed Laplace filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Laplace filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Laplace filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point Laplace filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point Laplace filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point Laplace filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point Laplace filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_8u16s_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned to 16-bit signed Laplace filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


NppStatus nppiFilterLaplaceBorder_8s16s_C1R_Ctx(const Npp8s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit signed to 16-bit signed Laplace filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterLaplaceBorder functions:.


### Image Filter Gauss


#### FilterGauss


Filters the image using a Gaussian filter kernel. Use FilterGaussAdvanced if you want to supply your own filter coefficients.


Note that all FilterGauss functions currently support mask sizes up to 15x15. Filter kernels for these functions are calculated using a sigma value of 0.4F + (mask width / 2) * 0.6F.


##### Common parameters for nppiFilterGauss functions:




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

param eMaskSize
Enumeration value specifying the mask size.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterGauss_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Gauss filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned Gauss filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 16-bit signed Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 16-bit signed Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Gauss filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


NppStatus nppiFilterGauss_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point Gauss filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGauss functions:.


### Image Filter Gauss Advanced


#### FilterGaussAdvanced


Filters the image using a separable Gaussian filter kernel with user supplied floating point coefficients:


##### Common parameters for nppiFilterGaussAdvanced functions:




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

param nFilterTaps
The number of filter taps where nFilterTaps = 2 * ((int)((float)ceil(radius) + 0.5F) ) + 1.

param pKernel
Pointer to an array of nFilterTaps kernel coefficients which sum to 1.0F.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterGaussAdvanced_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Gauss filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned Gauss filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Single channel 16-bit signed Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Three channel 16-bit signed Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Gauss filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point Gauss filter.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


NppStatus nppiFilterGaussAdvanced_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point Gauss filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvanced functions:.


### Image Filter Gauss Border


#### FilterGaussBorder


Filters the image using a Gaussian filter kernel with border control. Use FilterGaussAdvancedBorder if you want to supply your own filter coefficients.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


Note that all FilterGaussBorder functions currently support mask sizes up to 15x15. Filter kernels for these functions are calculated using a sigma value of 0.4F + (mask width / 2) * 0.6F.


##### Common parameters for nppiFilterGaussBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Full source image width and height in pixels.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param eMaskSize
Enumeration value specifying the mask size.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterGaussBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Gauss filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned Gauss filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Gauss filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


NppStatus nppiFilterGaussBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point Gauss filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGaussBorder functions:.


### Image Filter Advanced Gauss Border


#### FilterGaussAdvancedBorder


Filters the image using a separable Gaussian filter kernel with user supplied floating point coefficients with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Note that the performance of these functions can drop significantly for filter kernels with a very large number of taps.


Currently only the NPP_BORDER_REPLICATE and NPP_BORDER_MIRROR border type operations are supported.


##### Common parameters for nppiFilterGaussAdvancedBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Full source image width and height in pixels.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param nFilterTaps
The number of filter taps where nFilterTaps = 2 * ((int)((float)ceil(radius) + 0.5F) ) + 1.

param pKernel
Pointer to an array of nFilterTaps kernel coefficients which sum to 1.0F.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterGaussAdvancedBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Gauss filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned Gauss filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Gauss filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


NppStatus nppiFilterGaussAdvancedBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point Gauss filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterGaussAdvancedBorder functions:.


### Image Filter Gauss Pyramid Layer Down Border


#### FilterGaussPyramidLayerDownBorder


Filters the image using a separable Gaussian filter kernel with user supplied floating point coefficients with downsampling and border control.


If the downsampling rate is equivalent to an integer value then unnecessary source pixels are just skipped. If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_MIRROR and NPP_BORDER_REPLICATE border type operations are supported.


##### Common parameters for nppiFilterGaussPyramidLayerDownBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param nRate
The downsampling rate to be used. For integer equivalent rates unnecessary source pixels are just skipped. For non-integer rates the source image is bilinear interpolated. nRate must be > 1.0F and <= 10.0F.

param nFilterTaps
The number of filter taps where nFilterTaps = 2 * ((int)((float)ceil(radius) + 0.5F) ) + 1.

param pKernel
Pointer to an array of nFilterTaps kernel coefficients which sum to 1.0F.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiGetFilterGaussPyramidLayerDownBorderDstROI(int nSrcROIWidth, int nSrcROIHeight, NppiSize *pDstSizeROI, Npp32f nRate)
Calculate destination image SizeROI width and height from source image ROI width and height and downsampling rate.
It is highly recommended that this function be use to determine the destination image ROI for consistent results.

Parameters

nSrcROIWidth – The desired source image ROI width, must be <= oSrcSize.width.
nSrcROIHeight – The desired source image ROI height, must be <= oSrcSize.height.
pDstSizeROI – Host memory pointer to the destination image roi_specification.
nRate – The downsampling or upsampling rate to be used. For integer equivalent rates unnecessary source pixels are just skipped. For non-integer rates the source image is bilinear interpolated. nRate must be > 1.0F and <= 10.0F.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFilterGaussPyramidLayerDownBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRate, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned Gauss filter with downsampling and border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussPyramidLayerDownBorder functions:.


NppStatus nppiFilterGaussPyramidLayerDownBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRate, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned Gauss filter with downsampling and border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussPyramidLayerDownBorder functions:.


NppStatus nppiFilterGaussPyramidLayerDownBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRate, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned Gauss filter with downsampling and border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussPyramidLayerDownBorder functions:.


NppStatus nppiFilterGaussPyramidLayerDownBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRate, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned Gauss filter with downsampling and border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussPyramidLayerDownBorder functions:.


NppStatus nppiFilterGaussPyramidLayerDownBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRate, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point Gauss filter downsampling and with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussPyramidLayerDownBorder functions:.


NppStatus nppiFilterGaussPyramidLayerDownBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRate, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point Gauss filter with downsampling and border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussPyramidLayerDownBorder functions:.


### Image Filter Gauss Pyramid Layer Up Border


#### FilterGaussPyramidLayerUpBorder


Filters the image using a separable Gaussian filter kernel with user supplied floating point coefficients with upsampling and border control.


If the upsampling rate is equivalent to an integer value then unnecessary source pixels are just skipped. If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_MIRROR and NPP_BORDER_REPLICATE border type operations are supported.


##### Common parameters for nppiFilterGaussPyramidLayerUpBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param nRate
The upsampling rate to be used. For integer equivalent rates unnecessary source pixels are just skipped. For non-integer rates the source image is bilinear interpolated. nRate must be > 1.0F and <= 10.0F.

param nFilterTaps
The number of filter taps where nFilterTaps = 2 * ((int)((float)ceil(radius) + 0.5F) ) + 1.

param pKernel
Pointer to an array of nFilterTaps kernel coefficients which sum to 1.0F.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiGetFilterGaussPyramidLayerUpBorderDstROI(int nSrcROIWidth, int nSrcROIHeight, NppiSize *pDstSizeROIMin, NppiSize *pDstSizeROIMax, Npp32f nRate)
Calculate destination image minimum and maximum SizeROI width and height from source image ROI width and height and upsampling rate.
It is highly recommended that this function be use to determine the best destination image ROI for consistent results.

Parameters

nSrcROIWidth – The desired source image ROI width, must be <= oSrcSize.width.
nSrcROIHeight – The desired source image ROI height, must be <= oSrcSize.height.
pDstSizeROIMin – Host memory pointer to the minimum recommended destination image roi_specification.
pDstSizeROIMax – Host memory pointer to the maximum recommended destination image roi_specification.
nRate – The upsampling rate to be used. For integer equivalent rates unnecessary source pixels are just skipped. For non-integer rates the source image is bilinear interpolated. nRate must be > 1.0F and <= 10.0F.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFilterGaussPyramidLayerUpBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRate, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned Gauss filter with upsampling and border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussPyramidLayerUpBorder functions:.


NppStatus nppiFilterGaussPyramidLayerUpBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRate, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned Gauss filter with upsampling and border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussPyramidLayerUpBorder functions:.


NppStatus nppiFilterGaussPyramidLayerUpBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRate, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned Gauss filter with upsampling and border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussPyramidLayerUpBorder functions:.


NppStatus nppiFilterGaussPyramidLayerUpBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRate, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned Gauss filter with upsampling and border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussPyramidLayerUpBorder functions:.


NppStatus nppiFilterGaussPyramidLayerUpBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRate, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point Gauss filter upsampling and with border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussPyramidLayerUpBorder functions:.


NppStatus nppiFilterGaussPyramidLayerUpBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRate, const int nFilterTaps, const Npp32f *pKernel, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point Gauss filter with upsampling and border control.
For common parameter descriptions, see Common parameters for nppiFilterGaussPyramidLayerUpBorder functions:.


### Image Filter Bilateral Gauss Border


#### FilterBilateralGaussBorder


Filters the image using a bilateral Gaussian filter kernel with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


For this filter the anchor point is always the central element of the kernel. Coefficients of the bilateral filter kernel depend on their position in the kernel and on the value of some source image pixels overlayed by the filter kernel. Only source image pixels with both coordinates divisible by nDistanceBetweenSrcPixels are used in calculations.


The value of an output pixel \(d\) is

  \[d = \frac{\sum_{h=-nRadius}^{nRadius}\sum_{w=-nRadius}^{nRadius}W1(h,w)\cdot W2(h,w)\cdot S(h,w)}{\sum_{h=-nRadius}^{nRadius}\sum_{w=-nRadius}^{nRadius}W1(h,w)\cdot W2(h,w)}\] where h and w are the corresponding kernel width and height indexes, S(h,w) is the value of the source image pixel overlayed by filter kernel position (h,w), W1(h,w) is func(nValSquareSigma, (S(h,w) - S(0,0))) where S(0,0) is the value of the source image pixel at the center of the kernel, W2(h,w) is func(nPosSquareSigma, sqrt(h*h+w*w)), and func is the following formula  \[func(S,I) = exp(-\frac{I^2}{2.0F\cdot S^2})\]
Currently only the NPP_BORDER_REPLICATE border type operations are supported.


##### Common parameters for nppiFilterBilateralGaussBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param nRadius
The radius of the round filter kernel to be used. A radius of 1 indicates a filter kernel size of 3 by 3, 2 indicates 5 by 5, etc. Radius values from 1 to 32 are supported.

param nStepBetweenSrcPixels
The step size between adjacent source image pixels processed by the filter kernel, most commonly 1.

param nValSquareSigma
The square of the sigma for the relative intensity distance between a source image pixel in the filter kernel and the source image pixel at the center of the filter kernel.

param nPosSquareSigma
The square of the sigma for the relative geometric distance between a source image pixel in the filter kernel and the source image pixel at the center of the filter kernel.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterBilateralGaussBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nRadius, const int nStepBetweenSrcPixels, const Npp32f nValSquareSigma, const Npp32f nPosSquareSigma, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned bilateral Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBilateralGaussBorder functions:.


NppStatus nppiFilterBilateralGaussBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nRadius, const int nStepBetweenSrcPixels, const Npp32f nValSquareSigma, const Npp32f nPosSquareSigma, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned bilateral Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBilateralGaussBorder functions:.


NppStatus nppiFilterBilateralGaussBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nRadius, const int nStepBetweenSrcPixels, const Npp32f nValSquareSigma, const Npp32f nPosSquareSigma, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned bilateral Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBilateralGaussBorder functions:.


NppStatus nppiFilterBilateralGaussBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nRadius, const int nStepBetweenSrcPixels, const Npp32f nValSquareSigma, const Npp32f nPosSquareSigma, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned bilateral Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBilateralGaussBorder functions:.


NppStatus nppiFilterBilateralGaussBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nRadius, const int nStepBetweenSrcPixels, const Npp32f nValSquareSigma, const Npp32f nPosSquareSigma, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
One channel 32-bit floating-point bilateral Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBilateralGaussBorder functions:.


NppStatus nppiFilterBilateralGaussBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, const int nRadius, const int nStepBetweenSrcPixels, const Npp32f nValSquareSigma, const Npp32f nPosSquareSigma, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point bilateral Gauss filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterBilateralGaussBorder functions:.


### Image Filter High Pass


#### FilterHighPass


Filters the image using a high-pass filter kernel.


##### Common parameters for nppiFilterHighPass functions:



  \[\begin{split} \left( \begin{array}{rrr} -1 & -1 & -1 \\ -1 & 8 & -1 \\ -1 & -1 & -1 \\ \end{array} \right) \left( \begin{array}{rrrrr} -1 & -1 & -1 & -1 & -1 \\ -1 & -1 & -1 & -1 & -1 \\ -1 & -1 & 24 & -1 & -1 \\ -1 & -1 & -1 & -1 & -1 \\ -1 & -1 & -1 & -1 & -1 \\ \end{array} \right) \end{split}\]
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

param eMaskSize
Enumeration value specifying the mask size.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterHighPass_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 16-bit signed high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 16-bit signed high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit signed high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit signed high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


NppStatus nppiFilterHighPass_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterHighPass functions:.


### Image Filter High Pass Border


#### FilterHighPassBorder


Filters the image using a high-pass filter kernel with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterHighPassBorder functions:



  \[\begin{split} \left( \begin{array}{rrr} -1 & -1 & -1 \\ -1 & 8 & -1 \\ -1 & -1 & -1 \\ \end{array} \right) \left( \begin{array}{rrrrr} -1 & -1 & -1 & -1 & -1 \\ -1 & -1 & -1 & -1 & -1 \\ -1 & -1 & 24 & -1 & -1 \\ -1 & -1 & -1 & -1 & -1 \\ -1 & -1 & -1 & -1 & -1 \\ \end{array} \right) \end{split}\]
param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param eMaskSize
Enumeration value specifying the mask size.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterHighPassBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


NppStatus nppiFilterHighPassBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterHighPassBorder functions:.


### Image Filter Low Pass


#### FilterLowPass


Filters the image using a low-pass filter kernel.


##### Common parameters for nppiFilterLowPass functions:



  \[\begin{split} \left( \begin{array}{rrr} 1/9 & 1/9 & 1/9 \\ 1/9 & 1/9 & 1/9 \\ 1/9 & 1/9 & 1/9 \\ \end{array} \right) \left( \begin{array}{rrrrr} 1/25 & 1/25 & 1/25 & 1/25 & 1/25 \\ 1/25 & 1/25 & 1/25 & 1/25 & 1/25 \\ 1/25 & 1/25 & 1/25 & 1/25 & 1/25 \\ 1/25 & 1/25 & 1/25 & 1/25 & 1/25 \\ 1/25 & 1/25 & 1/25 & 1/25 & 1/25 \\ \end{array} \right) \end{split}\]
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

param eMaskSize
Enumeration value specifying the mask size.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterLowPass_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned low-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned low-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned low-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned low-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned low-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned low-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned low-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned low-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 16-bit signed low-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 16-bit signed low-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit signed low-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 16-bit signed low-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point low-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point low-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point low-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


NppStatus nppiFilterLowPass_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLowPass functions:.


### Image Filter Low Pass Border


#### FilterLowPassBorder


Filters the image using a low-pass filter kernel with border control.


If any portion of the mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterLowPassBorder functions:



  \[\begin{split} \left( \begin{array}{rrr} 1/9 & 1/9 & 1/9 \\ 1/9 & 1/9 & 1/9 \\ 1/9 & 1/9 & 1/9 \\ \end{array} \right) \left( \begin{array}{rrrrr} 1/25 & 1/25 & 1/25 & 1/25 & 1/25 \\ 1/25 & 1/25 & 1/25 & 1/25 & 1/25 \\ 1/25 & 1/25 & 1/25 & 1/25 & 1/25 \\ 1/25 & 1/25 & 1/25 & 1/25 & 1/25 \\ 1/25 & 1/25 & 1/25 & 1/25 & 1/25 \\ \end{array} \right) \end{split}\]
param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param eMaskSize
Enumeration value specifying the mask size.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterLowPassBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point high-pass filter.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


NppStatus nppiFilterLowPassBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point high-pass filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterLowPassBorder functions:.


### Image Filter Sharpen


#### FilterSharpen


Filters the image using a sharpening filter kernel:


##### Common parameters for nppiFilterSharpen functions:



  \[\begin{split} \left( \begin{array}{rrr} -1/8 & -1/8 & -1/8 \\ -1/8 & 16/8 & -1/8 \\ -1/8 & -1/8 & -1/8 \\ \end{array} \right) \end{split}\]
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


NppStatus nppiFilterSharpen_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned sharpening filter.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned sharpening filter.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned sharpening filter.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned sharpening filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned sharpening filter.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned sharpening filter.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned sharpening filter.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned sharpening filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 16-bit signed sharpening filter.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 16-bit signed sharpening filter.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed sharpening filter.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 16-bit signed sharpening filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point sharpening filter.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point sharpening filter.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point sharpening filter.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


NppStatus nppiFilterSharpen_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point sharpening filter, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSharpen functions:.


### Image Filter Sharpen Border


#### FilterSharpenBorder


Filters the image using a sharpening filter kernel with border control.


If any portion of the 3x3 mask overlaps the source image boundary the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterSharpenBorder functions:



  \[\begin{split} \left( \begin{array}{rrr} -1/8 & -1/8 & -1/8 \\ -1/8 & 16/8 & -1/8 \\ -1/8 & -1/8 & -1/8 \\ \end{array} \right) \end{split}\]
param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

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


NppStatus nppiFilterSharpenBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned sharpening filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned sharpening filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned sharpening filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned sharpening filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned sharpening filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned sharpening filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned sharpening filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned sharpening filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed sharpening filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed sharpening filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed sharpening filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed sharpening filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit floating-point sharpening filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit floating-point sharpening filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point sharpening filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


NppStatus nppiFilterSharpenBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit floating-point sharpening filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterSharpenBorder functions:.


### Image Filter Unsharp Border


#### FilterUnsharpBorder


Filters the image using a unsharp-mask sharpening filter kernel with border control.


The algorithm involves the following steps: Smooth the original image with a Gaussian filter, with the width controlled by the nRadius. Subtract the smoothed image from the original to create a high-pass filtered image. Apply any clipping needed on the high-pass image, as controlled by the nThreshold. Add a certain percentage of the high-pass filtered image to the original image, with the percentage controlled by the nWeight. In pseudocode this algorithm can be written as: HighPass = Image - Gaussian(Image) Result = Image + nWeight * HighPass * ( |HighPass| >= nThreshold ) where nWeight is the amount, nThreshold is the threshold, and >= indicates a Boolean operation, 1 if true, or 0 otherwise.


If any portion of the mask overlaps the source image boundary, the requested border type operation is applied to all mask pixels which fall outside of the source image.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### . Common parameters for nppiFilterUnsharpBorder functions:




##### . Common parameters for nppiFilterUnsharpGetBufferSize functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param nRadius
The radius of the Gaussian filter, in pixles, not counting the center pixel.

param nSigma
The standard deviation of the Gaussian filter, in pixel.

param nWeight
The percentage of the difference between the original and the high pass image that is added back into the original.

param nThreshold
The threshold neede to apply the difference amount.

param eBorderType
The border type operation to be applied at source image border boundaries.

param pDeviceBuffer
Pointer to the user-allocated device scratch buffer required for the unsharp operation.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes

param nRadius
The radius of the Gaussian filter, in pixles, not counting the center pixel.

param nSigma
The standard deviation of the Gaussian filter, in pixel.

param hpBufferSize
Pointer to the size of the scratch buffer required for the unsharp operation.

return
Image Data Related Error Codes


Functions


NppStatus nppiFilterUnsharpBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned unsharp filter.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned unsharp filter.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned unsharp filter.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned unsharp filter (alpha channel is not processed).
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_16u_C1R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Single channel 16-bit unsigned unsharp filter.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_16u_C3R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned unsharp filter.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_16u_C4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned unsharp filter.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_16u_AC4R_Ctx(const Npp16u *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp16u *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned unsharp filter (alpha channel is not processed).
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Single channel 16-bit signed unsharp filter.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Single channel 16-bit signed unsharp filter.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four channel 16-bit signed unsharp filter.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four channel 16-bit signed unsharp filter (alpha channel is not processed).
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Single channel 32-bit floating point unsharp filter.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Three channel 32-bit floating point unsharp filter.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four channel 32-bit floating point unsharp filter.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, Npp32f nRadius, Npp32f nSigma, Npp32f nWeight, Npp32f nThreshold, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Four channel 32-bit floating point unsharp filter (alpha channel is not processed).
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpBorder functions:.


NppStatus nppiFilterUnsharpGetBufferSize_8u_C1R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Single channel 8-bit unsigned unsharp filter scratch memory size.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_8u_C3R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Three channel 8-bit unsigned unsharp filter scratch memory size.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_8u_C4R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Four channel 8-bit unsigned unsharp filter scratch memory size.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_8u_AC4R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Four channel 8-bit unsigned unsharp filter scratch memory size (alpha channel is not processed).
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_16u_C1R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Single channel 16-bit unsigned unsharp filter scratch memory size.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_16u_C3R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Three channel 16-bit unsigned unsharp filter scratch memory size.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_16u_C4R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Four channel 16-bit unsigned unsharp filter scratch memory size.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_16u_AC4R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Four channel 16-bit unsigned unsharp filter scratch memory size (alpha channel is not processed).
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_16s_C1R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Single channel 16-bit signed unsharp filter scratch memory size.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_16s_C3R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Three channel 16-bit signed unsharp filter scratch memory size.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_16s_C4R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Four channel 16-bit signed unsharp filter scratch memory size.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_16s_AC4R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Four channel 16-bit signed unsharp filter scratch memory size (alpha channel is not processed).
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_32f_C1R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Single channel 32-bit floating point unsharp filter scratch memory size.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_32f_C3R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Three channel 32-bit floating point unsharp filter scratch memory size.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_32f_C4R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Four channel 32-bit floating point unsharp filter scratch memory size.
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


NppStatus nppiFilterUnsharpGetBufferSize_32f_AC4R(const Npp32f nRadius, const Npp32f nSigma, int *hpBufferSize)
Four channel 32-bit floating point unsharp filter scratch memory size (alpha channel is not processed).
For common parameter descriptions, see . Common parameters for nppiFilterUnsharpGetBufferSize functions:.


### Image Filter Wiener Border


#### FilterWienerBorder


Noise removal filtering of an image using an adaptive Wiener filter with border control.


Pixels under the source mask are used to generate statistics about the local neighborhood which are then used to control the amount of adaptive noise filtering locally applied.


Note that if the noise value for a particular channel is set to 0.0f then the output for that channel will contain the square of the variance of local pixels within aMaskSize surrounding each pixel in oSizeROI. Note that is unlikely to be useful unless the pixel data type is floating point due to result clamping. Output from these cases can then be passed through an nppiMean function call using the same oSizeROI. The square root for that channel from the nppiMean call result can then be used as a noise value for a future call to this function if there is no known preexisting noise value.


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterWienerBorder functions:


For each pixel in the source image the function estimates the local mean and variance in the neighborhood defined by oMaskSize relative to the primary source pixel located at oAnchor.x and oAnchor.y. Given an oMaskSize with width \(W\) and height \(H\), the mean, variance, and destination pixel value will be computed per channel as

  \[Mean = \frac{1}{W\cdot H}\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}pSrc(j,i)\]  \[Variance^2 = \frac{1}{W\cdot H}\sum_{j=0}^{H-1}\sum_{i=0}^{W-1}(pSrc(j,i)^2-Mean^2)\]  \[pDst(j,i) = Mean+\frac{(Variance^2-NoiseVariance^2)}{Variance^2}\cdot {(pSrc(j,i)-Mean)}\]
param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param oMaskSize
Pixel Width and Height of the rectangular region of interest surrounding the source pixel.

param oAnchor
Positive X and Y relative offsets of primary pixel in region of interest surrounding the source pixel relative to bottom right of oMaskSize.

param aNoise
Fixed size array of per-channel noise variance level value in range of 0.0F to 1.0F.

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiFilterWienerBorder_8u_C1R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp32f aNoise[1], NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 8-bit unsigned Wiener filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterWienerBorder functions:.


NppStatus nppiFilterWienerBorder_8u_C3R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp32f aNoise[3], NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned Wiener filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterWienerBorder functions:.


NppStatus nppiFilterWienerBorder_8u_C4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp32f aNoise[4], NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Wiener filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterWienerBorder functions:.


NppStatus nppiFilterWienerBorder_8u_AC4R_Ctx(const Npp8u *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp32f aNoise[3], NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned Wiener filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterWienerBorder functions:.


NppStatus nppiFilterWienerBorder_16s_C1R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp32f aNoise[1], NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 16-bit signed Wiener filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterWienerBorder functions:.


NppStatus nppiFilterWienerBorder_16s_C3R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp32f aNoise[3], NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 16-bit signed Wiener filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterWienerBorder functions:.


NppStatus nppiFilterWienerBorder_16s_C4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp32f aNoise[4], NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Wiener filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterWienerBorder functions:.


NppStatus nppiFilterWienerBorder_16s_AC4R_Ctx(const Npp16s *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp32f aNoise[3], NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 16-bit signed Wiener filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterWienerBorder functions:.


NppStatus nppiFilterWienerBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp32f aNoise[1], NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Single channel 32-bit float Wiener filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterWienerBorder functions:.


NppStatus nppiFilterWienerBorder_32f_C3R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp32f aNoise[3], NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Three channel 32-bit float Wiener filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterWienerBorder functions:.


NppStatus nppiFilterWienerBorder_32f_C4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp32f aNoise[4], NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit float Wiener filter with border control.
For common parameter descriptions, see Common parameters for nppiFilterWienerBorder functions:.


NppStatus nppiFilterWienerBorder_32f_AC4R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiSize oMaskSize, NppiPoint oAnchor, Npp32f aNoise[3], NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
Four channel 32-bit float Wiener filter with border control, ignoring alpha channel.
For common parameter descriptions, see Common parameters for nppiFilterWienerBorder functions:.


### Image Filter Gradient Vector Prewitt Border


#### GradientVectorPrewittBorder




RGB Color to Prewitt Gradient Vector conversion using user selected fixed mask size and gradient distance method. Functions support up to 4 optional single channel output gradient vectors, X (vertical), Y (horizontal), magnitude, and angle with user selectable distance methods. Output for a particular vector is disabled by supplying a NULL pointer for that vector. X and Y gradient vectors are in cartesian form in the destination data type.


Magnitude vectors are polar gradient form in the destination data type, angle is always in floating point polar gradient format. Only fixed mask sizes of 3x3 are supported. Only nppiNormL1 (sum) and nppiNormL2 (sqrt of sum of squares) distance methods are currently supported.


Currently only the NPP_BORDER_REPLICATE border type operation is supported. Borderless output can be accomplished by using a larger source image than the destination and adjusting oSrcSize and oSrcOffset parameters accordingly.


##### Common parameters for nppiFilterGradientVectorPrewittBorder functions:


The following fixed kernel mask is used for producing the pDstX (vertical) output image.



  \[\begin{split} \left( \begin{array}{rrr} -1 & 0 & 1 \\ -1 & 0 & 1 \\ -1 & 0 & 1 \\ \end{array} \right) \end{split}\]
The following fixed kernel mask is used for producing the pDstY (horizontal) output image.



  \[\begin{split} \left( \begin{array}{rrr} 1 & 1 & 1 \\ 0 & 0 & 0 \\ -1 & -1 & -1 \\ \end{array} \right) \end{split}\]
For the C1R versions of the function the pDstMag output image value for L1 normalization consists of the absolute value of the pDstX value plus the absolute value of the pDstY value at that particular image pixel location. For the C1R versions of the function the pDstMag output image value for L2 normalization consists of the square root of the pDstX value squared plus the pDstY value squared at that particular image pixel location. For the C1R versions of the function the pDstAngle output image value consists of the arctangent (atan2) of the pDstY value and the pDstX value at that particular image pixel location.


For the C3C1R versions of the function, regardless of the selected normalization method, the L2 normalization value is first determined for each or the pDstX and pDstY values for each source channel then the largest L2 normalization value (largest gradient) is used to select which of the 3 pDstX channel values are output to the pDstX image or pDstY channel values are output to the pDstY image. For the C3C1R versions of the function the pDstMag output image value for L1 normalizaton consists of the same technique used for the C1R version for each source image channel. Then the largest L2 normalization value is again used to select which of the 3 pDstMag channel values to output to the pDstMag image. For the C3C1R versions of the function the pDstMag output image value for L2 normalizaton consists of just outputting the largest per source channel L2 normalization value to the pDstMag image. For the C3C1R versions of the function the pDstAngle output image value consists of the same technique used for the C1R version calculated for each source image channel. Then the largest L2 normalization value is again used to select which of the 3 angle values to output to the pDstAngle image.


param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDstX
X vector destination_image_pointer.

param nDstXStep
X vector destination_image_line_step.

param pDstY
Y vector destination_image_pointer.

param nDstYStep
Y vector destination_image_line_step.

param pDstMag
magnitude destination_image_pointer.

param nDstMagStep
magnitude destination_image_line_step.

param pDstAngle
angle destination_image_pointer.

param nDstAngleStep
angle destination_image_line_step.

param oSizeROI
Region-Of-Interest (ROI).

param eMaskSize
fixed filter mask size to use.

param eNorm
gradient distance method to use.

param eBorderType
source image border type to use use.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiGradientVectorPrewittBorder_8u16s_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDstX, int nDstXStep, Npp16s *pDstY, int nDstYStep, Npp16s *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned packed RGB to optional 1 channel 16-bit signed X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorPrewittBorder functions:.


NppStatus nppiGradientVectorPrewittBorder_8u16s_C3C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDstX, int nDstXStep, Npp16s *pDstY, int nDstYStep, Npp16s *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to optional 1 channel 16-bit signed X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorPrewittBorder functions:.


NppStatus nppiGradientVectorPrewittBorder_16s32f_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit signed packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorPrewittBorder functions:.


NppStatus nppiGradientVectorPrewittBorder_16s32f_C3C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 16-bit signed packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorPrewittBorder functions:.


NppStatus nppiGradientVectorPrewittBorder_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorPrewittBorder functions:.


NppStatus nppiGradientVectorPrewittBorder_16u32f_C3C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorPrewittBorder functions:.


NppStatus nppiGradientVectorPrewittBorder_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorPrewittBorder functions:.


NppStatus nppiGradientVectorPrewittBorder_32f_C3C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorPrewittBorder functions:.


### Image Filter Gradient Vector Scharr Border


#### GradientVectorScharrBorder




RGB Color to Scharr Gradient Vector conversion using user selected fixed mask size and gradient distance method. Functions support up to 4 optional single channel output gradient vectors, X (vertical), Y (horizontal), magnitude, and angle with user selectable distance methods. Output for a particular vector is disabled by supplying a NULL pointer for that vector. X and Y gradient vectors are in cartesian form in the destination data type.


Magnitude vectors are polar gradient form in the destination data type, angle is always in floating point polar gradient format. Only fixed mask sizes of 3x3 are supported. Only nppiNormL1 (sum) and nppiNormL2 (sqrt of sum of squares) distance methods are currently supported.


Currently only the NPP_BORDER_REPLICATE border type operation is supported. Borderless output can be accomplished by using a larger source image than the destination and adjusting oSrcSize and oSrcOffset parameters accordingly.


##### Common parameters for nppiFilterGradientVectorScharrBorder functions:


The following fixed kernel mask is used for producing the pDstX (vertical) output image.



  \[\begin{split} \left( \begin{array}{rrr} 3 & 0 & -3 \\ 10 & 0 & -10 \\ 3 & 0 & -3 \\ \end{array} \right) \end{split}\]
The following fixed kernel mask is used for producing the pDstY (horizontal) output image.



  \[\begin{split} \left( \begin{array}{rrr} 3 & 10 & 3 \\ 0 & 0 & 0 \\ -3 & -10 & -3 \\ \end{array} \right) \end{split}\]
For the C1R versions of the function the pDstMag output image value for L1 normalization consists of the absolute value of the pDstX value plus the absolute value of the pDstY value at that particular image pixel location. For the C1R versions of the function the pDstMag output image value for L2 normalization consists of the square root of the pDstX value squared plus the pDstY value squared at that particular image pixel location. For the C1R versions of the function the pDstAngle output image value consists of the arctangent (atan2) of the pDstY value and the pDstX value at that particular image pixel location.


For the C3C1R versions of the function, regardless of the selected normalization method, the L2 normalization value is first determined for each or the pDstX and pDstY values for each source channel then the largest L2 normalization value (largest gradient) is used to select which of the 3 pDstX channel values are output to the pDstX image or pDstY channel values are output to the pDstY image. For the C3C1R versions of the function the pDstMag output image value for L1 normalizaton consists of the same technique used for the C1R version for each source image channel. Then the largest L2 normalization value is again used to select which of the 3 pDstMag channel values to output to the pDstMag image. For the C3C1R versions of the function the pDstMag output image value for L2 normalizaton consists of just outputting the largest per source channel L2 normalization value to the pDstMag image. For the C3C1R versions of the function the pDstAngle output image value consists of the same technique used for the C1R version calculated for each source image channel. Then the largest L2 normalization value is again used to select which of the 3 angle values to output to the pDstAngle image.


param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDstX
X vector destination_image_pointer.

param nDstXStep
X vector destination_image_line_step.

param pDstY
Y vector destination_image_pointer.

param nDstYStep
Y vector destination_image_line_step.

param pDstMag
magnitude destination_image_pointer.

param nDstMagStep
magnitude destination_image_line_step.

param pDstAngle
angle destination_image_pointer.

param nDstAngleStep
angle destination_image_line_step.

param oSizeROI
Region-Of-Interest (ROI).

param eMaskSize
fixed filter mask size to use.

param eNorm
gradient distance method to use.

param eBorderType
source image border type to use use.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiGradientVectorScharrBorder_8u16s_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDstX, int nDstXStep, Npp16s *pDstY, int nDstYStep, Npp16s *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned packed RGB to optional 1 channel 16-bit signed X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorScharrBorder functions:.


NppStatus nppiGradientVectorScharrBorder_8u16s_C3C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDstX, int nDstXStep, Npp16s *pDstY, int nDstYStep, Npp16s *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to optional 1 channel 16-bit signed X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorScharrBorder functions:.


NppStatus nppiGradientVectorScharrBorder_16s32f_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit signed packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorScharrBorder functions:.


NppStatus nppiGradientVectorScharrBorder_16s32f_C3C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 16-bit signed packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorScharrBorder functions:.


NppStatus nppiGradientVectorScharrBorder_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorScharrBorder functions:.


NppStatus nppiGradientVectorScharrBorder_16u32f_C3C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorScharrBorder functions:.


NppStatus nppiGradientVectorScharrBorder_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorScharrBorder functions:.


NppStatus nppiGradientVectorScharrBorder_32f_C3C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorScharrBorder functions:.


### Image Filter Gradient Vector Sobel Border


#### GradientVectorSobelBorder




RGB Color to Sobel Gradient Vector conversion using user selected fixed mask size and gradient distance method. Functions support up to 4 optional single channel output gradient vectors, X (vertical), Y (horizontal), magnitude, and angle with user selectable distance methods. Output for a particular vector is disabled by supplying a NULL pointer for that vector. X and Y gradient vectors are in cartesian form in the destination data type.


Magnitude vectors are polar gradient form in the destination data type, angle is always in floating point polar gradient format. Only fixed mask sizes of 3x3 and 5x5 are supported. Only nppiNormL1 (sum) and nppiNormL2 (sqrt of sum of squares) distance methods are currently supported.


Currently only the NPP_BORDER_REPLICATE border type operation is supported. Borderless output can be accomplished by using a larger source image than the destination and adjusting oSrcSize and oSrcOffset parameters accordingly.


##### Common parameters for nppiFilterGradientVectorSobelBorder functions:


One of the following fixed kernel masks are used for producing the 3x3 or 5x5 pDstX (vertical) output image depending on selected mask size.



  \[\begin{split} \left( \begin{array}{rrr} -1 & 0 & 1 \\ -2 & 0 & 2 \\ -1 & 0 & 1 \\ \end{array} \right) \end{split}\]

  \[\begin{split} \left( \begin{array}{rrrrr} -1 & -2 & 0 & 2 & 1 \\ -4 & -8 & 0 & 8 & 4 \\ -6 & -12 & 0 & 12 & 6 \\ -4 & -8 & 0 & 8 & 4 \\ -1 & -2 & 0 & 2 & 1 \\ \end{array} \right) \end{split}\]
One of the following fixed kernel masks are used for producing the 3x3 or 5x5 pDstY (horizontal) output image depending on selected mask size.



  \[\begin{split} \left( \begin{array}{rrr} 1 & 2 & 1 \\ 0 & 0 & 0 \\ -1 & -2 & -1 \\ \end{array} \right) \end{split}\]

  \[\begin{split} \left( \begin{array}{rrrrr} 1 & 4 & 6 & 4 & 1 \\ 2 & 8 & 12 & 8 & 2 \\ 0 & 0 & 0 & 0 & 0 \\ -2 & -8 & -12 & -8 & -2 \\ -1 & -4 & -6 & -4 & -1 \\ \end{array} \right) \end{split}\]
For the C1R versions of the function the pDstMag output image value for L1 normalization consists of the absolute value of the pDstX value plus the absolute value of the pDstY value at that particular image pixel location. For the C1R versions of the function the pDstMag output image value for L2 normalization consists of the square root of the pDstX value squared plus the pDstY value squared at that particular image pixel location. For the C1R versions of the function the pDstAngle output image value consists of the arctangent (atan2) of the pDstY value and the pDstX value at that particular image pixel location.


For the C3C1R versions of the function, regardless of the selected normalization method, the L2 normalization value is first determined for each or the pDstX and pDstY values for each source channel then the largest L2 normalization value (largest gradient) is used to select which of the 3 pDstX channel values are output to the pDstX image or pDstY channel values are output to the pDstY image. For the C3C1R versions of the function the pDstMag output image value for L1 normalizaton consists of the same technique used for the C1R version for each source image channel. Then the largest L2 normalization value is again used to select which of the 3 pDstMag channel values to output to the pDstMag image. For the C3C1R versions of the function the pDstMag output image value for L2 normalizaton consists of just outputting the largest per source channel L2 normalization value to the pDstMag image. For the C3C1R versions of the function the pDstAngle output image value consists of the same technique used for the C1R version calculated for each source image channel. Then the largest L2 normalization value is again used to select which of the 3 angle values to output to the pDstAngle image.


param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param pDstX
X vector destination_image_pointer.

param nDstXStep
X vector destination_image_line_step.

param pDstY
Y vector destination_image_pointer.

param nDstYStep
Y vector destination_image_line_step.

param pDstMag
magnitude destination_image_pointer.

param nDstMagStep
magnitude destination_image_line_step.

param pDstAngle
angle destination_image_pointer.

param nDstAngleStep
angle destination_image_line_step.

param oSizeROI
Region-Of-Interest (ROI).

param eMaskSize
fixed filter mask size to use.

param eNorm
gradient distance method to use.

param eBorderType
source image border type to use use.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiGradientVectorSobelBorder_8u16s_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDstX, int nDstXStep, Npp16s *pDstY, int nDstYStep, Npp16s *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned packed RGB to optional 1 channel 16-bit signed X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorSobelBorder functions:.


NppStatus nppiGradientVectorSobelBorder_8u16s_C3C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp16s *pDstX, int nDstXStep, Npp16s *pDstY, int nDstYStep, Npp16s *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to optional 1 channel 16-bit signed X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorSobelBorder functions:.


NppStatus nppiGradientVectorSobelBorder_16s32f_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit signed packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorSobelBorder functions:.


NppStatus nppiGradientVectorSobelBorder_16s32f_C3C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 16-bit signed packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.


NppStatus nppiGradientVectorSobelBorder_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorSobelBorder functions:.


NppStatus nppiGradientVectorSobelBorder_16u32f_C3C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorSobelBorder functions:.


NppStatus nppiGradientVectorSobelBorder_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorSobelBorder functions:.


NppStatus nppiGradientVectorSobelBorder_32f_C3C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDstX, int nDstXStep, Npp32f *pDstY, int nDstYStep, Npp32f *pDstMag, int nDstMagStep, Npp32f *pDstAngle, int nDstAngleStep, NppiSize oSizeROI, NppiMaskSize eMaskSize, NppiNorm eNorm, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point packed RGB to optional 1 channel 32-bit floating point X (vertical), Y (horizontal), magnitude, and/or 32-bit floating point angle gradient vectors with user selectable fixed mask size and distance method with border control.
For common parameter descriptions, see Common parameters for nppiFilterGradientVectorSobelBorder functions:.


## Computer Vision Filtering Functions


### Computer Vision


The set of computer vision functions available in the library.


### Image Filter Distance Transform


#### FilterDistanceTransform


Performs Exact Euclidean Distance Transform function using the Parallel Banding Algorithm (PBA+) defined by Tiow-Seng Tan, et al paper named “Parallel Banding Algorithm to Compute Exact Distance Transform with the GPU” published dated August 8, 2019.


Output for these functions is an optional 16-bit signed integer voronoi diagram (pairs of signed 16 bit integer x, y distance values) and/or an optional true euclidean distance transform image generated from the internal voronoi diagram in either unsigned 16-bit truncated integer format or 32-bit floating point format. Additional optional output can include an signed 16-bit integer Voronoi diagram containing site indices and/or a signed 16-bit integer Voronoi diagram containing relative Manhattan distances to the closest sites. Minimum and maximum image ROI widths and heights are 64 and 32767.


Note that an input image that does not contain at least one site pixel is considered to be an invalid image. If you suspect that your input image may be invalid you can call an NPP function like nppiCountInRange() first to confirm that the image is valid before calling the distance transform function.


The nMinSiteValue and nMaxSiteValue parameters can be used to control which source image pixels are considered sites(traditionally 0) and non-sites (everything else).


Antialiased true distance transform, when available, is only available as double precision floating point (Npp64f) output data only and is enabled by setting the pAntialiasingDeviceBuffer pointer parameter to a non-NULL value.


The algorithm used for antialising is derived from the edtaa4 version from “Anti-aliased Euclidean distance transform” by Stefan Gustavson et. al. published in 2009 and is used under the permissions specified below.


Derived from edtaa4.c - compute the Euclidean distance transform of an image, with more accurate handling of 1 pixel wide anti-aliased edges.


This is a MEX-file for MATLAB. MATLAB is a product of The MathWorks, Inc.


Code in “edtaa4func.c” originally by Stefan Gustavson 1994, implemented from a verbal description in the PhD dissertation of Ingemar Ragnemalm, dept of EE, Linkoping University.


Modification to handle antialiased edges and this Matlab MEX wrapper by Stefan Gustavson, ([stefan.gustavson@gmail.com](mailto:stefan.gustavson%40gmail.com)) 2009-05-17


Copyright (C) 2009 Stefan Gustavson ([stefan.gustavson@gmail.com](mailto:stefan.gustavson%40gmail.com))


This software is distributed under the permissive “MIT License”:


Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:


The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.


THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


Functions


NppStatus nppiDistanceTransformPBAGetBufferSize(NppiSize oSizeROI, size_t *hpBufferSize)
Calculate scratch buffer size needed for the DistanceTransformPBA function based on destination image SizeROI width and height.

Parameters

oSizeROI – Region-Of-Interest (ROI).
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBAGetAntialiasingBufferSize(NppiSize oSizeROI, size_t *hpAntialiasingBufferSize)
Calculate scratch buffer size needed for the DistanceTransformPBA function antialiasing based on destination image SizeROI width and height.

Parameters

oSizeROI – Region-Of-Interest (ROI).
hpAntialiasingBufferSize – Optional buffer size. Important: hpAntialiasingBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSignedDistanceTransformPBAGetBufferSize(NppiSize oSizeROI, size_t *hpBufferSize)
Calculate scratch buffer size needed for the DistanceTransformPBA Antialiasing function based on destination image SizeROI width and height.

Parameters

oSizeROI – Region-Of-Interest (ROI).
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSignedDistanceTransformPBAGet64fBufferSize(NppiSize oSizeROI, size_t *hpBufferSize)
Calculate scratch buffer size needed for the SignedDistanceTransformPBA function when transform output data type is Npp64f based on destination image SizeROI width and height.

Parameters

oSizeROI – Region-Of-Interest (ROI).
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSignedDistanceTransformPBAGetAntialiasingBufferSize(NppiSize oSizeROI, size_t *hpAntialiasingBufferSize)
Calculate scratch buffer size needed for the SignedDistanceTransformPBA function antialiasing based on destination image SizeROI width and height.

Parameters

oSizeROI – Region-Of-Interest (ROI).
hpAntialiasingBufferSize – Optional buffer size. Important: hpAntialiasingBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_8u16u_C1R_Ctx(Npp8u *pSrc, int nSrcStep, Npp8u nMinSiteValue, Npp8u nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp16u *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional unsigned 16-bit truncated integer transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp16u)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_8u16u_C1R_Ctx(Npp8u *pSrc, int nSrcStep, Npp8u nMinSiteValue, Npp8u nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp16u *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional unsigned 16-bit truncated integer transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp16u)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_8s16u_C1R_Ctx(Npp8s *pSrc, int nSrcStep, Npp8s nMinSiteValue, Npp8s nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp16u *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit signed grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional unsigned 16-bit truncated integer transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp16u)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_8s16u_C1R_Ctx(Npp8s *pSrc, int nSrcStep, Npp8s nMinSiteValue, Npp8s nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp16u *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit signed grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional unsigned 16-bit truncated integer transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp16u)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_16u16u_C1R_Ctx(Npp16u *pSrc, int nSrcStep, Npp16u nMinSiteValue, Npp16u nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp16u *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional unsigned 16-bit truncated integer transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp16u)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_16u16u_C1R_Ctx(Npp16u *pSrc, int nSrcStep, Npp16u nMinSiteValue, Npp16u nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp16u *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional unsigned 16-bit truncated integer transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp16u)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_16s16u_C1R_Ctx(Npp16s *pSrc, int nSrcStep, Npp16s nMinSiteValue, Npp16s nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp16u *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit signed grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional unsigned 16-bit truncated integer transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp16u)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_16s16u_C1R_Ctx(Npp16s *pSrc, int nSrcStep, Npp16s nMinSiteValue, Npp16s nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp16u *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit signed grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional unsigned 16-bit truncated integer transform with absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp16u)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_8u32f_C1R_Ctx(Npp8u *pSrc, int nSrcStep, Npp8u nMinSiteValue, Npp8u nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp32f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 32-bit floating point transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_8u32f_C1R_Ctx(Npp8u *pSrc, int nSrcStep, Npp8u nMinSiteValue, Npp8u nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp32f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 32-bit floating point transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_8s32f_C1R_Ctx(Npp8s *pSrc, int nSrcStep, Npp8s nMinSiteValue, Npp8s nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp32f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit signed grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 32-bit floating point transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_8s32f_C1R_Ctx(Npp8s *pSrc, int nSrcStep, Npp8s nMinSiteValue, Npp8s nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp32f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit signed grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 32-bit floating point transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_16u32f_C1R_Ctx(Npp16u *pSrc, int nSrcStep, Npp16u nMinSiteValue, Npp16u nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp32f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 32-bit floating point transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_16u32f_C1R_Ctx(Npp16u *pSrc, int nSrcStep, Npp16u nMinSiteValue, Npp16u nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp32f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 32-bit floating point transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_16s32f_C1R_Ctx(Npp16s *pSrc, int nSrcStep, Npp16s nMinSiteValue, Npp16s nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp32f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit signed grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 32-bit floating point transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_16s32f_C1R_Ctx(Npp16s *pSrc, int nSrcStep, Npp16s nMinSiteValue, Npp16s nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp32f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit signed grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 32-bit floating point transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_8u64f_C1R_Ctx(Npp8u *pSrc, int nSrcStep, Npp8u nMinSiteValue, Npp8u nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 64-bit floating point transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp64f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_8u64f_C1R_Ctx(Npp8u *pSrc, int nSrcStep, Npp8u nMinSiteValue, Npp8u nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 64-bit floating point transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp64f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_8s64f_C1R_Ctx(Npp8s *pSrc, int nSrcStep, Npp8s nMinSiteValue, Npp8s nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit signed grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 64-bit floating point transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp64f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_8s64f_C1R_Ctx(Npp8s *pSrc, int nSrcStep, Npp8s nMinSiteValue, Npp8s nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit signed grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 64-bit floating point transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp64f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_16u64f_C1R_Ctx(Npp16u *pSrc, int nSrcStep, Npp16u nMinSiteValue, Npp16u nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 64-bit floating point transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp64f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_16u64f_C1R_Ctx(Npp16u *pSrc, int nSrcStep, Npp16u nMinSiteValue, Npp16u nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 64-bit floating point transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp64f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_16s64f_C1R_Ctx(Npp16s *pSrc, int nSrcStep, Npp16s nMinSiteValue, Npp16s nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit signed grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 64-bit floating point transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp64f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_16s64f_C1R_Ctx(Npp16s *pSrc, int nSrcStep, Npp16s nMinSiteValue, Npp16s nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit signed grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 64-bit floating point transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – signed source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp64f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_32f64f_C1R_Ctx(Npp32f *pSrc, int nSrcStep, Npp32f nMinSiteValue, Npp32f nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 64-bit floating point transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp64f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_32f64f_C1R_Ctx(Npp32f *pSrc, int nSrcStep, Npp32f nMinSiteValue, Npp32f nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 64-bit floating point transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp64f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformPBA_64f_C1R_Ctx(Npp64f *pSrc, int nSrcStep, Npp64f nMinSiteValue, Npp64f nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 64-bit floating point grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 64-bit floating point transform with optional relative Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp64f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiDistanceTransformAbsPBA_64f_C1R_Ctx(Npp64f *pSrc, int nSrcStep, Npp64f nMinSiteValue, Npp64f nMaxSiteValue, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 64-bit floating point grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram output and/or optional 64-bit floating point transform with optional absolute Manhattan distances.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nMinSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
nMaxSiteValue – source image pixel values >= nMinSiteValue and <= nMaxSiteValue are considered sites (traditionally 0s).
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp64f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiDistanceTransformPBAGetBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSignedDistanceTransformPBA_32f_C1R_Ctx(Npp32f *pSrc, int nSrcStep, Npp32f nCutoffValue, Npp32f nSubPixelXShift, Npp32f nSubPixelYShift, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp32f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram and 32-bit floating point transform with optional sub-pixel shifts.
For this particular version of the function acceptable input pixel intensities are less than or equal to 0.0f for those fully outside of connected pixel regions, intensities with fractional parts between 0.0f and 1.0f representing the percentage of connected pixel region sub-pixel coverage within a particular pixel (region contour), and intensities greater than or equal to 1.0f for pixels that are fully contained within closed connected pixel regions. This function executes in two passes, the first pass prioritizes pixels outside of closed regions, the second pass prioritizes pixels within closed regions. The two passes are then merged on output. The function assumes that fully covered pixels have centers located at sub-pixel locations of .5,.5 . In general, object exterior distances are output as negative numbers and object interior distances are output as positive numbers.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nCutoffValue – source image pixel values < nCutoffValue will be considered fully outside of pixel regions (and set to -1).
nSubPixelXShift – final transform distances will be shifted in the X direction by this sub-pixel fraction.
nSubPixelYShift – final transform distances will be shifted in the Y direction by this sub-pixel fraction.
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiSignedDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSignedDistanceTransformAbsPBA_32f_C1R_Ctx(Npp32f *pSrc, int nSrcStep, Npp32f nCutoffValue, Npp32f nSubPixelXShift, Npp32f nSubPixelYShift, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp32f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram and 32-bit floating point transform with optional sub-pixel shifts.
For this particular version of the function acceptable input pixel intensities are less than or equal to 0.0f for those fully outside of connected pixel regions, intensities with fractional parts between 0.0f and 1.0f representing the percentage of connected pixel region sub-pixel coverage within a particular pixel (region contour), and intensities greater than or equal to 1.0f for pixels that are fully contained within closed connected pixel regions. This function executes in two passes, the first pass prioritizes pixels outside of closed regions, the second pass prioritizes pixels within closed regions. The two passes are then merged on output. The function assumes that fully covered pixels have centers located at sub-pixel locations of .5,.5 . In general, object exterior distances are output as negative numbers progressing to positive and object interior distances are output as positive numbers progressing to negative.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nCutoffValue – source image pixel values < nCutoffValue will be considered fully outside of pixel regions (and set to -1).
nSubPixelXShift – final transform distances will be shifted in the X direction by this sub-pixel fraction.
nSubPixelYShift – final transform distances will be shifted in the Y direction by this sub-pixel fraction.
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiSignedDistanceTransformPBAGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSignedDistanceTransformPBA_32f64f_C1R_Ctx(Npp32f *pSrc, int nSrcStep, Npp32f nCutoffValue, Npp64f nSubPixelXShift, Npp64f nSubPixelYShift, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram and 64-bit floating point transform with optional sub-pixel shifts.
For this particular version of the function acceptable input pixel intensities are less than or equal to 0.0f for those fully outside of connected pixel regions, intensities with fractional parts between 0.0f and 1.0f representing the percentage of connected pixel region sub-pixel coverage within a particular pixel (region contour), and intensities greater than or equal to 1.0f for pixels that are fully contained within closed connected pixel regions. This function executes in two passes, the first pass prioritizes pixels outside of closed regions, the second pass prioritizes pixels within closed regions. The two passes are then merged on output. The function assumes that fully covered pixels have centers located at sub-pixel locations of .5,.5 . In general, object exterior distances are output as negative numbers progressing to positive and object interior distances are output as positive numbers progressing to negative.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nCutoffValue – source image pixel values < nCutoffValue will be considered fully outside of pixel regions (and set to -1).
nSubPixelXShift – final transform distances will be shifted in the X direction by this sub-pixel fraction.
nSubPixelYShift – final transform distances will be shifted in the Y direction by this sub-pixel fraction.
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiSignedDistanceTransformPBAGet64fBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiSignedDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSignedDistanceTransformAbsPBA_32f64f_C1R_Ctx(Npp32f *pSrc, int nSrcStep, Npp32f nCutoffValue, Npp64f nSubPixelXShift, Npp64f nSubPixelYShift, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram and 64-bit floating point transform with optional sub-pixel shifts.
For this particular version of the function acceptable input pixel intensities are less than or equal to 0.0f for those fully outside of connected pixel regions, intensities with fractional parts between 0.0f and 1.0f representing the percentage of connected pixel region sub-pixel coverage within a particular pixel (region contour), and intensities greater than or equal to 1.0f for pixels that are fully contained within closed connected pixel regions. This function executes in two passes, the first pass prioritizes pixels outside of closed regions, the second pass prioritizes pixels within closed regions. The two passes are then merged on output. The function assumes that fully covered pixels have centers located at sub-pixel locations of .5,.5 . In general, object exterior distances are output as negative numbers progressing to positive and object interior distances are output as positive numbers progressing to negative.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nCutoffValue – source image pixel values < nCutoffValue will be considered fully outside of pixel regions (and set to -1).
nSubPixelXShift – final transform distances will be shifted in the X direction by this sub-pixel fraction.
nSubPixelYShift – final transform distances will be shifted in the Y direction by this sub-pixel fraction.
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiSignedDistanceTransformPBAGet64fBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiSignedDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSignedDistanceTransformPBA_64f_C1R_Ctx(Npp64f *pSrc, int nSrcStep, Npp64f nCutoffValue, Npp64f nSubPixelXShift, Npp64f nSubPixelYShift, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16s *pDstVoronoiRelativeManhattanDistances, int nDstVoronoiRelativeManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 64-bit floating point grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram and 64-bit floating point transform with optional sub-pixel shifts.
For this particular version of the function acceptable input pixel intensities are less than or equal to 0.0f for those fully outside of connected pixel regions, intensities with fractional parts between 0.0f and 1.0f representing the percentage of connected pixel region sub-pixel coverage within a particular pixel (region contour), and intensities greater than or equal to 1.0f for pixels that are fully contained within closed connected pixel regions. This function executes in two passes, the first pass prioritizes pixels outside of closed regions, the second pass prioritizes pixels within closed regions. The two passes are then merged on output. The function assumes that fully covered pixels have centers located at sub-pixel locations of .5,.5 . In general, object exterior distances are output as negative numbers progressing to positive and object interior distances are output as positive numbers progressing to negative.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nCutoffValue – source image pixel values < nCutoffValue will be considered fully outside of pixel regions (and set to -1).
nSubPixelXShift – final transform distances will be shifted in the X direction by this sub-pixel fraction.
nSubPixelYShift – final transform distances will be shifted in the Y direction by this sub-pixel fraction.
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiRelativeManhattanDistances – device memory voronoi relative Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiRelativeManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiSignedDistanceTransformPBAGet64fBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSignedDistanceTransformAbsPBA_64f_C1R_Ctx(Npp64f *pSrc, int nSrcStep, Npp64f nCutoffValue, Npp64f nSubPixelXShift, Npp64f nSubPixelYShift, Npp16s *pDstVoronoi, int nDstVoronoiStep, Npp16s *pDstVoronoiIndices, int nDstVoronoiIndicesStep, Npp16u *pDstVoronoiAbsoluteManhattanDistances, int nDstVoronoiAbsoluteManhattanDistancesStep, Npp64f *pDstTransform, int nDstTransformStep, NppiSize oSizeROI, Npp8u *pDeviceBuffer, Npp8u *pAntialiasingDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 64-bit floating point grayscale to optional 1 channel 16-bit signed integer euclidean distance voronoi diagram and 64-bit floating point transform with optional sub-pixel shifts.
For this particular version of the function acceptable input pixel intensities are less than or equal to 0.0f for those fully outside of connected pixel regions, intensities with fractional parts between 0.0f and 1.0f representing the percentage of connected pixel region sub-pixel coverage within a particular pixel (region contour), and intensities greater than or equal to 1.0f for pixels that are fully contained within closed connected pixel regions. This function executes in two passes, the first pass prioritizes pixels outside of closed regions, the second pass prioritizes pixels within closed regions. The two passes are then merged on output. The function assumes that fully covered pixels have centers located at sub-pixel locations of .5,.5 . In general, object exterior distances are output as negative numbers progressing to positive and object interior distances are output as positive numbers progressing to negative.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
nCutoffValue – source image pixel values < nCutoffValue will be considered fully outside of pixel regions (and set to -1).
nSubPixelXShift – final transform distances will be shifted in the X direction by this sub-pixel fraction.
nSubPixelYShift – final transform distances will be shifted in the Y direction by this sub-pixel fraction.
pDstVoronoi – device memory voronoi diagram destination_image_pointer or NULL for no voronoi output.
nDstVoronoiStep – voronoi destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiIndices – device memory voronoi diagram destination_image_pointer or NULL for no voronoi indices output.
nDstVoronoiIndicesStep – voronoi indices destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstVoronoiAbsoluteManhattanDistances – device memory voronoi absolute Manhattan distances destination_image_pointer or NULL for no voronoi Manhattan output.
nDstVoronoiAbsoluteManhattanDistancesStep – voronoi Manhattan destination_image_line_step (must be at least oSizeROI.width * 2 * sizeof(Npp16s)).
pDstTransform – device memory true euclidean distance transform destination_image_pointer or NULL for no transform output.
nDstTransformStep – true euclidean distance transform destination_image_line_step (must be at least oSizeROI.width * sizeof(Npp32f)).
oSizeROI – Region-Of-Interest (ROI).
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiSignedDistanceTransformPBAGet64fBufferSize() above)
pAntialiasingDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpAntialiasingBufferSize (see nppiDistanceTransformPBAGetAntialiasingBufferSize() above) or NULL if not Antialiasing
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Image Filter Canny Border


#### FilterCannyBorder


Performs Canny edge detection on a single channel 8-bit grayscale image and outputs a single channel 8-bit image consisting of 0x00 and 0xFF values with 0xFF representing edge pixels.


The algorithm consists of three phases. The first phase generates two output images consisting of a single channel 16-bit signed image containing magnitude values and a single channel 32-bit floating point image containing the angular direction of those magnitude values. This phase is accomplished by calling the appropriate GradientVectorBorder filter function based on the filter type, filter mask size, and norm type requested. The next phase uses those magnitude and direction images to suppress non-maximum magnitude values which are lower than the values of either of its two nearest neighbors in the same direction as the test magnitude pixel in the 3x3 surrounding magnitude pixel neighborhood. This phase outputs a new magnitude image with non-maximum pixel values suppressed. Finally, in the third phase, the new magnitude image is passed through a hysteresis threshold filter that filters out any magnitude values that are not connected to another edge magnitude value. In this phase, any magnitude value above the high threshold value is automatically accepted, any magnitude value below the low threshold value is automatically rejected. For magnitude values that lie between the low and high threshold, values are only accepted if one of their two neighbors in the same direction in the 3x3 neighborhood around them lies above the low threshold value. In other words, if they are connected to an active edge. J. Canny recommends that the ratio of high to low threshold limit be in the range two or three to one, based on predicted signal-to-noise ratios. The final output of the third phase consists of a single channel 8-bit unsigned image of 0x00 and 0xFF values based on whether they are accepted or rejected during threshold testing.


Currently only the NPP_BORDER_REPLICATE border type operation is supported. Borderless output can be accomplished by using a larger source image than the destination and adjusting oSrcSize and oSrcOffset parameters accordingly.


Functions


NppStatus nppiFilterCannyBorderGetBufferSize(NppiSize oSizeROI, int *hpBufferSize)
Calculate scratch buffer size needed for the FilterCannyBorder function based on destination image SizeROI width and height.

Parameters

oSizeROI – Region-Of-Interest (ROI).
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFilterCannyBorder_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiDifferentialKernel eFilterType, NppiMaskSize eMaskSize, Npp16s nLowThreshold, Npp16s nHighThreshold, NppiNorm eNorm, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned grayscale to 1 channel 8-bit unsigned black (0x00) and white (0xFF) image with border control.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
oSrcSize – Source image width and height in pixels relative to pSrc.
oSrcOffset – The pixel offset that pSrc points to relative to the origin of the source image.
pDst – output edge destination_image_pointer.
nDstStep – output edge destination_image_line_step.
oSizeROI – Region-Of-Interest (ROI).
eFilterType – selects between Sobel or Scharr filter type.
eMaskSize – fixed filter mask size to use.
nLowThreshold – low hysteresis threshold value.
nHighThreshold – high hysteresis threshold value.
eNorm – gradient distance method to use.
eBorderType – source image border type to use use.
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiFilterCannyBorderGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFilterCannyBorder_8u_C3C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiDifferentialKernel eFilterType, NppiMaskSize eMaskSize, Npp16s nLowThreshold, Npp16s nHighThreshold, NppiNorm eNorm, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned color to 1 channel 8-bit unsigned black (0x00) and white (0xFF) image with border control.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
oSrcSize – Source image width and height in pixels relative to pSrc.
oSrcOffset – The pixel offset that pSrc points to relative to the origin of the source image.
pDst – output edge destination_image_pointer.
nDstStep – output edge destination_image_line_step.
oSizeROI – Region-Of-Interest (ROI).
eFilterType – selects between Sobel or Scharr filter type.
eMaskSize – fixed filter mask size to use.
nLowThreshold – low hysteresis threshold value.
nHighThreshold – high hysteresis threshold value.
eNorm – gradient distance method to use.
eBorderType – source image border type to use use.
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiFilterCannyBorderGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Image Filter Harris Corners Border


#### FilterHarrisCornersBorder


Performs Harris Corner detection on a single channel 8-bit grayscale image and outputs a single channel 32-bit floating point image consisting the corner response at each pixel of the image.


The algorithm consists of two phases. The first phase generates the floating point product of XX, YY, and XY gradients at each pixel in the image. The type of gradient used is controlled by the eFilterType and eMaskSize parameters. The second phase averages those products over a window of either 3x3 or 5x5 pixels around the center pixel then generates the Harris corner response at that pixel which is output in the destination image. The Harris response value is determined as H = ((XX * YY - XY * XY) - (nK * ((XX + YY) * (XX + YY)))) * nScale.


Currently only the NPP_BORDER_REPLICATE border type operation is supported. Borderless output can be accomplished by using a larger source image than the destination and adjusting oSrcSize and oSrcOffset parameters accordingly.


Functions


NppStatus nppiFilterHarrisCornersBorderGetBufferSize(NppiSize oSizeROI, int *hpBufferSize)
Calculate scratch buffer size needed for the FilterHarrisCornersBorder function based on destination image SizeROI width and height.

Parameters

oSizeROI – Region-Of-Interest (ROI).
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFilterHarrisCornersBorder_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppiDifferentialKernel eFilterType, NppiMaskSize eMaskSize, NppiMaskSize eAvgWindowSize, Npp32f nK, Npp32f nScale, NppiBorderType eBorderType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned grayscale to 1 channel 32-bit floating point Harris corners response image with border control.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
oSrcSize – Source image width and height in pixels relative to pSrc.
oSrcOffset – The pixel offset that pSrc points to relative to the origin of the source image.
pDst – output edge destination_image_pointer.
nDstStep – output edge destination_image_line_step.
oSizeROI – Region-Of-Interest (ROI).
eFilterType – selects between Sobel or Scharr filter type.
eMaskSize – fixed filter mask size to use (3x3 or 5x5 for Sobel).
eAvgWindowSize – fixed window mask size to use (3x3 or 5x5).
nK – Harris Corners constant (commonly used value is 0.04F).
nScale – output is scaled by this scale factor.
eBorderType – source image border type to use use.
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiFilterHarrisCornersBorderGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Image Filter Hough Line


#### FilterHoughLine


Extracts Hough lines from a single channel 8-bit binarized (0, 255) source feature (canny edges, etc.) image.


Outputs a list of lines in point polar format representing the length (rho) and angle (theta) of each line from the origin of the normal to the line using the formula rho = x cos(theta) + y sin(theta). The level of discretization, nDelta, is specified as an input parameter. The performance and effectiveness of this function highly depends on this parameter with higher performance for larger numbers and more detailed results for lower numbers. Also, lines are not guaranteed to be added to the pDeviceLines list in the same order from one call to the next. However, all of the same lines will still be generated as long as nMaxLineCount is set large enough so that they all can fit in the list. To convert lines in point polar format back to cartesian lines use the following formula:


```
Npp32f nHough = ((sqrt(2.0F) * static_cast<Npp32f>(oSizeROI.height > oSizeROI.width ? oSizeROI.height
                                                                                    : oSizeROI.width)) / 2.0F);
int nAccumulatorsHeight = nDelta.rho > 1.0F ? static_cast<int>(ceil(nHough * 2.0F))
                                            : static_cast<int>(ceil((nHough * 2.0F) / nDelta.rho));
int nCenterX = oSizeROI.width >> 1;
int nCenterY = oSizeROI.height >> 1;
Npp32f nThetaRad = static_cast<Npp32f>(deviceline.theta) * 0.0174532925199433F;
Npp32f nSinTheta = sin(nThetaRad);
Npp32f nCosTheta = cos(nThetaRad);
int nX1, nY1, nX2, nY2;

if (deviceline.theta >= 45 && deviceline.theta <= 135) // degrees
{
    // y = (rho - x cos(theta)) / sin(theta)
    nX1 = minimum cartesian X boundary value;
    nY1 = static_cast<int>((static_cast<Npp32f>(deviceline.rho - (nAccumulatorsHeight >> 1)) -
                           ((nX1 - nCenterX) * nCosTheta)) / nSinTheta + nCenterY);
    nX2 = maximum cartesian X boundary value;
    nY2 = static_cast<int>((static_cast<Npp32f>(deviceline.rho - (nAccumulatorsHeight >> 1)) -
                           ((nX2 - nCenterX) * nCosTheta)) / nSinTheta + nCenterY);
}
else
{
    // x = (rho - y sin(theta)) / cos(theta)
    nY1 = minimum cartesian Y boundary value;
    nX1 = static_cast<int>((static_cast<Npp32f>(deviceline.rho - (nAccumulatorsHeight >> 1)) -
                           ((nY1 - nCenterY) * nSinTheta)) / nCosTheta + nCenterX);
    nY2 = maximum cartesian Y boundary value;
    nX2 = static_cast<int>((static_cast<Npp32f>(deviceline.rho - (nAccumulatorsHeight >> 1)) -
                           ((nY2 - nCenterY) * nSinTheta)) / nCosTheta + nCenterX);
}
```


Functions


NppStatus nppiFilterHoughLineGetBufferSize(NppiSize oSizeROI, NppPointPolar nDelta, int nMaxLineCount, int *hpBufferSize)
Calculate scratch buffer size needed for the FilterHoughLine or FilterHoughLineRegion functions based on destination image SizeROI width and height and nDelta parameters.

Parameters

oSizeROI – Region-Of-Interest (ROI).
nDelta – rho radial increment and theta angular increment that will be used in the FilterHoughLine or FilterHoughLineRegion function call.
nMaxLineCount – The maximum number of lines expected from the FilterHoughLine or FilterHoughLineRegion function call.
hpBufferSize – Required buffer size in bytes. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFilterHoughLine_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, NppPointPolar nDelta, int nThreshold, NppPointPolar *pDeviceLines, int nMaxLineCount, int *pDeviceLineCount, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned binarized (0, 255) source feature (canny edges, etc.) source image to list of lines in point polar format representing the length (rho) and angle (theta) of each line from the origin of the normal to the line using the formula rho = x cos(theta) + y sin(theta).
The level of discretization, nDelta, is specified as an input parameter. The performance and effectiveness of this function highly depends on this parameter with higher performance for larger numbers and more detailed results for lower numbers. nDelta must have the same values as those used in the nppiFilterHoughLineGetBufferSize() function call.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nDelta – Discretization steps, range 0.0F < radial increment nDelta.rho < 3.0F, 1.0F recommended, range 0.25F < angular increment nDelta.theta < 3.0F, 1.0F recommended.
nThreshold – Minimum number of points to accept a line.
pDeviceLines – Device pointer to (nMaxLineCount * sizeof(NppPointPolar) line objects.
nMaxLineCount – The maximum number of lines to output.
pDeviceLineCount – The number of lines detected by this function up to nMaxLineCount.
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiFilterHoughLineGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFilterHoughLineRegion_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSizeROI, NppPointPolar nDelta, int nThreshold, NppPointPolar *pDeviceLines, NppPointPolar oDstROI[2], int nMaxLineCount, int *pDeviceLineCount, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned binarized (0, 255) source feature (canny edges, etc.) source image to list of lines in point polar format representing the length (rho) and angle (theta) of each line from the origin of the normal to the line using the formula rho = x cos(theta) + y sin(theta).
The level of discretization, nDelta, is specified as an input parameter. The performance and effectiveness of this function highly depends on this parameter with higher performance for larger numbers and more detailed results for lower numbers. nDelta must have the same values as those used in the nppiFilterHoughLineGetBufferSize() function call. The oDstROI region limits are used to limit accepted lines to those that fall within those limits.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nDelta – Discretization steps, range 0.0F < radial increment nDelta.rho < 3.0F, 1.0F recommended, range 0.25F < angular increment nDelta.theta < 3.0F, 1.0F recommended.
nThreshold – Minimum number of points to accept a line.
pDeviceLines – Device pointer to (nMaxLineCount * sizeof(NppPointPolar) line objects.
oDstROI – Region limits with oDstROI[0].rho <= accepted rho <= oDstROI[1].rho and oDstROI[0].theta <= accepted theta <= oDstROI[1].theta.
nMaxLineCount – The maximum number of lines to output.
pDeviceLineCount – The number of lines detected by this function up to nMaxLineCount.
pDeviceBuffer – pointer to scratch DEVICE memory buffer of size hpBufferSize (see nppiFilterHoughLineGetBufferSize() above)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Image Filter Histogram Of Oriented Gradients Border


#### HistogramOfOrientedGradientsBorder


Performs Histogram Of Oriented Gradients operation on source image generating separate windows of Histogram Descriptors for each requested location.


This function implements the simplest form of functionality described by N. Dalal and B. Triggs. Histograms of Oriented Gradients for Human Detection. INRIA, 2005. It supports overlapped contrast normalized block histogram output with L2 normalization only, no threshold clipping, and no pre or post gaussian smoothing of input images or histogram output values. It supports both single channel grayscale source images and three channel color images. For color images, the color channel with the highest magnitude value is used as that pixel’s magnitude. Output is row order only. Descriptors are output consecutively with no separation padding if multiple descriptor output is requested (one desriptor per source image location). For example, common HOG parameters are 9 histogram bins per 8 by 8 pixel cell, 2 by 2 cells per block, with a descriptor window size of 64 horizontal by 128 vertical pixels yielding 7 by 15 overlapping blocks (1 cell overlap in both horizontal and vertical directions). This results in 9 bins * 4 cells * 7 horizontal overlapping blocks * 15 vertical overlapping blocks or 3780 32-bit floating point output values (bins) per descriptor window.


The number of horizontal overlapping block histogram bins per descriptor window width is determined by (((oHOGConfig.detectionWindowSize.width / oHOGConfig.histogramBlockSize) * 2) - 1) * oHOGConfig.nHistogramBins. The number of vertical overlapping block histograms per descriptor window height is determined by (((oHOGConfig.detectionWindowSize.height / oHOGConfig.histogramBlockSize) * 2) - 1) The offset of each descriptor window in the descriptors output buffer is therefore horizontal histogram bins per descriptor window width * vertical histograms per descriptor window height 32-bit floating point values relative to the previous descriptor window output.


The algorithm uses a 1D centered derivative mask of [-1, 0, +1] when generating input magnitude and angle gradients. Magnitudes are added to the two nearest histogram bins of oriented gradients between 0 and 180 degrees using a weighted linear interpolation of each magnitude value across the 2 nearest angular bin orientations. 2D overlapping blocks of histogram bins consisting of the bins from 2D arrangements of cells are then contrast normalized using L2 normalization and output to the corresponding histogram descriptor window for that particular window location in the window locations list.


Some restrictions include:




```
#define NPP_HOG_MAX_CELL_SIZE                          (16)
#define NPP_HOG_MAX_BLOCK_SIZE                         (64)
#define NPP_HOG_MAX_BINS_PER_CELL                      (16)
#define NPP_HOG_MAX_CELLS_PER_DESCRIPTOR              (256)
#define NPP_HOG_MAX_OVERLAPPING_BLOCKS_PER_DESCRIPTOR (256)
#define NPP_HOG_MAX_DESCRIPTOR_LOCATIONS_PER_CALL     (128)
```


Currently only the NPP_BORDER_REPLICATE border type operation is supported.


##### Common parameters for nppiFilterHistogramOfGradientsBorder functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param oSrcSize
Source image width and height in pixels relative to pSrc.

param oSrcOffset
The pixel offset that pSrc points to relative to the origin of the source image.

param hpLocations
Host pointer to array of NppiPoint source pixel starting locations of requested descriptor windows. Important: hpLocations is a host pointer.

param nLocations
Number of NppiPoint in pLocations array.

param pDstWindowDescriptorBuffer
Output device memory buffer pointer of size hpDescriptorsSize bytes to first of nLoc descriptor windows (see nppiHistogramOfGradientsBorderGetDescriptorsSize() above).

param oSizeROI
Region-Of-Interest (ROI) of source image.

param oHOGConfig
Requested HOG configuration parameters structure.

param pScratchBuffer
Device memory buffer pointer of size hpBufferSize bytes to scratch memory buffer (see nppiHistogramOfGradientsBorderGetBufferSize() above).

param eBorderType
The border type operation to be applied at source image border boundaries.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiHistogramOfGradientsBorderGetBufferSize(const NppiHOGConfig oHOGConfig, const NppiPoint *hpLocations, int nLocations, NppiSize oSizeROI, int *hpBufferSize)
Validates requested HOG configuration and calculates scratch buffer size needed for the HistogramOfGradientsBorder function based on requested HOG configuration, source image ROI, and number and locations of descriptor window locations.

Parameters

oHOGConfig – Requested HOG configuration parameters structure.
hpLocations – Host pointer to array of NppiPoint source pixel starting locations of requested descriptor windows. Important: hpLocations is a host pointer.
nLocations – Number of NppiPoint in pLocations array.
oSizeROI – Region-Of-Interest (ROI) of source image.
hpBufferSize – Required buffer size in bytes. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiHistogramOfGradientsBorderGetDescriptorsSize(const NppiHOGConfig oHOGConfig, int nLocations, int *hpDescriptorsSize)
Validates requested HOG configuration and calculates output window descriptors buffer size needed for the HistogramOfGradientsBorder function based on requested HOG configuration, and number of descriptor window locations, one descriptor window is output for each location.
Descriptor windows are located sequentially and contiguously in the descriptors buffer.
The number of horizontal overlapping block histogram bins per descriptor window width is determined by (((oHOGConfig.detectionWindowSize.width / oHOGConfig.histogramBlockSize) * 2) - 1) * oHOGConfig.nHistogramBins. The number of vertical overlapping block histograms per descriptor window height is determined by (((oHOGConfig.detectionWindowSize.height / oHOGConfig.histogramBlockSize) * 2) - 1) The offset of each descriptor window in the descriptors output buffer is therefore horizontal histogram bins per descriptor window width * vertical histograms per descriptor window height floating point values relative to the previous descriptor window output.

Parameters

oHOGConfig – Requested HOG configuration parameters structure.
nLocations – Number of NppiPoint in pLocations array.
hpDescriptorsSize – Required buffer size in bytes of output windows descriptors for nLocations descriptor windows. Important: hpDescriptorsSize is a host pointer.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiHistogramOfGradientsBorder_8u32f_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, const NppiPoint *hpLocations, int nLocations, Npp32f *pDstWindowDescriptorBuffer, NppiSize oSizeROI, const NppiHOGConfig oHOGConfig, Npp8u *pScratchBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned grayscale per source image descriptor window location with source image border control to per descriptor window destination floating point histogram of gradients.
Requires first calling nppiHistogramOfGradientsBorderGetBufferSize function call to get required scratch (host) working buffer size and nppiHistogramOfGradientsBorderGetDescriptorsSize() function call to get total size for nLocations of output histogram block descriptor windows.
For common parameter descriptions, see Common parameters for nppiFilterHistogramOfGradientsBorder functions:.


NppStatus nppiHistogramOfGradientsBorder_8u32f_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, const NppiPoint *hpLocations, int nLocations, Npp32f *pDstWindowDescriptorBuffer, NppiSize oSizeROI, const NppiHOGConfig oHOGConfig, Npp8u *pScratchBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned color per source image descriptor window location with source image border control to per descriptor window destination floating point histogram of gradients.
Requires first calling nppiHistogramOfGradientsBorderGetBufferSize function call to get required scratch (host) working buffer size and nppiHistogramOfGradientsBorderGetDescriptorsSize() function call to get total size for nLocations of output histogram block descriptor windows.
For common parameter descriptions, see Common parameters for nppiFilterHistogramOfGradientsBorder functions:.


NppStatus nppiHistogramOfGradientsBorder_16u32f_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, const NppiPoint *hpLocations, int nLocations, Npp32f *pDstWindowDescriptorBuffer, NppiSize oSizeROI, const NppiHOGConfig oHOGConfig, Npp8u *pScratchBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned grayscale per source image descriptor window location with source image border control to per descriptor window destination floating point histogram of gradients.
Requires first calling nppiHistogramOfGradientsBorderGetBufferSize function call to get required scratch (host) working buffer size and nppiHistogramOfGradientsBorderGetDescriptorsSize() function call to get total size for nLocations of output histogram block descriptor windows.
For common parameter descriptions, see Common parameters for nppiFilterHistogramOfGradientsBorder functions:.


NppStatus nppiHistogramOfGradientsBorder_16u32f_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, const NppiPoint *hpLocations, int nLocations, Npp32f *pDstWindowDescriptorBuffer, NppiSize oSizeROI, const NppiHOGConfig oHOGConfig, Npp8u *pScratchBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned color per source image descriptor window location with source image border control to per descriptor window destination floating point histogram of gradients.
Requires first calling nppiHistogramOfGradientsBorderGetBufferSize function call to get required scratch (host) working buffer size and nppiHistogramOfGradientsBorderGetDescriptorsSize() function call to get total size for nLocations of output histogram block descriptor windows.
For common parameter descriptions, see Common parameters for nppiFilterHistogramOfGradientsBorder functions:.


NppStatus nppiHistogramOfGradientsBorder_16s32f_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, const NppiPoint *hpLocations, int nLocations, Npp32f *pDstWindowDescriptorBuffer, NppiSize oSizeROI, const NppiHOGConfig oHOGConfig, Npp8u *pScratchBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 16-bit signed grayscale per source image descriptor window location with source image border control to per descriptor window destination floating point histogram of gradients.
Requires first calling nppiHistogramOfGradientsBorderGetBufferSize function call to get required scratch (host) working buffer size and nppiHistogramOfGradientsBorderGetDescriptorsSize() function call to get total size for nLocations of output histogram block descriptor windows.
For common parameter descriptions, see Common parameters for nppiFilterHistogramOfGradientsBorder functions:.


NppStatus nppiHistogramOfGradientsBorder_16s32f_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, const NppiPoint *hpLocations, int nLocations, Npp32f *pDstWindowDescriptorBuffer, NppiSize oSizeROI, const NppiHOGConfig oHOGConfig, Npp8u *pScratchBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 16-bit signed color per source image descriptor window location with source image border control to per descriptor window destination floating point histogram of gradients.
Requires first calling nppiHistogramOfGradientsBorderGetBufferSize function call to get required scratch (host) working buffer size and nppiHistogramOfGradientsBorderGetDescriptorsSize() function call to get total size for nLocations of output histogram block descriptor windows.
For common parameter descriptions, see Common parameters for nppiFilterHistogramOfGradientsBorder functions:.


NppStatus nppiHistogramOfGradientsBorder_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, const NppiPoint *hpLocations, int nLocations, Npp32f *pDstWindowDescriptorBuffer, NppiSize oSizeROI, const NppiHOGConfig oHOGConfig, Npp8u *pScratchBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point grayscale per source image descriptor window location with source image border control to per descriptor window destination floating point histogram of gradients.
Requires first calling nppiHistogramOfGradientsBorderGetBufferSize function call to get required scratch (host) working buffer size and nppiHistogramOfGradientsBorderGetDescriptorsSize() function call to get total size for nLocations of output histogram block descriptor windows.
For common parameter descriptions, see Common parameters for nppiFilterHistogramOfGradientsBorder functions:.


NppStatus nppiHistogramOfGradientsBorder_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, NppiSize oSrcSize, NppiPoint oSrcOffset, const NppiPoint *hpLocations, int nLocations, Npp32f *pDstWindowDescriptorBuffer, NppiSize oSizeROI, const NppiHOGConfig oHOGConfig, Npp8u *pScratchBuffer, NppiBorderType eBorderType, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point color per source image descriptor window location with source image border control to per descriptor window destination floating point histogram of gradients.
Requires first calling nppiHistogramOfGradientsBorderGetBufferSize function call to get required scratch (host) working buffer size and nppiHistogramOfGradientsBorderGetDescriptorsSize() function call to get total size for nLocations of output histogram block descriptor windows.
For common parameter descriptions, see Common parameters for nppiFilterHistogramOfGradientsBorder functions:.


## Image Filter Flood Fill


### FloodFill


Flood fill a connected region of an image with a specified new value.


FloodFillGetBufferSize


Before calling any of the FloodFill functions the application first needs to call the FloodFillGetBufferSize function to determine the amount of device memory to allocate as a working buffer.


The application allocated device memory is then passed as the pBuffer parameter to the corresponding FloodFill function.


NppStatus nppiFloodFillGetBufferSize(NppiSize oSizeROI, int *hpBufferSize)
Calculate scratch buffer size needed for the FloodFill function based on destination image oSizeROI width and height.

Parameters

oSizeROI – Region-Of-Interest (ROI).
hpBufferSize – Required buffer size in bytes.


### Flood Fill


#### FloodFill


In place flood fill of a region of pixels connected to the pixel at the seed pixel location in an image with a new pixel value.


Before calling any of the FloodFill functions the application first needs to call the FloodFillGetBufferSize function to determine the amount of device memory to allocate as a working buffer. The allocated device memory is then passed as the pBuffer parameter to the corresponding FloodFill function.


Optionally the function can return connected region information for the filled region in the pConnectedRegion [NppiConnectedRegion](nppdefs.html#structnppiconnectedregion) structure in host memory. The oBoundingBox x and y will be set to the left and top coordinates and width and height will be set to the right bottom coordinates of the bounding box relative to pSrcDst. Set pConnectedRegion to NULL if not required. Requesting pConnectedRegion information may slightly degrade performance.


Functions


NppStatus nppiFloodFill_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, const Npp8u nNewValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nNewValue – Image pixel value to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFill_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, const Npp8u aNewValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aNewValues – Image pixel values to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFill_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, const Npp16u nNewValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nNewValue – Image pixel value to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFill_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, const Npp16u aNewValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aNewValues – Image pixel values to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFill_32u_C1IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, const Npp32u nNewValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nNewValue – Image pixel value to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFill_32u_C3IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, const Npp32u aNewValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 32-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aNewValues – Image pixel values to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Flood Fill Boundary


#### FloodFillBoundary


In place flood fill of a region of pixels connected to the pixel at the seed pixel location in an image with a new pixel value. Also fill boundary of filled region with a specified color.


Before calling any of the FloodFill functions the application first needs to call the FloodFillGetBufferSize function to determine the amount of device memory to allocate as a working buffer. The allocated device memory is then passed as the pBuffer parameter to the corresponding FloodFill function.


Optionally the function can return connected region information for the filled region in the pConnectedRegion [NppiConnectedRegion](nppdefs.html#structnppiconnectedregion) structure in host memory. The oBoundingBox x and y will be set to the left and top coordinates and width and height will be set to the right bottom coordinates of the bounding box relative to pSrcDst. Set pConnectedRegion to NULL if not required. Requesting pConnectedRegion information may slightly degrade performance.


Functions


NppStatus nppiFloodFillBoundary_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, const Npp8u nNewValue, const Npp8u nBoundaryValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nNewValue – Image pixel value to be used to replace matching pixels.
nBoundaryValue – Image pixel value to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillBoundary_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, const Npp8u aNewValues[3], const Npp8u aBoundaryValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aNewValues – Image pixel values to be used to replace matching pixels.
aBoundaryValues – Image pixel values to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillBoundary_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, const Npp16u nNewValue, const Npp16u nBoundaryValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nNewValue – Image pixel value to be used to replace matching pixels.
nBoundaryValue – Image pixel value to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillBoundary_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, const Npp16u aNewValues[3], const Npp16u aBoundaryValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aNewValues – Image pixel values to be used to replace matching pixels.
aBoundaryValues – Image pixel values to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillBoundary_32u_C1IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, const Npp32u nNewValue, const Npp32u nBoundaryValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nNewValue – Image pixel value to be used to replace matching pixels.
nBoundaryValue – Image pixel value to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillBoundary_32u_C3IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, const Npp32u aNewValues[3], const Npp32u aBoundaryValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 32-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aNewValues – Image pixel values to be used to replace matching pixels.
aBoundaryValues – Image pixel values to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Flood Fill Range


#### FloodFillRange


In place flood fill of a region of pixels connected to the pixel at the seed pixel location and with a Pixel value >= Min and <= Max in an image with a new pixel value.


Before calling any of the FloodFill functions the application first needs to call the FloodFillGetBufferSize function to determine the amount of device memory to allocate as a working buffer. The allocated device memory is then passed as the pBuffer parameter to the corresponding FloodFill function.


Optionally the function can return connected region information for the filled region in the pConnectedRegion [NppiConnectedRegion](nppdefs.html#structnppiconnectedregion) structure in host memory. The oBoundingBox x and y will be set to the left and top coordinates and width and height will be set to the right bottom coordinates of the bounding box relative to pSrcDst. Set pConnectedRegion to NULL if not required. Requesting pConnectedRegion information may slightly degrade performance.


Functions


NppStatus nppiFloodFillRange_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp8u nMin, Npp8u nMax, const Npp8u nNewValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nMin – Value of tested pixel must be >= this value.
nMax – Value of tested pixel must be <= this value.
nNewValue – Image pixel value to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillRange_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp8u aMin[3], Npp8u aMax[3], const Npp8u aNewValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aMin – Value of each element of tested pixel must be >= the corresponding aMin value.
aMax – Value of each element of tested pixel must be <= the corresponding aMax value.
aNewValues – Image pixel values to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillRange_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp16u nMin, Npp16u nMax, const Npp16u nNewValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nMin – Value of tested pixel must be >= this value.
nMax – Value of tested pixel must be <= this value.
nNewValue – Image pixel value to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillRange_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp16u aMin[3], Npp16u aMax[3], const Npp16u aNewValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aMin – Value of each element of tested pixel must be >= the corresponding aMin value.
aMax – Value of each element of tested pixel must be <= the corresponding aMax value.
aNewValues – Image pixel values to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillRange_32u_C1IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp32u nMin, Npp32u nMax, const Npp32u nNewValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nMin – Value of tested pixel must be >= this value.
nMax – Value of tested pixel must be <= this value.
nNewValue – Image pixel value to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillRange_32u_C3IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp32u aMin[3], Npp32u aMax[3], const Npp32u aNewValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 32-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aMin – Value of each element of tested pixel must be >= the corresponding aMin value.
aMax – Value of each element of tested pixel must be <= the corresponding aMax value.
aNewValues – Image pixel values to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Flood Fill Range Boundary


#### FloodFillRangeBoundary


In place flood fill of a region of pixels connected to the pixel at the seed pixel location and with a Pixel value >= Min and <= Max in an image with a new pixel value. Also fill boundary of filled region with a specified color.


Before calling any of the FloodFill functions the application first needs to call the FloodFillGetBufferSize function to determine the amount of device memory to allocate as a working buffer. The allocated device memory is then passed as the pBuffer parameter to the corresponding FloodFill function.


Optionally the function can return connected region information for the filled region in the pConnectedRegion [NppiConnectedRegion](nppdefs.html#structnppiconnectedregion) structure in host memory. The oBoundingBox x and y will be set to the left and top coordinates and width and height will be set to the right bottom coordinates of the bounding box relative to pSrcDst. Set pConnectedRegion to NULL if not required. Requesting pConnectedRegion information may slightly degrade performance.


Functions


NppStatus nppiFloodFillRangeBoundary_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp8u nMin, Npp8u nMax, const Npp8u nNewValue, const Npp8u nBoundaryValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nMin – Value of tested pixel must be >= this value.
nMax – Value of tested pixel must be <= this value.
nNewValue – Image pixel value to be used to replace matching pixels.
nBoundaryValue – Image pixel value to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillRangeBoundary_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp8u aMin[3], Npp8u aMax[3], const Npp8u aNewValues[3], const Npp8u aBoundaryValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aMin – Value of each element of tested pixel must be >= the corresponding aMin value.
aMax – Value of each element of tested pixel must be <= the corresponding aMax value.
aNewValues – Image pixel values to be used to replace matching pixels.
aBoundaryValues – Image pixel values to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillRangeBoundary_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp16u nMin, Npp16u nMax, const Npp16u nNewValue, const Npp16u nBoundaryValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nMin – Value of tested pixel must be >= this value.
nMax – Value of tested pixel must be <= this value.
nNewValue – Image pixel value to be used to replace matching pixels.
nBoundaryValue – Image pixel value to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillRangeBoundary_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp16u aMin[3], Npp16u aMax[3], const Npp16u aNewValues[3], const Npp16u aBoundaryValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aMin – Value of each element of tested pixel must be >= the corresponding aMin value.
aMax – Value of each element of tested pixel must be <= the corresponding aMax value.
aNewValues – Image pixel values to be used to replace matching pixels.
aBoundaryValues – Image pixel values to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillRangeBoundary_32u_C1IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp32u nMin, Npp32u nMax, const Npp32u nNewValue, const Npp32u nBoundaryValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nMin – Value of tested pixel must be >= this value.
nMax – Value of tested pixel must be <= this value.
nNewValue – Image pixel value to be used to replace matching pixels.
nBoundaryValue – Image pixel value to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillRangeBoundary_32u_C3IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp32u aMin[3], Npp32u aMax[3], const Npp32u aNewValues[3], const Npp32u aBoundaryValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 32-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aMin – Value of each element of tested pixel must be >= the corresponding aMin value.
aMax – Value of each element of tested pixel must be <= the corresponding aMax value.
aNewValues – Image pixel values to be used to replace matching pixels.
aBoundaryValues – Image pixel values to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Flood Fill Gradient


#### FloodFillGradient


In place flood fill of a region of pixels connected to the pixel at the seed pixel location and with an original pixel value including seed - Min to seed + Max in an image with a new pixel value.


In place flood fill of a region of pixels connected to the pixel at the seed pixel location in an image with a new pixel value.


Before calling any of the FloodFill functions the application first needs to call the FloodFillGetBufferSize function to determine the amount of device memory to allocate as a working buffer. The allocated device memory is then passed as the pBuffer parameter to the corresponding FloodFill function.


Optionally the function can return connected region information for the filled region in the pConnectedRegion [NppiConnectedRegion](nppdefs.html#structnppiconnectedregion) structure in host memory. The oBoundingBox x and y will be set to the left and top coordinates and width and height will be set to the right bottom coordinates of the bounding box relative to pSrcDst. Set pConnectedRegion to NULL if not required. Requesting pConnectedRegion information may slightly degrade performance.


Functions


NppStatus nppiFloodFillGradient_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp8u nMin, Npp8u nMax, const Npp8u nNewValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nMin – Value of tested pixel must be >= seed value - this value.
nMax – Value of tested pixel must be <= seed value + this value.
nNewValue – Image pixel value to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillGradient_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp8u aMin[3], Npp8u aMax[3], const Npp8u aNewValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aMin – Value of each element of tested pixel must be >= the corresponding seed value - aMin value.
aMax – Value of each element of tested pixel must be <= the corresponding seed value + aMax value.
aNewValues – Image pixel values to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillGradient_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp16u nMin, Npp16u nMax, const Npp16u nNewValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nMin – Value of tested pixel must be >= seed value - this value.
nMax – Value of tested pixel must be <= seed value + this value.
nNewValue – Image pixel value to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillGradient_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp16u aMin[3], Npp16u aMax[3], const Npp16u aNewValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aMin – Value of each element of tested pixel must be >= the corresponding seed value - aMin value.
aMax – Value of each element of tested pixel must be <= the corresponding seed value + aMax value.
aNewValues – Image pixel values to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillGradient_32u_C1IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp32u nMin, Npp32u nMax, const Npp32u nNewValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nMin – Value of tested pixel must be >= seed value - this value.
nMax – Value of tested pixel must be <= seed value + this value.
nNewValue – Image pixel value to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillGradient_32u_C3IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp32u aMin[3], Npp32u aMax[3], const Npp32u aNewValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 32-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aMin – Value of each element of tested pixel must be >= the corresponding seed value - aMin value.
aMax – Value of each element of tested pixel must be <= the corresponding seed value + aMax value.
aNewValues – Image pixel values to be used to replace matching pixels.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Flood Fill Gradient Boundary


#### FloodFillGradientBoundary


In place flood fill of a region of pixels connected to the pixel at the seed pixel location and with an original pixel value including seed - Min to seed + Max in an image with a new pixel value. Also fill boundary of filled region with a specified color.


In place flood fill of a region of pixels connected to the pixel at the seed pixel location in an image with a new pixel value.


Before calling any of the FloodFill functions the application first needs to call the FloodFillGetBufferSize function to determine the amount of device memory to allocate as a working buffer. The allocated device memory is then passed as the pBuffer parameter to the corresponding FloodFill function.


Optionally the function can return connected region information for the filled region in the pConnectedRegion [NppiConnectedRegion](nppdefs.html#structnppiconnectedregion) structure in host memory. The oBoundingBox x and y will be set to the left and top coordinates and width and height will be set to the right bottom coordinates of the bounding box relative to pSrcDst. Set pConnectedRegion to NULL if not required. Requesting pConnectedRegion information may slightly degrade performance.


Functions


NppStatus nppiFloodFillGradientBoundary_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp8u nMin, Npp8u nMax, const Npp8u nNewValue, const Npp8u nBoundaryValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nMin – Value of tested pixel must be >= seed value - this value.
nMax – Value of tested pixel must be <= seed value + this value.
nNewValue – Image pixel value to be used to replace matching pixels.
nBoundaryValue – Image pixel value to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillGradientBoundary_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp8u aMin[3], Npp8u aMax[3], const Npp8u aNewValues[3], const Npp8u aBoundaryValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aMin – Value of each element of tested pixel must be >= the corresponding seed value - aMin value.
aMax – Value of each element of tested pixel must be <= the corresponding seed value + aMax value.
aNewValues – Image pixel values to be used to replace matching pixels.
aBoundaryValues – Image pixel values to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillGradientBoundary_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp16u nMin, Npp16u nMax, const Npp16u nNewValue, const Npp16u nBoundaryValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nMin – Value of tested pixel must be >= seed value - this value.
nMax – Value of tested pixel must be <= seed value + this value.
nNewValue – Image pixel value to be used to replace matching pixels.
nBoundaryValue – Image pixel value to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillGradientBoundary_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp16u aMin[3], Npp16u aMax[3], const Npp16u aNewValues[3], const Npp16u aBoundaryValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aMin – Value of each element of tested pixel must be >= the corresponding seed value - aMin value.
aMax – Value of each element of tested pixel must be <= the corresponding seed value + aMax value.
aNewValues – Image pixel values to be used to replace matching pixels.
aBoundaryValues – Image pixel values to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillGradientBoundary_32u_C1IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp32u nMin, Npp32u nMax, const Npp32u nNewValue, const Npp32u nBoundaryValue, NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit unsigned integer grayscale in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
nMin – Value of tested pixel must be >= seed value - this value.
nMax – Value of tested pixel must be <= seed value + this value.
nNewValue – Image pixel value to be used to replace matching pixels.
nBoundaryValue – Image pixel value to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiFloodFillGradientBoundary_32u_C3IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiPoint oSeed, Npp32u aMin[3], Npp32u aMax[3], const Npp32u aNewValues[3], const Npp32u aBoundaryValues[3], NppiNorm eNorm, NppiSize oSizeROI, NppiConnectedRegion *pConnectedRegion, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
3 channel 32-bit unsigned integer color in place flood fill.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step in bytes.
oSeed – Image location of seed pixel value to be used for comparison.
aMin – Value of each element of tested pixel must be >= the corresponding seed value - aMin value.
aMax – Value of each element of tested pixel must be <= the corresponding seed value + aMax value.
aNewValues – Image pixel values to be used to replace matching pixels.
aBoundaryValues – Image pixel values to be used for region boundary.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
oSizeROI – Region-Of-Interest (ROI).
pConnectedRegion – Optional host memory pointer to an NppiConnectedRegion object which returns information about the filled region. Set to NULL if not needed.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding FloodFillGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


## Label Markers


### LabelMarkers


Generate image connected region label markers to be used for later image segmentation.


These functions have been deprecated. Use LabelMarkersUF functions instead.


LabelMarkersUFGetBufferSize


Before calling any of the LabelMarkersUF functions the application first needs to call the LabelMarkersGetBufferSize function to determine the amount of device memory to allocate as a working buffer.


The application allocated device memory is then passed as the pBuffer parameter to the corresponding LabelMarkersUF function.


NppStatus nppiLabelMarkersUFGetBufferSize_32u_C1R(NppiSize oSizeROI, int *hpBufferSize)
Calculate scratch buffer size needed 1 channel 32-bit unsigned integer LabelMarkersUF function based on destination image oSizeROI width and height.

Parameters

oSizeROI – Region-Of-Interest (ROI).
hpBufferSize – Required buffer size in bytes.


### Label MarkersUF


#### LabelMarkersUF


Generate image connected region label markers to be used for later image segmentation.


A connected region is any pixel region where all pixels in the region have the same pixel value. Note that marker label IDs generally increase in value from image left to right and top to bottom they are not generated in any particular order and there may be numeric gaps between sequential marker IDs. To limit the number of marker IDs generated the application should pass the image through a threshold filter before calling this funcion. Doing so however does not necessarily limit the maximum marker ID value generated by this function. Note that these functions currently only support image ROI sizes up to 4 gigapixels. Also note that while these functions support destination image pitches that are not exactly equal to oSizeROI.width * sizeof(Npp32u) it can avoid a cudaMemCpyAsync() call to copy the final result from the working buffer to the destination image if the pitch exactly equals oSizeROI.width * sizeof(Npp32u).


Before calling any of the LabelMarkersUF functions the application first needs to call the LabelMarkersUFGetBufferSize to determine the amount of device memory to allocate as a working buffer. The allocated device memory is then passed as the pBuffer parameter to the corresponding LabelMarkersUF function.


The algorithm used in this implementation is based on the one described in “An Optimized Union-Find Algorithm for Connected Components Labeling Using GPUs” by Jun Chen and others.


Note that the destination image in these functions must be allocated with cudaMalloc() and NOT cudaMallocPitch(). Also the pitch of the output image MUST be set to oSizeROI.width * sizeof(Npp32u).


Functions


NppStatus nppiLabelMarkersUF_8u32u_C1R_Ctx(Npp8u *pSrc, int nSrcStep, Npp32u *pDst, int nDstStep, NppiSize oSizeROI, NppiNorm eNorm, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit to 32-bit unsigned integer label markers image generation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding LabelMarkersUFGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiLabelMarkersUF_16u32u_C1R_Ctx(Npp16u *pSrc, int nSrcStep, Npp32u *pDst, int nDstStep, NppiSize oSizeROI, NppiNorm eNorm, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit to 32-bit unsigned integer label markers image generation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding LabelMarkersUFGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiLabelMarkersUF_32u_C1R_Ctx(Npp32u *pSrc, int nSrcStep, Npp32u *pDst, int nDstStep, NppiSize oSizeROI, NppiNorm eNorm, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit to 32-bit unsigned integer label markers image generation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding LabelMarkersUFGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Label MarkersUF Batch


#### LabelMarkersUFBatch


Generate image connected region label markers to be used for later image segmentation for a batched list of images.


A connected region is any pixel region where all pixels in the region have the same pixel value. Note that marker label IDs generally increase in value from image left to right and top to bottom they are not generated in any particular order and there may be numeric gaps between sequential marker IDs. To limit the number of marker IDs generated the application should pass the image through a threshold filter before calling this funcion. Doing so however does not necessarily limit the maximum marker ID value generated by this function. Note that these functions currently only support image ROI sizes up to 4 gigapixels. Also note that these functions work directly in the destination image so destination pitch MUST be equal to destination ROI.width * sizeof(Npp32u) and even if destination pitch is greater than that the output will be in that format. If this doesn’t work for you use the single image version of these functions or cudaMemCopy2D can be called for each output image to restore the original pitch. Note that all source and destination images in the batch list must contain enough device memory to support the full ROI size. ROIs in descriptor lists are ignored in these functions.


The algorithm used in this implementation is based on the one described in “An Optimized Union-Find Algorithm for Connected Components Labeling Using GPUs” by Jun Chen and others.


Note that the destination images in these functions must be allocated with cudaMalloc() and NOT cudaMallocPitch(). Also the pitch of the output image MUST be set to oSizeROI.width * sizeof(Npp32u).


Functions


NppStatus nppiLabelMarkersUFBatch_8u32u_C1R_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppiNorm eNorm, NppStreamContext nppStreamCtx)
1 channel 8-bit to 32-bit unsigned integer label markers image generation with fixed destination ROI applied to all images in the batch.

Parameters

pSrcBatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory source image descriptors, oSize element is ignored.
pDstBatchList – Destination-Batch-Images Pointer device memory pointer to the list of device memory destination image descriptors, oSize element is ignored.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity for all images in batch.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiLabelMarkersUFBatch_16u32u_C1R_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppiNorm eNorm, NppStreamContext nppStreamCtx)
1 channel 16-bit to 32-bit unsigned integer label markers image generation with fixed destination ROI applied to all images in the batch.

Parameters

pSrcBatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory source image descriptors, oSize element is ignored.
pDstBatchList – Destination-Batch-Images Pointer device memory pointer to the list of device memory destination image descriptors, oSize element is ignored.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity for all images in batch.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiLabelMarkersUFBatch_32u_C1R_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppiNorm eNorm, NppStreamContext nppStreamCtx)
1 channel 32-bit to 32-bit unsigned integer label markers image generation with fixed destination ROI applied to all images in the batch.

Parameters

pSrcBatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory source image descriptors, oSize element is ignored.
pDstBatchList – Destination-Batch-Images Pointer device memory pointer to the list of device memory destination image descriptors, oSize element is ignored.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity for all images in batch.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Label MarkersUF Batch Advanced


#### LabelMarkersUFBatchAdvanced


Generate image connected region label markers to be used for later image segmentation for a batched list of images.


A connected region is any pixel region where all pixels in the region have the same pixel value. Note that marker label IDs generally increase in value from image left to right and top to bottom they are not generated in any particular order and there may be numeric gaps between sequential marker IDs. To limit the number of marker IDs generated the application should pass the image through a threshold filter before calling this funcion. Doing so however does not necessarily limit the maximum marker ID value generated by this function. Note that these functions currently only support image ROI sizes up to 4 gigapixels. Also note that these functions work directly in the destination image so destination pitch MUST be equal to destination ROI.width * sizeof(Npp32u) for each destination image in the list and even if the destination image pitch is greater than that of the output will be in that format. If this doesn’t work for you use the single image version of these functions or cudaMemCopy2D can be called for each output image to restore the original pitch. Note that all source and destination images in the batch list must contain enough device memory to contain their specified ROI size.


The algorithm used in this implementation is based on the one described in “An Optimized Union-Find Algorithm for Connected Components Labeling Using GPUs” by Jun Chen and others.


Note that the destination images in these functions must be allocated with cudaMalloc() and NOT cudaMallocPitch(). Also the pitch of the output image MUST be set to oSizeROI.width * sizeof(Npp32u).


Functions


NppStatus nppiLabelMarkersUFBatch_8u32u_C1R_Advanced_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppiNorm eNorm, NppStreamContext nppStreamCtx)
1 channel 8-bit to 32-bit unsigned integer label markers image generation with per image destination ROI.

Parameters

pSrcBatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory source image descriptors, oSize element is ignored.
pDstBatchList – Destination-Batch-Images Pointer device memory pointer to the list of device memory destination image descriptors.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI) maximum ROI width and height of ALL images in the batch.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity for all images in batch.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiLabelMarkersUFBatch_16u32u_C1R_Advanced_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppiNorm eNorm, NppStreamContext nppStreamCtx)
1 channel 16-bit to 32-bit unsigned integer label markers image generation with per image destination ROI.

Parameters

pSrcBatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory source image descriptors, oSize element is ignored.
pDstBatchList – Destination-Batch-Images Pointer device memory pointer to the list of device memory destination image descriptors.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI) maximum ROI width and height of ALL images in the batch.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity for all images in batch.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiLabelMarkersUFBatch_32u_C1R_Advanced_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppiNorm eNorm, NppStreamContext nppStreamCtx)
1 channel 32-bit to 32-bit unsigned integer label markers image generation with per image destination ROI.

Parameters

pSrcBatchList – Source-Batch-Images Pointer device memory pointer to the list of device memory source image descriptors, oSize element is ignored.
pDstBatchList – Destination-Batch-Images Pointer device memory pointer to the list of device memory destination image descriptors.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI) maximum ROI width and height of ALL images in the batch.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity for all images in batch.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Image Filter Compress Marker Labels


Removes sparseness between marker label IDs output from LabelMarkers call.


CompressMarkerLabelsGetBufferSize


Before calling any of the CompressMarkerLabels functions the application first needs to call the corresponding CompressMarkerLabelsGetBufferSize function to determine the amount of device memory to allocate as a working buffer.


The application allocated device memory is then passed as the pBuffer parameter to the corresponding CompressMarkerLabels function.


NppStatus nppiCompressMarkerLabelsGetBufferSize_32u_C1R(int nStartingNumber, int *hpBufferSize)
Calculate scratch buffer size needed for 1 channel 32-bit unsigned integer CompressMarkerLabels function based on the number returned in pNumber from a previous nppiLabelMarkers call.
Note that this is the only function that supports the nppiCompressMarkerLabelsUF_32u function and that nStartingNumber MUST be ROI width * ROI height when used with that function.

Parameters

nStartingNumber – The value returned from a previous call to the nppiLabelMarkers_32u function or ROI width * ROI height for images generated by the nppiLabelMarkersUF function and those values MUST match the values used those used in that call.
hpBufferSize – Required buffer size in bytes.


CompressMarkerLabels


NOTE: The previous versions of these functions have been deprecated.


Only nppiCompressMarkerLabelsUF_32u works with output from nppiLabelMarkersUF functions.


NppStatus nppiCompressMarkerLabelsUF_32u_C1IR_Ctx(Npp32u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nStartingNumber, int *pNewNumber, Npp8u *pBuffer, NppStreamContext nppStreamCtx)
1 channel 32-bit unsigned integer in place connected region marker label renumbering for output from nppiLabelMarkersUF functions only with numbering sparseness elimination.

Note that the image in this function must be allocated with cudaMalloc() and NOT cudaMallocPitch(). Also the pitch MUST be set to oSizeROI.width * sizeof(Npp32u). And the image pointer and oSizeROI values MUST match those used when nppiLabelMarkersUF was called.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – Source-Image Line Step. NOTE THAT THIS VALUE MUST BE EQUAL TO oSizeROI.width * sizeof(Npp32u).
oSizeROI – Region-Of-Interest (ROI).
nStartingNumber – MUST be ROI width * ROI height and MUST match ROI values used in the label markers generation function call.
pNewNumber – Pointer to host memory integer value where the maximum renumbered marker label ID will be returned.
pBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponding CompressMarkerLabelsGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Image Filter Compressed Marker Labels Info


Various methods for extracting information from compressed marker labels.


### Image Filter Contour Pixel Interpolation


#### ContourPixelInterpolation


Various functions for interpolating pixels in image contours.


### Contours Image Marching Squares Interpolation


#### ContoursImageMarchingSquaresInterpolation


Apply Marching Squares bilinear interpolation to all contour pixels in a contours image where contour pixels have values of 0 and non-contour pixels have values of 255.


Functions


NppStatus nppiContoursImageMarchingSquaresInterpolation_32f_C1R_Ctx(Npp8u *pContoursImageDev, Npp32s nContoursImageStep, NppiPoint32f *pContoursInterpolatedImageDev, Npp32s nContoursInterpolatedImageStep, NppiContourPixelDirectionInfo *pContoursDirectionImageDev, Npp32s nContoursDirectionImageStep, NppiContourPixelGeometryInfo *pContoursPixelGeometryListsDev, NppiContourPixelGeometryInfo *pContoursPixelGeometryListsHost, NppiPoint32f *pContoursInterpolatedGeometryListsDev, Npp32u *pContoursPixelsFoundListHost, Npp32u *pContoursPixelsStartingOffsetDev, Npp32u *pContoursPixelsStartingOffsetHost, Npp32u nTotalImagePixelContourCount, Npp32u nMaxMarkerLabelID, Npp32u nFirstContourGeometryListID, Npp32u nLastContourGeometryListID, NppiContourBlockSegment *pContoursBlockSegmentListDev, NppiContourBlockSegment *pContoursBlockSegmentListHost, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
1 channel integer coordinate based contours image to marching squares bilinear interpolated coordinates contours image.
Note that ALL input and output data for the function MUST be in device memory except where noted otherwise. Also nFirstContourID and nLastContourID allow only a portion of the contour geometry lists in the image to be output.
Note that the geometry list for each contour will begin at pContoursGeometryListsHost[pContoursPixelStartingOffsetHost[nContourID] * sizeof(NppiContourPixelGeometryInfo).
Note that to significantly improve performance by default a contour that contains more than 256K pixels will be bypassed when generating the output geometry list. The contour ID and number of contour pixels will be output in the contour list however. You can still get this function to output the geometry of this size contour howver by calling the function with a starting contour ID of that contour ID and and ending contour ID of that contour ID + 1. Note that doing so for contours approaching a million pixels can take many minutes. Also, due to the structure of some images contour ID 0 can contain ALL contours in the image so setting the starting contour ID to 1 can significantly increase output preprocessing performance.
Also note that the ordered contour geometry list is contained in the oContourOrderedGeometryLocation object within the NppiContourPixelGeometryInfo object for each contour pixel and that this location information is the only valid information in the object relevent to that ordered pixel.
Note that for a particular contour geometry pixel list the bounding box for that contour will be contained in the following elements of first pixel (pixel 0) of the corresponding contour pixel list.

pixel[0].oContourPrevPixelLocation.x will contain pCurMarkerLabelsInfo->oMarkerLabelBoundingBox.x      upper left x
pixel[0].oContourPrevPixelLocation.y will contain pCurMarkerLabelsInfo->oMarkerLabelBoundingBox.y      upper left y
pixel[0].oContourNextPixelLocation.x will contain pCurMarkerLabelsInfo->oMarkerLabelBoundingBox.width  lower right x
pixel[0].oContourNextPixelLocation.y will contain pCurMarkerLabelsInfo->oMarkerLabelBoundingBox.height lower right y

Note that while the bounding box is relatively accurate occasionally a few contour pixels may extend beyond the bounding box limits.

Parameters

pContoursImageDev – pointer to device memory image of at least oSizeROI.width * sizeof(Npp8u) * oSizeROI.height bytes.
nContoursImageStep – image line step.
pContoursInterpolatedImageDev – pointer to device memory image of at least oSizeROI.width * sizeof(NppiPoint32f) * OSizeROI.height bytes.
nContoursInterpolatedImageStep – image line step
pContoursDirectionImageDev – Source-Image Pointer to output image in device memory containing per contour pixel direction info around each uniquely labeled connected pixel region returned by corresponding nppiCompressedMarkerLabelsUFInfo call.
nContoursDirectionImageStep – image_line_step for contours image.
pContoursPixelGeometryListsDev – pointer to device memory buffer allocated to be at least as big as size returned by corresponding nppiCompressedMarkerLabelsUFGetGeometryListsSize call.
pContoursPixelGeometryListsHost – pointer to host memory buffer allocated to be at least as big as size returned by corresponding nppiCompressedMarkerLabelsUFGetGeometryListsSize call.
pContoursInterpolatedGeometryListsDev – pointer to device memory buffer allocated to be at least nTotalImagePixelContourCount * sizeof(NppPoint32f) bytes.
pContoursPixelsFoundListHost – host memory pointer to array of nMaxMarkerLabelID unsigned integers returned by previous call to nppiCompressedMarkerLabelsUFContoursPixelGeometryLists_C1R_Ctx.
pContoursPixelsStartingOffsetDev – device memory pointer to array of unsigned integers returned by this call representing the starting offset index of each contour found during geometry list generation.
pContoursPixelsStartingOffsetHost – host memory pointer to array of unsigned integers returned by this call representing the starting offset index of each contour found during geometry list generation.
nTotalImagePixelContourCount – the total number of contour pixels in the image returned by nppiCompressedMarkerLabelsUFInfo_32u_C1R_Ctx() call.
nMaxMarkerLabelID – the value of the maximum marker label ID returned by corresponding compress marker labels UF call.
nFirstContourGeometryListID – the ID of the first contour geometry list to output.
nLastContourGeometryListID – the ID of the last contour geometry list to output, last ID MUST be greater than first ID.
pContoursBlockSegmentListDev – device memory pointer to array of NppiContourBlockSegment objects, contents will be initialized by NPP.
pContoursBlockSegmentListHost – host memory pointer to array of NppiContourBlockSegment objects, contents will be intialized by NPP.
oSizeROI – Region-Of-Interest (ROI) for the images, must be the same as used in previous calls.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiContoursImageMarchingSquaresInterpolation_64f_C1R_Ctx(Npp8u *pContoursImageDev, Npp32s nContoursImageStep, NppiPoint64f *pContoursInterpolatedImageDev, Npp32s nContoursInterpolatedImageStep, NppiContourPixelDirectionInfo *pContoursDirectionImageDev, Npp32s nContoursDirectionImageStep, NppiContourPixelGeometryInfo *pContoursPixelGeometryListsDev, NppiContourPixelGeometryInfo *pContoursPixelGeometryListsHost, NppiPoint64f *pContoursInterpolatedGeometryListsDev, Npp32u *pContoursPixelsFoundListHost, Npp32u *pContoursPixelsStartingOffsetDev, Npp32u *pContoursPixelsStartingOffsetHost, Npp32u nTotalImagePixelContourCount, Npp32u nMaxMarkerLabelID, Npp32u nFirstContourGeometryListID, Npp32u nLastContourGeometryListID, NppiContourBlockSegment *pContoursBlockSegmentListDev, NppiContourBlockSegment *pContoursBlockSegmentListHost, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Note that while the bounding box is relatively accurate occasionally a few contour pixels may extend beyond the bounding box limits.

Parameters

pContoursImageDev – pointer to device memory image of at least oSizeROI.width * sizeof(Npp8u) * oSizeROI.height bytes.
nContoursImageStep – image line step.
pContoursInterpolatedImageDev – pointer to device memory image of at least oSizeROI.width * sizeof(NppiPoint64f) * OSizeROI.height bytes.
nContoursInterpolatedImageStep – image line step
pContoursDirectionImageDev – Source-Image Pointer to output image in device memory containing per contour pixel direction info around each uniquely labeled connected pixel region returned by corresponding nppiCompressedMarkerLabelsUFInfo call.
nContoursDirectionImageStep – image_line_step for contours image.
pContoursPixelGeometryListsDev – pointer to device memory buffer allocated to be at least as big as size returned by corresponding nppiCompressedMarkerLabelsUFGetGeometryListsSize call.
pContoursPixelGeometryListsHost – pointer to host memory buffer allocated to be at least as big as size returned by corresponding nppiCompressedMarkerLabelsUFGetGeometryListsSize call.
pContoursInterpolatedGeometryListsDev – pointer to device memory buffer allocated to be at least nTotalImagePixelContourCount * sizeof(NppPoint64f) bytes.
pContoursPixelsFoundListHost – host memory pointer to array of nMaxMarkerLabelID unsigned integers returned by previous call to nppiCompressedMarkerLabelsUFContoursPixelGeometryLists_C1R_Ctx.
pContoursPixelsStartingOffsetDev – device memory pointer to array of unsigned integers returned by this call representing the starting offset index of each contour found during geometry list generation.
pContoursPixelsStartingOffsetHost – host memory pointer to array of unsigned integers returned by this call representing the starting offset index of each contour found during geometry list generation.
nTotalImagePixelContourCount – the total number of contour pixels in the image returned by nppiCompressedMarkerLabelsUFInfo_32u_C1R_Ctx() call.
nMaxMarkerLabelID – the value of the maximum marker label ID returned by corresponding compress marker labels UF call.
nFirstContourGeometryListID – the ID of the first contour geometry list to output.
nLastContourGeometryListID – the ID of the last contour geometry list to output, last ID MUST be greater than first ID.
pContoursBlockSegmentListDev – device memory pointer to array of NppiContourBlockSegment objects, contents will be initialized by NPP.
pContoursBlockSegmentListHost – host memory pointer to array of NppiContourBlockSegment objects, contents will be intialized by NPP.
oSizeROI – Region-Of-Interest (ROI) for the images, must be the same as used in previous calls.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


## Bound Segments


Note that these functions have been deprecated.


Use the nppiLabelMarkerUF, nppiCompressMarkerLabelsUF, and nppiCompressedMarkerLabelsUFInfo functions to generate connected pixel region boundaries (contours).


## Watershed Segmentation


### WatershedSegmentation


Segments a grayscale image using the watershed segmentation technique described in “Efficient 2D and 3D Watershed on Graphics Processing Unit: Block-Asynchronous Approaches Based on Cellular Automata” by Pablo Quesada-Barriuso and others.


SegmentWatershedGetBufferSize


Before calling any of the SegmentWatershed functions the application first needs to call the corresponding SegmentWatershedGetBufferSize function to determine the amount of device memory to allocate as a working buffer.


The application allocated device memory is then passed as the pBuffer parameter to the corresponding SegmentWatershed function.


NppStatus nppiSegmentWatershedGetBufferSize_8u_C1R(NppiSize oSizeROI, size_t *hpDeviceMemoryBufferSize)
Calculate scratch buffer sizes needed for 1 channel 8-bit unsigned integer watershed segmentation function based on destination image oSizeROI width and height.

Parameters

oSizeROI – Region-Of-Interest (ROI).
hpDeviceMemoryBufferSize – Required device memory buffer size in bytes.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSegmentWatershedGetBufferSize_16u_C1R(NppiSize oSizeROI, size_t *hpDeviceMemoryBufferSize)
Calculate scratch buffer sizes needed for 1 channel 16-bit unsigned integer watershed segmentation function based on destination image oSizeROI width and height.

Parameters

oSizeROI – Region-Of-Interest (ROI).
hpDeviceMemoryBufferSize – Required device memory buffer size in bytes.

Returns

Image Data Related Error Codes, ROI Related Error Codes


SegmentWatershed


Generate an output image containing regions of constant value grayscale defined by watershed segmentation plateau boundaries from a grayscale input image.


Optionally output the corresponding marker labels image.


Before calling any of the SegmentWatershed functions the application first needs to call the corresponding SegmentWatershedGetBufferSize to determine the amount of device memory to allocate as working buffers. The allocatd memory is then passed as the pDeviceMemoryBuffer parameter to the corresponding SegmentWatershed function.


NppStatus nppiSegmentWatershed_8u_C1IR_Ctx(Npp8u *pSrcDst, Npp32s nSrcDstStep, Npp32u *pMarkerLabels, Npp32s nMarkerLabelsStep, NppiNorm eNorm, NppiWatershedSegmentBoundaryType eSegmentBoundaryType, NppiSize oSizeROI, Npp8u *pDeviceMemoryBuffer, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer in place image watershed segmentation generation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – Source-Image Line Step.
pMarkerLabels – Device memory pointer to optionally output the corresponding marker labels image, set to NULL if no marker labels image output is desired.
nMarkerLabelsStep – Marker labels image line step,ignored if pMarkerLabels is NULL.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
eSegmentBoundaryType – Type of segment boundaries, if any, to be added to output image.
oSizeROI – Region-Of-Interest (ROI) for both segmented image and corresponding marker labels image.
pDeviceMemoryBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponging SegmentWatershedGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiSegmentWatershed_16u_C1IR_Ctx(Npp16u *pSrcDst, Npp32s nSrcDstStep, Npp32u *pMarkerLabels, Npp32s nMarkerLabelsStep, NppiNorm eNorm, NppiWatershedSegmentBoundaryType eSegmentBoundaryType, NppiSize oSizeROI, Npp8u *pDeviceMemoryBuffer, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned integer in place image watershed segmentation generation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – Source-Image Line Step.
pMarkerLabels – Device memory pointer to optionally output the corresponding marker labels image, set to NULL if no marker labels image output is desired.
nMarkerLabelsStep – Marker labels image line step, ignored if pMarkerLabels is NULL.
eNorm – Type of pixel connectivity test to use, nppiNormInf will use 8 way connectivity and nppiNormL1 will use 4 way connectivity.
eSegmentBoundaryType – Type of segment boundaries, if any, to be added to output image.
oSizeROI – Region-Of-Interest (ROI) for both segmented image and corresponding marker labels image.
pDeviceMemoryBuffer – Pointer to device memory scratch buffer at least as large as value returned by the corresponging SegmentWatershedGetBufferSize call.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes