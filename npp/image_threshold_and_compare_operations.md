# Image Threshold And Compare Operations — npp 13.1 documentation

>


# Image Threshold And Compare Operations


Methods for pixel-wise threshold and compare operations.


These functions can be found in the nppitc library. Linking to only the sub-libraries that you use can significantly save link time, application load time, and CUDA runtime startup time when using dynamic libraries.


## Image Threshold Operations


### Threshold Operations


Threshold image pixels.


#### Common parameters for nppiThreshold non-inplace and inplace functions:




param pSrcDst
In-Place Image Pointer for inplace functions.

param nSrcDstStep
In-Place-Image Line Step for inplace functions.

param pSrc
Source-Image Pointer for non-inplace functions.

param nSrcStep
Source-Image Line Step for non-inplace functions.

param pDst
Destination-Image Pointer for non-inplace functions.

param nDstStep
Destination-Image Line Step for non-inplace functions.

param oSizeROI
Region-Of-Interest (ROI).

param nThreshold
The threshold value.

param eComparisonOperation
The type of comparison operation to be used. The only valid values are: NPP_CMP_LESS and NPP_CMP_GREATER.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes, or NPP_NOT_SUPPORTED_MODE_ERROR if an invalid comparison operation type is specified.


Functions


NppStatus nppiThreshold_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u nThreshold, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u nThreshold, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u nThreshold, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u nThreshold, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s nThreshold, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_16s_C1IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s nThreshold, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f nThreshold, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f nThreshold, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 16-bit signed short threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_16s_C3IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 16-bit signed short in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char in place image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_16u_AC4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short in place image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit signed short image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_16s_AC4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit signed short in place image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


NppStatus nppiThreshold_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point in place image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold non-inplace and inplace functions:.


### Image Threshold Greater Than Operations


#### Threshold Greater Than Operations


Threshold greater than image pixels.


##### Common parameters for nppiThreshold_GT non-inplace and inplace functions:




param pSrcDst
In-Place Image Pointer for inplace functions.

param nSrcDstStep
In-Place-Image Line Step for inplace functions.

param pSrc
Source-Image Pointer for non-inplace functions.

param nSrcStep
Source-Image Line Step for non-inplace functions.

param pDst
Destination-Image Pointer for non-inplace functions.

param nDstStep
Destination-Image Line Step for non-inplace functions.

param oSizeROI
Region-Of-Interest (ROI).

param nThreshold
The threshold value.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes.


Functions


NppStatus nppiThreshold_GT_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u nThreshold, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u nThreshold, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char in place threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u nThreshold, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u nThreshold, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short in place threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s nThreshold, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_16s_C1IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s nThreshold, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short in place threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f nThreshold, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f nThreshold, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point in place threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char in place threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short in place threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed short threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_16s_C3IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed short in place threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point in place threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_16u_AC4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed short image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_16s_AC4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed short in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


NppStatus nppiThreshold_GT_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GT non-inplace and inplace functions:.


### Image Threshold Less Than Operations


#### Threshold Less Than Operations


Threshold less than image pixels.


##### Common parameters for nppiThreshold_LT non-inplace and inplace functions:




param pSrcDst
In-Place Image Pointer for inplace functions.

param nSrcDstStep
In-Place-Image Line Step for inplace functions.

param pSrc
Source-Image Pointer for non-inplace functions.

param nSrcStep
Source-Image Line Step for non-inplace functions.

param pDst
Destination-Image Pointer for non-inplace functions.

param nDstStep
Destination-Image Line Step for non-inplace functions.

param oSizeROI
Region-Of-Interest (ROI).

param nThreshold
The threshold value.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes.


Functions


NppStatus nppiThreshold_LT_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u nThreshold, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u nThreshold, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char in place threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u nThreshold, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u nThreshold, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short in place threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s nThreshold, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_16s_C1IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s nThreshold, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short in place threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f nThreshold, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f nThreshold, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point in place threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char in place threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short in place threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed short threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_16s_C3IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed short in place threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point in place threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_16u_AC4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed short image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_16s_AC4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed short in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


NppStatus nppiThreshold_LT_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set value is set to nThreshold, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LT non-inplace and inplace functions:.


### Image Threshold Value Operations


#### Threshold Value Operations


Replace thresholded image pixels with a value.


##### Common parameters for nppiThreshold_Val non-inplace and inplace functions:




param pSrcDst
In-Place Image Pointer for inplace functions.

