# Signal Conversion Functions


Functions that provide conversion and threshold operations.


## Signal Convert


### Convert


The set of conversion operations available in the library


Convert


Routines for converting the sample-data type of signals.


NppStatus nppsConvert_8s16s_Ctx(const Npp8s *pSrc, Npp16s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit signed byte to 16-bit signed short conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_8s32f_Ctx(const Npp8s *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit signed byte to 32-bit floating point number conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_8u32f_Ctx(const Npp8u *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned byte to 32-bit floating point number conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_16s8s_Sfs_Ctx(const Npp16s *pSrc, Npp8s *pDst, Npp32u nLength, NppRoundMode eRoundMode, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short to 8-bit signed byte conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
eRoundMode – Rounding Mode Parameter.
nScaleFactor – nScaleFactor
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_16s32s_Ctx(const Npp16s *pSrc, Npp32s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short to 32-bit signed integer conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_16s32f_Ctx(const Npp16s *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short to 32-bit floating point number conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_16u32f_Ctx(const Npp16u *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short to 32-bit floating point number conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_32s16s_Ctx(const Npp32s *pSrc, Npp16s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed integer to 16-bit signed short conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_32s32f_Ctx(const Npp32s *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed integer to 32-bit floating point number conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_32s64f_Ctx(const Npp32s *pSrc, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed integer to 64-bit floating point number conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_32f64f_Ctx(const Npp32f *pSrc, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point number to 64-bit floating point number conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_64s64f_Ctx(const Npp64s *pSrc, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit signed integer to 64-bit floating point number conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_64f32f_Ctx(const Npp64f *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point number to 32-bit floating point number conversion

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_16s32f_Sfs_Ctx(const Npp16s *pSrc, Npp32f *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short to 32-bit floating point number conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_16s64f_Sfs_Ctx(const Npp16s *pSrc, Npp64f *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short to 64-bit floating point number conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_32s16s_Sfs_Ctx(const Npp32s *pSrc, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer to 16-bit signed short conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_32s32f_Sfs_Ctx(const Npp32s *pSrc, Npp32f *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer to 32-bit floating point number conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_32s64f_Sfs_Ctx(const Npp32s *pSrc, Npp64f *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer to 64-bit floating point number conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_32f8s_Sfs_Ctx(const Npp32f *pSrc, Npp8s *pDst, size_t nLength, NppRoundMode eRoundMode, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer to 8-bit signed byte conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
eRoundMode – Rounding Mode Parameter.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_32f8u_Sfs_Ctx(const Npp32f *pSrc, Npp8u *pDst, size_t nLength, NppRoundMode eRoundMode, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit floating point number to 8-bit unsigned byte conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
eRoundMode – Rounding Mode Parameter.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_32f16s_Sfs_Ctx(const Npp32f *pSrc, Npp16s *pDst, size_t nLength, NppRoundMode eRoundMode, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit floating point number to 16-bit signed short conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
eRoundMode – Rounding Mode Parameter.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_32f16u_Sfs_Ctx(const Npp32f *pSrc, Npp16u *pDst, size_t nLength, NppRoundMode eRoundMode, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit floating point number to 16-bit unsigned short conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
eRoundMode – Rounding Mode Parameter.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_32f32s_Sfs_Ctx(const Npp32f *pSrc, Npp32s *pDst, size_t nLength, NppRoundMode eRoundMode, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit floating point number to 32-bit signed integer conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
eRoundMode – Rounding Mode Parameter.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_64s32s_Sfs_Ctx(const Npp64s *pSrc, Npp32s *pDst, size_t nLength, NppRoundMode eRoundMode, int nScaleFactor, NppStreamContext nppStreamCtx)
64-bit signed integer to 32-bit signed integer conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
eRoundMode – Rounding Mode Parameter.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_64f16s_Sfs_Ctx(const Npp64f *pSrc, Npp16s *pDst, size_t nLength, NppRoundMode eRoundMode, int nScaleFactor, NppStreamContext nppStreamCtx)
64-bit floating point number to 16-bit signed short conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
eRoundMode – Rounding Mode Parameter.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_64f32s_Sfs_Ctx(const Npp64f *pSrc, Npp32s *pDst, size_t nLength, NppRoundMode eRoundMode, int nScaleFactor, NppStreamContext nppStreamCtx)
64-bit floating point number to 32-bit signed integer conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
eRoundMode – Rounding Mode Parameter.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsConvert_64f64s_Sfs_Ctx(const Npp64f *pSrc, Npp64s *pDst, size_t nLength, NppRoundMode eRoundMode, int nScaleFactor, NppStreamContext nppStreamCtx)
64-bit floating point number to 64-bit signed integer conversion with scaling

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
eRoundMode – Rounding Mode Parameter.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Threshold


### Threshold


The set of threshold operations available in the library.


Threshold Functions


Performs the threshold operation on the samples of a signal by limiting the sample values by a specified constant value.


NppStatus nppsThreshold_16s_Ctx(const Npp16s *pSrc, Npp16s *pDst, size_t nLength, Npp16s nLevel, NppCmpOp nRelOp, NppStreamContext nppStreamCtx)
16-bit signed short signal threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nRelOp – NppCmpOp type of thresholding operation (NPP_CMP_LESS or NPP_CMP_GREATER only).
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_16s_I_Ctx(Npp16s *pSrcDst, size_t nLength, Npp16s nLevel, NppCmpOp nRelOp, NppStreamContext nppStreamCtx)
16-bit in place signed short signal threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nRelOp – NppCmpOp type of thresholding operation (NPP_CMP_LESS or NPP_CMP_GREATER only).
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_16sc_Ctx(const Npp16sc *pSrc, Npp16sc *pDst, size_t nLength, Npp16s nLevel, NppCmpOp nRelOp, NppStreamContext nppStreamCtx)
16-bit signed short complex number signal threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nRelOp – NppCmpOp type of thresholding operation (NPP_CMP_LESS or NPP_CMP_GREATER only).
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_16sc_I_Ctx(Npp16sc *pSrcDst, size_t nLength, Npp16s nLevel, NppCmpOp nRelOp, NppStreamContext nppStreamCtx)
16-bit in place signed short complex number signal threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nRelOp – NppCmpOp type of thresholding operation (NPP_CMP_LESS or NPP_CMP_GREATER only).
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, Npp32f nLevel, NppCmpOp nRelOp, NppStreamContext nppStreamCtx)
32-bit floating point signal threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nRelOp – NppCmpOp type of thresholding operation (NPP_CMP_LESS or NPP_CMP_GREATER only).
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, Npp32f nLevel, NppCmpOp nRelOp, NppStreamContext nppStreamCtx)
32-bit in place floating point signal threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nRelOp – NppCmpOp type of thresholding operation (NPP_CMP_LESS or NPP_CMP_GREATER only).
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_32fc_Ctx(const Npp32fc *pSrc, Npp32fc *pDst, size_t nLength, Npp32f nLevel, NppCmpOp nRelOp, NppStreamContext nppStreamCtx)
32-bit floating point complex number signal threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nRelOp – NppCmpOp type of thresholding operation (NPP_CMP_LESS or NPP_CMP_GREATER only).
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_32fc_I_Ctx(Npp32fc *pSrcDst, size_t nLength, Npp32f nLevel, NppCmpOp nRelOp, NppStreamContext nppStreamCtx)
32-bit in place floating point complex number signal threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nRelOp – NppCmpOp type of thresholding operation (NPP_CMP_LESS or NPP_CMP_GREATER only).
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_64f_Ctx(const Npp64f *pSrc, Npp64f *pDst, size_t nLength, Npp64f nLevel, NppCmpOp nRelOp, NppStreamContext nppStreamCtx)
64-bit floating point signal threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nRelOp – NppCmpOp type of thresholding operation (NPP_CMP_LESS or NPP_CMP_GREATER only).
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_64f_I_Ctx(Npp64f *pSrcDst, size_t nLength, Npp64f nLevel, NppCmpOp nRelOp, NppStreamContext nppStreamCtx)
64-bit in place floating point signal threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nRelOp – NppCmpOp type of thresholding operation (NPP_CMP_LESS or NPP_CMP_GREATER only).
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_64fc_Ctx(const Npp64fc *pSrc, Npp64fc *pDst, size_t nLength, Npp64f nLevel, NppCmpOp nRelOp, NppStreamContext nppStreamCtx)
64-bit floating point complex number signal threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nRelOp – NppCmpOp type of thresholding operation (NPP_CMP_LESS or NPP_CMP_GREATER only).
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_64fc_I_Ctx(Npp64fc *pSrcDst, size_t nLength, Npp64f nLevel, NppCmpOp nRelOp, NppStreamContext nppStreamCtx)
64-bit in place floating point complex number signal threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nRelOp – NppCmpOp type of thresholding operation (NPP_CMP_LESS or NPP_CMP_GREATER only).
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LT_16s_Ctx(const Npp16s *pSrc, Npp16s *pDst, size_t nLength, Npp16s nLevel, NppStreamContext nppStreamCtx)
16-bit signed short signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LT_16s_I_Ctx(Npp16s *pSrcDst, size_t nLength, Npp16s nLevel, NppStreamContext nppStreamCtx)
16-bit in place signed short signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LT_16sc_Ctx(const Npp16sc *pSrc, Npp16sc *pDst, size_t nLength, Npp16s nLevel, NppStreamContext nppStreamCtx)
16-bit signed short complex number signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LT_16sc_I_Ctx(Npp16sc *pSrcDst, size_t nLength, Npp16s nLevel, NppStreamContext nppStreamCtx)
16-bit in place signed short complex number signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LT_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, Npp32f nLevel, NppStreamContext nppStreamCtx)
32-bit floating point signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LT_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, Npp32f nLevel, NppStreamContext nppStreamCtx)
32-bit in place floating point signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LT_32fc_Ctx(const Npp32fc *pSrc, Npp32fc *pDst, size_t nLength, Npp32f nLevel, NppStreamContext nppStreamCtx)
32-bit floating point complex number signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LT_32fc_I_Ctx(Npp32fc *pSrcDst, size_t nLength, Npp32f nLevel, NppStreamContext nppStreamCtx)
32-bit in place floating point complex number signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LT_64f_Ctx(const Npp64f *pSrc, Npp64f *pDst, size_t nLength, Npp64f nLevel, NppStreamContext nppStreamCtx)
64-bit floating point signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LT_64f_I_Ctx(Npp64f *pSrcDst, size_t nLength, Npp64f nLevel, NppStreamContext nppStreamCtx)
64-bit in place floating point signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LT_64fc_Ctx(const Npp64fc *pSrc, Npp64fc *pDst, size_t nLength, Npp64f nLevel, NppStreamContext nppStreamCtx)
64-bit floating point complex number signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LT_64fc_I_Ctx(Npp64fc *pSrcDst, size_t nLength, Npp64f nLevel, NppStreamContext nppStreamCtx)
64-bit in place floating point complex number signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GT_16s_Ctx(const Npp16s *pSrc, Npp16s *pDst, size_t nLength, Npp16s nLevel, NppStreamContext nppStreamCtx)
16-bit signed short signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GT_16s_I_Ctx(Npp16s *pSrcDst, size_t nLength, Npp16s nLevel, NppStreamContext nppStreamCtx)
16-bit in place signed short signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GT_16sc_Ctx(const Npp16sc *pSrc, Npp16sc *pDst, size_t nLength, Npp16s nLevel, NppStreamContext nppStreamCtx)
16-bit signed short complex number signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GT_16sc_I_Ctx(Npp16sc *pSrcDst, size_t nLength, Npp16s nLevel, NppStreamContext nppStreamCtx)
16-bit in place signed short complex number signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GT_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, Npp32f nLevel, NppStreamContext nppStreamCtx)
32-bit floating point signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GT_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, Npp32f nLevel, NppStreamContext nppStreamCtx)
32-bit in place floating point signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GT_32fc_Ctx(const Npp32fc *pSrc, Npp32fc *pDst, size_t nLength, Npp32f nLevel, NppStreamContext nppStreamCtx)
32-bit floating point complex number signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GT_32fc_I_Ctx(Npp32fc *pSrcDst, size_t nLength, Npp32f nLevel, NppStreamContext nppStreamCtx)
32-bit in place floating point complex number signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GT_64f_Ctx(const Npp64f *pSrc, Npp64f *pDst, size_t nLength, Npp64f nLevel, NppStreamContext nppStreamCtx)
64-bit floating point signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GT_64f_I_Ctx(Npp64f *pSrcDst, size_t nLength, Npp64f nLevel, NppStreamContext nppStreamCtx)
64-bit in place floating point signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GT_64fc_Ctx(const Npp64fc *pSrc, Npp64fc *pDst, size_t nLength, Npp64f nLevel, NppStreamContext nppStreamCtx)
64-bit floating point complex number signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GT_64fc_I_Ctx(Npp64fc *pSrcDst, size_t nLength, Npp64f nLevel, NppStreamContext nppStreamCtx)
64-bit in place floating point complex number signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LTVal_16s_Ctx(const Npp16s *pSrc, Npp16s *pDst, size_t nLength, Npp16s nLevel, Npp16s nValue, NppStreamContext nppStreamCtx)
16-bit signed short signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LTVal_16s_I_Ctx(Npp16s *pSrcDst, size_t nLength, Npp16s nLevel, Npp16s nValue, NppStreamContext nppStreamCtx)
16-bit in place signed short signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LTVal_16sc_Ctx(const Npp16sc *pSrc, Npp16sc *pDst, size_t nLength, Npp16s nLevel, Npp16sc nValue, NppStreamContext nppStreamCtx)
16-bit signed short complex number signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LTVal_16sc_I_Ctx(Npp16sc *pSrcDst, size_t nLength, Npp16s nLevel, Npp16sc nValue, NppStreamContext nppStreamCtx)
16-bit in place signed short complex number signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LTVal_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, Npp32f nLevel, Npp32f nValue, NppStreamContext nppStreamCtx)
32-bit floating point signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LTVal_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, Npp32f nLevel, Npp32f nValue, NppStreamContext nppStreamCtx)
32-bit in place floating point signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LTVal_32fc_Ctx(const Npp32fc *pSrc, Npp32fc *pDst, size_t nLength, Npp32f nLevel, Npp32fc nValue, NppStreamContext nppStreamCtx)
32-bit floating point complex number signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LTVal_32fc_I_Ctx(Npp32fc *pSrcDst, size_t nLength, Npp32f nLevel, Npp32fc nValue, NppStreamContext nppStreamCtx)
32-bit in place floating point complex number signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LTVal_64f_Ctx(const Npp64f *pSrc, Npp64f *pDst, size_t nLength, Npp64f nLevel, Npp64f nValue, NppStreamContext nppStreamCtx)
64-bit floating point signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LTVal_64f_I_Ctx(Npp64f *pSrcDst, size_t nLength, Npp64f nLevel, Npp64f nValue, NppStreamContext nppStreamCtx)
64-bit in place floating point signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LTVal_64fc_Ctx(const Npp64fc *pSrc, Npp64fc *pDst, size_t nLength, Npp64f nLevel, Npp64fc nValue, NppStreamContext nppStreamCtx)
64-bit floating point complex number signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_LTVal_64fc_I_Ctx(Npp64fc *pSrcDst, size_t nLength, Npp64f nLevel, Npp64fc nValue, NppStreamContext nppStreamCtx)
64-bit in place floating point complex number signal NPP_CMP_LESS threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GTVal_16s_Ctx(const Npp16s *pSrc, Npp16s *pDst, size_t nLength, Npp16s nLevel, Npp16s nValue, NppStreamContext nppStreamCtx)
16-bit signed short signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GTVal_16s_I_Ctx(Npp16s *pSrcDst, size_t nLength, Npp16s nLevel, Npp16s nValue, NppStreamContext nppStreamCtx)
16-bit in place signed short signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GTVal_16sc_Ctx(const Npp16sc *pSrc, Npp16sc *pDst, size_t nLength, Npp16s nLevel, Npp16sc nValue, NppStreamContext nppStreamCtx)
16-bit signed short complex number signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GTVal_16sc_I_Ctx(Npp16sc *pSrcDst, size_t nLength, Npp16s nLevel, Npp16sc nValue, NppStreamContext nppStreamCtx)
16-bit in place signed short complex number signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GTVal_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, Npp32f nLevel, Npp32f nValue, NppStreamContext nppStreamCtx)
32-bit floating point signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GTVal_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, Npp32f nLevel, Npp32f nValue, NppStreamContext nppStreamCtx)
32-bit in place floating point signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GTVal_32fc_Ctx(const Npp32fc *pSrc, Npp32fc *pDst, size_t nLength, Npp32f nLevel, Npp32fc nValue, NppStreamContext nppStreamCtx)
32-bit floating point complex number signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GTVal_32fc_I_Ctx(Npp32fc *pSrcDst, size_t nLength, Npp32f nLevel, Npp32fc nValue, NppStreamContext nppStreamCtx)
32-bit in place floating point complex number signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GTVal_64f_Ctx(const Npp64f *pSrc, Npp64f *pDst, size_t nLength, Npp64f nLevel, Npp64f nValue, NppStreamContext nppStreamCtx)
64-bit floating point signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GTVal_64f_I_Ctx(Npp64f *pSrcDst, size_t nLength, Npp64f nLevel, Npp64f nValue, NppStreamContext nppStreamCtx)
64-bit in place floating point signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GTVal_64fc_Ctx(const Npp64fc *pSrc, Npp64fc *pDst, size_t nLength, Npp64f nLevel, Npp64fc nValue, NppStreamContext nppStreamCtx)
64-bit floating point complex number signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsThreshold_GTVal_64fc_I_Ctx(Npp64fc *pSrcDst, size_t nLength, Npp64f nLevel, Npp64fc nValue, NppStreamContext nppStreamCtx)
64-bit in place floating point complex number signal NPP_CMP_GREATER threshold with constant level.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nLevel – Constant threshold value (real part only and must be greater than 0) to be used to limit each signal sample
nValue – Constant value to replace source value when threshold test is true.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.