param nSrcDstStep
In-Place-Image Line Step for inplace functions.

param pSrc
Source-Image Pointer for non-inplace functions.

param nSrcStep
Source-Image Line Step for non-inplace functions.

param pDst
Destination-Image Pointer for non-inplace functions.

param nDstStep
Destination-Image Line Step for non-inplace functions.

param oSizeROI
Region-Of-Interest (ROI).

param nThreshold
The threshold value.

param nValue
The threshold replacement value.

param eComparisonOperation
The type of comparison operation to be used. The only valid values are: NPP_CMP_LESS and NPP_CMP_GREATER.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes, or NPP_NOT_SUPPORTED_MODE_ERROR if an invalid comparison operation type is specified.


Functions


NppStatus nppiThreshold_Val_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u nThreshold, const Npp8u nValue, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u nThreshold, const Npp8u nValue, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u nThreshold, const Npp16u nValue, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u nThreshold, const Npp16u nValue, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s nThreshold, const Npp16s nValue, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_16s_C1IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s nThreshold, const Npp16s nValue, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f nThreshold, const Npp32f nValue, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f nThreshold, const Npp32f nValue, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], const Npp8u rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], const Npp8u rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], const Npp16u rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], const Npp16u rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], const Npp16s rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 16-bit signed short threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_16s_C3IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], const Npp16s rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 16-bit signed short in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], const Npp32f rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], const Npp32f rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point in place threshold.
If for a comparison operations OP the predicate (sourcePixel OP nThreshold) is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], const Npp8u rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], const Npp8u rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char in place image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], const Npp16u rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_16u_AC4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], const Npp16u rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short in place image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], const Npp16s rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit signed short image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_16s_AC4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], const Npp16s rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit signed short in place image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], const Npp32f rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


NppStatus nppiThreshold_Val_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], const Npp32f rValues[3], NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point in place image threshold, not affecting Alpha.
If for a comparison operations OP the predicate (sourcePixel.channel OP nThreshold) is true, the channel value is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_Val non-inplace and inplace functions:.


### Image Threshold Greater Than Value Operations


#### Threshold Greater Than Value Operations


Replace image pixels greater than threshold with a value.


##### Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:




param pSrcDst
In-Place Image Pointer for inplace functions.

param nSrcDstStep
In-Place-Image Line Step for inplace functions.

param pSrc
Source-Image Pointer for non-inplace functions.

param nSrcStep
Source-Image Line Step for non-inplace functions.

param pDst
Destination-Image Pointer for non-inplace functions.

param nDstStep
Destination-Image Line Step for non-inplace functions.

param oSizeROI
Region-Of-Interest (ROI).

param nThreshold
The threshold value.

param nValue
The threshold replacement value.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes.


Functions


NppStatus nppiThreshold_GTVal_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u nThreshold, const Npp8u nValue, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u nThreshold, const Npp8u nValue, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char in place threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u nThreshold, const Npp16u nValue, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u nThreshold, const Npp16u nValue, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short in place threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s nThreshold, const Npp16s nValue, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_16s_C1IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s nThreshold, const Npp16s nValue, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short in place threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f nThreshold, const Npp32f nValue, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f nThreshold, const Npp32f nValue, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point in place threshold.
If for a comparison operations sourcePixel is greater than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], const Npp8u rValues[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char threshold.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], const Npp8u rValues[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char in place threshold.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], const Npp16u rValues[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short threshold.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], const Npp16u rValues[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short in place threshold.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], const Npp16s rValues[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed short threshold.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_16s_C3IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], const Npp16s rValues[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed short in place threshold.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], const Npp32f rValues[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point threshold.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], const Npp32f rValues[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point in place threshold.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], const Npp8u rValues[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], const Npp8u rValues[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], const Npp16u rValues[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_16u_AC4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], const Npp16u rValues[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], const Npp16s rValues[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed short image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_16s_AC4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], const Npp16s rValues[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed short in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], const Npp32f rValues[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_GTVal_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], const Npp32f rValues[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is greater than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_GTVal non-inplace and inplace functions:.


### Image Threshold Less Than Value Operations


#### Threshold Less Than Value Operations


Replace image pixels less than threshold with a value.


##### Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:




param pSrcDst
In-Place Image Pointer for inplace functions.

param nSrcDstStep
In-Place-Image Line Step for inplace functions.

param pSrc
Source-Image Pointer for non-inplace functions.

param nSrcStep
Source-Image Line Step for non-inplace functions.

param pDst
Destination-Image Pointer for non-inplace functions.

param nDstStep
Destination-Image Line Step for non-inplace functions.

param oSizeROI
Region-Of-Interest (ROI).

param nThreshold
The threshold value.

param nValue
The threshold replacement value.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes.


Functions


NppStatus nppiThreshold_LTVal_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u nThreshold, const Npp8u nValue, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u nThreshold, const Npp8u nValue, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char in place threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u nThreshold, const Npp16u nValue, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u nThreshold, const Npp16u nValue, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short in place threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s nThreshold, const Npp16s nValue, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_16s_C1IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s nThreshold, const Npp16s nValue, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short in place threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f nThreshold, const Npp32f nValue, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f nThreshold, const Npp32f nValue, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point in place threshold.
If for a comparison operations sourcePixel is less than nThreshold is true, the pixel is set to nValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], const Npp8u rValues[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char threshold.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], const Npp8u rValues[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char in place threshold.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], const Npp16u rValues[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short threshold.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], const Npp16u rValues[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short in place threshold.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], const Npp16s rValues[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed short threshold.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_16s_C3IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], const Npp16s rValues[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed short in place threshold.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], const Npp32f rValues[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point threshold.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], const Npp32f rValues[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point in place threshold.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], const Npp8u rValues[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholds[3], const Npp8u rValues[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], const Npp16u rValues[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_16u_AC4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholds[3], const Npp16u rValues[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], const Npp16s rValues[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed short image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_16s_AC4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholds[3], const Npp16s rValues[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed short in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], const Npp32f rValues[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTVal_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholds[3], const Npp32f rValues[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThreshold is true, the pixel is set value is set to rValue, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTVal non-inplace and inplace functions:.


### Image Fused AbsDiff Threshold Greater Than Value Operations


#### Fused AbsDiff Threshold Greater Than Value Operations


Replace image pixels greater than threshold with a value.


Supported data types include NPP_8U, NPP_16U, NPP_16S, NPP_32F. Supported channel counts include NPP_CH_1, NPP_CH_3, NPP_CH_A4.


param eSrcDstType
image data type.

param eSrcDstChannels
image channels.

param pSrcDst
In-Place Image Pointer for inplace functions.

param nSrcDstStep
In-Place-Image Line Step for inplace functions.

param pSrc1
Source-Image Pointer for non-inplace functions.

param nSrc1Step
Source-Image Line Step for non-inplace functions.

param pSrc2
Source-Image Pointer to second source image for non-inplace functions.

param nSrc2Step
Source-Image Line Step of second source image for non-inplace functions.

param pDst
Destination-Image Pointer for non-inplace functions.

param nDstStep
Destination-Image Line Step for non-inplace functions.

param oSizeROI
Region-Of-Interest (ROI).

param pThreshold
The threshold value.

param pValue
The threshold replacement value.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes.


Functions


NppStatus nppiFusedAbsDiff_Threshold_GTVal_Ctx(NppDataType eSrcDstType, NppiChannels eSrcDstChannels, const void *pSrc1, int nSrc1Step, const void *pSrc2, int nSrc2Step, void *pDst, int nDstStep, NppiSize oSizeROI, const void *pThreshold, const void *pvalue, NppStreamContext nppStreamCtx)
Image fused absdiff and greater than threshold value.
If for a comparison operations absdiff of sourcePixels is greater than pThreshold is true, the output pixel is set to pValue, otherwise it is set to absdiff of sourcePixels.


NppStatus nppiFusedAbsDiff_Threshold_GTVal_I_Ctx(NppDataType eSrcDstType, NppiChannels eSrcDstChannels, void *pSrcDst, int nSrcDstStep, const void *pSrc2, int nSrc2Step, NppiSize oSizeROI, const void *pThreshold, const void *pvalue, NppStreamContext nppStreamCtx)
In place fused absdiff image greater than threshold value.
If for a comparison operations absdiff of sourcePixels is greater than pThreshold is true, the output pixel is set to pValue, otherwise it is set to absdiff of sourcePixels.


### Image Threshold Less Than Value Greater Than Value Operations


#### Threshold Less Than Value Or Greater Than Value Operations


Replace image pixels less than thresholdLT or greater than thresholdGT with with valueLT or valueGT respectively.


##### Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:




param pSrcDst
In-Place Image Pointer for inplace functions.

param nSrcDstStep
In-Place-Image Line Step for inplace functions.

param pSrc
Source-Image Pointer for non-inplace functions.

param nSrcStep
Source-Image Line Step for non-inplace functions.

param pDst
Destination-Image Pointer for non-inplace functions.

param nDstStep
Destination-Image Line Step for non-inplace functions.

param oSizeROI
Region-Of-Interest (ROI).

param nThresholdLT
The thresholdLT value.

param nValueLT
The thresholdLT replacement value.

param nThresholdGT
The thresholdGT value.

param nValueGT
The thresholdGT replacement value.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes.


Functions


NppStatus nppiThreshold_LTValGTVal_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u nThresholdLT, const Npp8u nValueLT, const Npp8u nThresholdGT, const Npp8u nValueGT, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char threshold.
If for a comparison operations sourcePixel is less than nThresholdLT is true, the pixel is set to nValueLT, else if sourcePixel is greater than nThresholdGT the pixel is set to nValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u nThresholdLT, const Npp8u nValueLT, const Npp8u nThresholdGT, const Npp8u nValueGT, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char in place threshold.
If for a comparison operations sourcePixel is less than nThresholdLT is true, the pixel is set to nValueLT, else if sourcePixel is greater than nThresholdGT the pixel is set to nValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u nThresholdLT, const Npp16u nValueLT, const Npp16u nThresholdGT, const Npp16u nValueGT, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short threshold.
If for a comparison operations sourcePixel is less than nThresholdLT is true, the pixel is set to nValueLT, else if sourcePixel is greater than nThresholdGT the pixel is set to nValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u nThresholdLT, const Npp16u nValueLT, const Npp16u nThresholdGT, const Npp16u nValueGT, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short in place threshold.
If for a comparison operations sourcePixel is less than nThresholdLT is true, the pixel is set to nValueLT, else if sourcePixel is greater than nThresholdGT the pixel is set to nValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s nThresholdLT, const Npp16s nValueLT, const Npp16s nThresholdGT, const Npp16s nValueGT, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short threshold.
If for a comparison operations sourcePixel is less than nThresholdLT is true, the pixel is set to nValueLT, else if sourcePixel is greater than nThresholdGT the pixel is set to nValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_16s_C1IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s nThresholdLT, const Npp16s nValueLT, const Npp16s nThresholdGT, const Npp16s nValueGT, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short in place threshold.
If for a comparison operations sourcePixel is less than nThresholdLT is true, the pixel is set to nValueLT, else if sourcePixel is greater than nThresholdGT the pixel is set to nValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f nThresholdLT, const Npp32f nValueLT, const Npp32f nThresholdGT, const Npp32f nValueGT, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point threshold.
If for a comparison operations sourcePixel is less than nThresholdLT is true, the pixel is set to nValueLT, else if sourcePixel is greater than nThresholdGT the pixel is set to nValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f nThresholdLT, const Npp32f nValueLT, const Npp32f nThresholdGT, const Npp32f nValueGT, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point in place threshold.
If for a comparison operations sourcePixel is less than nThresholdLT is true, the pixel is set to nValueLT, else if sourcePixel is greater than nThresholdGT the pixel is set to nValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholdsLT[3], const Npp8u rValuesLT[3], const Npp8u rThresholdsGT[3], const Npp8u rValuesGT[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char threshold.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholdsLT[3], const Npp8u rValuesLT[3], const Npp8u rThresholdsGT[3], const Npp8u rValuesGT[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char in place threshold.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholdsLT[3], const Npp16u rValuesLT[3], const Npp16u rThresholdsGT[3], const Npp16u rValuesGT[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short threshold.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholdsLT[3], const Npp16u rValuesLT[3], const Npp16u rThresholdsGT[3], const Npp16u rValuesGT[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short in place threshold.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholdsLT[3], const Npp16s rValuesLT[3], const Npp16s rThresholdsGT[3], const Npp16s rValuesGT[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed short threshold.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_16s_C3IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholdsLT[3], const Npp16s rValuesLT[3], const Npp16s rThresholdsGT[3], const Npp16s rValuesGT[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed short in place threshold.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholdsLT[3], const Npp32f rValuesLT[3], const Npp32f rThresholdsGT[3], const Npp32f rValuesGT[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point threshold.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholdsLT[3], const Npp32f rValuesLT[3], const Npp32f rThresholdsGT[3], const Npp32f rValuesGT[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point in place threshold.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u rThresholdsLT[3], const Npp8u rValuesLT[3], const Npp8u rThresholdsGT[3], const Npp8u rValuesGT[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set value is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp8u rThresholdsLT[3], const Npp8u rValuesLT[3], const Npp8u rThresholdsGT[3], const Npp8u rValuesGT[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set value is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u rThresholdsLT[3], const Npp16u rValuesLT[3], const Npp16u rThresholdsGT[3], const Npp16u rValuesGT[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set value is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_16u_AC4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16u rThresholdsLT[3], const Npp16u rValuesLT[3], const Npp16u rThresholdsGT[3], const Npp16u rValuesGT[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set value is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp16s rThresholdsLT[3], const Npp16s rValuesLT[3], const Npp16s rThresholdsGT[3], const Npp16s rValuesGT[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed short image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set value is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_16s_AC4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp16s rThresholdsLT[3], const Npp16s rValuesLT[3], const Npp16s rThresholdsGT[3], const Npp16s rValuesGT[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed short in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set value is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f rThresholdsLT[3], const Npp32f rValuesLT[3], const Npp32f rThresholdsGT[3], const Npp32f rValuesGT[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set value is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


NppStatus nppiThreshold_LTValGTVal_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f rThresholdsLT[3], const Npp32f rValuesLT[3], const Npp32f rThresholdsGT[3], const Npp32f rValuesGT[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point in place image threshold, not affecting Alpha.
If for a comparison operations sourcePixel is less than rThresholdLT is true, the pixel is set value is set to rValueLT, else if sourcePixel is greater than rThresholdGT the pixel is set to rValueGT, otherwise it is set to sourcePixel.
For common parameter descriptions, see Common parameters for nppiThreshold_LTValGTVal non-inplace and inplace functions:.


## Image Comparison Operations


### Comparison Operations


Compare the pixels of two images or one image and a constant value and create a binary result image. In case of multi-channel image types, the condition must be fulfilled for all channels, otherwise the comparison is considered false. The “binary” result image is of type 8u_C1. False is represented by 0, true by NPP_MAX_8U.


### Compare Images Operations


#### Compare Images Operations


Compare the pixels of two images and create a binary result image. In case of multi-channel image types, the condition must be fulfilled for all channels, otherwise the comparison is considered false. The “binary” result image is of type 8u_C1. False is represented by 0, true by NPP_MAX_8U.


##### Common parameters for nppiCompare functions:




param pSrc1
Source-Image Pointer.

param nSrc1Step
Source-Image Line Step.

param pSrc2
Source-Image Pointer.

param nSrc2Step
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param eComparisonOperation
Specifies the comparison operation to be used in the pixel comparison.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiCompare_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char image compare.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char image compare.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char image compare.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char image compare, not affecting Alpha.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short image compare.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short image compare.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short image compare.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short image compare, not affecting Alpha.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short image compare.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_16s_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 16-bit signed short image compare.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_16s_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit signed short image compare.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_16s_AC4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit signed short image compare, not affecting Alpha.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point image compare.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point image compare.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point image compare.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


NppStatus nppiCompare_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 32-bit signed floating point compare, not affecting Alpha.
Compare pSrc1’s pixels with corresponding pixels in pSrc2.
For common parameter descriptions, see Common parameters for nppiCompare functions:.


### Compare Image With Constant Operations


#### Compare Image With Constant Operations


Compare the pixels of an image with a constant value and create a binary result image. In case of multi-channel image types, the condition must be fulfilled for all channels, otherwise the comparison is considered false. The “binary” result image is of type 8u_C1. False is represented by 0, true by NPP_MAX_8U.


##### Common parameters for nppiCompareC functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param nConstant
constant value for single channel functions.

param pConstants
pointer to a list of constant values, one per color channel for multi-channel functions.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param eComparisonOperation
Specifies the comparison operation to be used in the pixel comparison.

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiCompareC_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned char image compare with constant value.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned char image compare with constant value.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char image compare with constant value.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned char image compare, not affecting Alpha.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp16u nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned short image compare with constant value.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp16u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned short image compare with constant value.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp16u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short image compare with constant value.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp16u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned short image compare, not affecting Alpha.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, const Npp16s nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 16-bit signed short image compare with constant value.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, const Npp16s *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 16-bit signed short image compare with constant value.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, const Npp16s *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit signed short image compare with constant value.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, const Npp16s *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 16-bit signed short image compare, not affecting Alpha.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp32f nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point image compare with constant value.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp32f *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point image compare with constant value.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp32f *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point image compare with constant value.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


NppStatus nppiCompareC_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp32f *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppCmpOp eComparisonOperation, NppStreamContext nppStreamCtx)
4 channel 32-bit signed floating point compare, not affecting Alpha.
Compare pSrc’s pixels with constant value.
For common parameter descriptions, see Common parameters for nppiCompareC functions:.


### Compare Image Differences With Epsilon Operations


#### Compare Image Differences With Epsilon Operations


Compare the pixels value differences of two images with an epsilon value and create a binary result image. In case of multi-channel image types, the condition must be fulfilled for all channels, otherwise the comparison is considered false. The “binary” result image is of type 8u_C1. False is represented by 0, true by NPP_MAX_8U.


##### Common parameters for nppiCompareEqualEps functions include:




param pSrc1
Source-Image Pointer.

param nSrc1Step
Source-Image Line Step.

param pSrc2
Source-Image Pointer.

param nSrc2Step
Source-Image Line Step.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param nEpsilon
epsilon tolerance value to compare to pixel absolute differences

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiCompareEqualEps_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp32f nEpsilon, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point image compare whether two images are equal within epsilon.
Compare pSrc1’s pixels with corresponding pixels in pSrc2 to determine whether they are equal with a difference of epsilon.
For common parameter descriptions, see Common parameters for nppiCompareEqualEps functions include:.


NppStatus nppiCompareEqualEps_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp32f nEpsilon, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point image compare whether two images are equal within epsilon.
Compare pSrc1’s pixels with corresponding pixels in pSrc2 to determine whether they are equal with a difference of epsilon.
For common parameter descriptions, see Common parameters for nppiCompareEqualEps functions include:.


NppStatus nppiCompareEqualEps_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp32f nEpsilon, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point image compare whether two images are equal within epsilon.
Compare pSrc1’s pixels with corresponding pixels in pSrc2 to determine whether they are equal with a difference of epsilon.
For common parameter descriptions, see Common parameters for nppiCompareEqualEps functions include:.


NppStatus nppiCompareEqualEps_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp32f nEpsilon, NppStreamContext nppStreamCtx)
4 channel 32-bit signed floating point compare whether two images are equal within epsilon, not affecting Alpha.
Compare pSrc1’s pixels with corresponding pixels in pSrc2 to determine whether they are equal with a difference of epsilon.
For common parameter descriptions, see Common parameters for nppiCompareEqualEps functions include:.


### Compare Image Difference To Constant With Epsilon Operations


#### Compare Image Difference With Constant Within Epsilon Operations


Compare differences between image pixels and constant within an epsilon value and create a binary result image. In case of multi-channel image types, the condition must be fulfilled for all channels, otherwise the comparison is considered false. The “binary” result image is of type 8u_C1. False is represented by 0, true by NPP_MAX_8U.


##### Common parameters for nppiCompareEqualEpsC functions:




param pSrc
Source-Image Pointer.

param nSrcStep
Source-Image Line Step.

param nConstant
constant value for single channel functions.

param pConstants
pointer to a list of constants, one per color channel for multi-channel image functions.

param pDst
Destination-Image Pointer.

param nDstStep
Destination-Image Line Step.

param oSizeROI
Region-Of-Interest (ROI).

param nEpsilon
epsilon tolerance value to compare to per color channel pixel absolute differences

param nppStreamCtx
Application Managed Stream Context.

return
Image Data Related Error Codes, ROI Related Error Codes


Functions


NppStatus nppiCompareEqualEpsC_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp32f nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp32f nEpsilon, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point image compare whether image and constant are equal within epsilon.
Compare pSrc’s pixels with constant value to determine whether they are equal within a difference of epsilon.
For common parameter descriptions, see Common parameters for nppiCompareEqualEpsC functions:.


NppStatus nppiCompareEqualEpsC_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp32f *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp32f nEpsilon, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point image compare whether image and constant are equal within epsilon.
Compare pSrc’s pixels with constant value to determine whether they are equal within a difference of epsilon.
For common parameter descriptions, see Common parameters for nppiCompareEqualEpsC functions:.


NppStatus nppiCompareEqualEpsC_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp32f *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp32f nEpsilon, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point image compare whether image and constant are equal within epsilon.
Compare pSrc’s pixels with constant value to determine whether they are equal within a difference of epsilon.
For common parameter descriptions, see Common parameters for nppiCompareEqualEpsC functions:.


NppStatus nppiCompareEqualEpsC_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp32f *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp32f nEpsilon, NppStreamContext nppStreamCtx)
4 channel 32-bit signed floating point compare whether image and constant are equal within epsilon, not affecting Alpha.
Compare pSrc’s pixels with constant value to determine whether they are equal within a difference of epsilon.
For common parameter descriptions, see Common parameters for nppiCompareEqualEpsC functions:.