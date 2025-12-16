# Signal Arithmetic And Logical Operations


Functions that provide common arithmetic and logical operations.


## Signal Arithmetic Functions


### Arithmetic Operations


The set of arithmetic operations for signal processing available in the library.


### Signal AddC


#### AddC


Adds a constant value to each sample of a signal.


Functions


NppStatus nppsAddC_8u_ISfs_Ctx(Npp8u nValue, Npp8u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal add constant, scale, then clamp to saturated value

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be added to each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_8u_Sfs_Ctx(const Npp8u *pSrc, Npp8u nValue, Npp8u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned charvector add constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be added to each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_16u_ISfs_Ctx(Npp16u nValue, Npp16u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal add constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be added to each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_16u_Sfs_Ctx(const Npp16u *pSrc, Npp16u nValue, Npp16u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short vector add constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be added to each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_16s_ISfs_Ctx(Npp16s nValue, Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short in place signal add constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be added to each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_16s_Sfs_Ctx(const Npp16s *pSrc, Npp16s nValue, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal add constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be added to each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_16sc_ISfs_Ctx(Npp16sc nValue, Npp16sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit integer complex number (16 bit real, 16 bit imaginary)signal add constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be added to each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_16sc_Sfs_Ctx(const Npp16sc *pSrc, Npp16sc nValue, Npp16sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit integer complex number (16 bit real, 16 bit imaginary) signal add constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be added to each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_32s_ISfs_Ctx(Npp32s nValue, Npp32s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer in place signal add constant and scale.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be added to each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_32s_Sfs_Ctx(const Npp32s *pSrc, Npp32s nValue, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integersignal add constant and scale.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be added to each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_32sc_ISfs_Ctx(Npp32sc nValue, Npp32sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit integer complex number (32 bit real, 32 bit imaginary) in place signal add constant and scale.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be added to each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_32sc_Sfs_Ctx(const Npp32sc *pSrc, Npp32sc nValue, Npp32sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit integer complex number (32 bit real, 32 bit imaginary) signal add constant and scale.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be added to each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_32f_I_Ctx(Npp32f nValue, Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point in place signal add constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be added to each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_32f_Ctx(const Npp32f *pSrc, Npp32f nValue, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal add constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be added to each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_32fc_I_Ctx(Npp32fc nValue, Npp32fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point complex number (32 bit real, 32 bit imaginary) in place signal add constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be added to each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_32fc_Ctx(const Npp32fc *pSrc, Npp32fc nValue, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point complex number (32 bit real, 32 bit imaginary) signal add constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be added to each vector element.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_64f_I_Ctx(Npp64f nValue, Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point, in place signal add constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be added to each vector element
nLength – Length of the vectors, number of items.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_64f_Ctx(const Npp64f *pSrc, Npp64f nValue, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating pointsignal add constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be added to each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_64fc_I_Ctx(Npp64fc nValue, Npp64fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point complex number (64 bit real, 64 bit imaginary) in place signal add constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be added to each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddC_64fc_Ctx(const Npp64fc *pSrc, Npp64fc nValue, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point complex number (64 bit real, 64 bit imaginary) signal add constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be added to each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal AddProductC


#### AddProductC


Adds product of a constant and each sample of a source signal to the each sample of destination signal.


Functions


NppStatus nppsAddProductC_32f_Ctx(const Npp32f *pSrc, Npp32f nValue, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal add product of signal times constant to destination signal.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal MulC


#### MulC


Multiplies each sample of a signal by a constant value.


Functions


NppStatus nppsMulC_8u_ISfs_Ctx(Npp8u nValue, Npp8u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal times constant, scale, then clamp to saturated value

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be multiplied by each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_8u_Sfs_Ctx(const Npp8u *pSrc, Npp8u nValue, Npp8u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char signal times constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_16u_ISfs_Ctx(Npp16u nValue, Npp16u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal times constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be multiplied by each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_16u_Sfs_Ctx(const Npp16u *pSrc, Npp16u nValue, Npp16u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal times constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_16s_ISfs_Ctx(Npp16s nValue, Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short in place signal times constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be multiplied by each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_16s_Sfs_Ctx(const Npp16s *pSrc, Npp16s nValue, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal times constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_16sc_ISfs_Ctx(Npp16sc nValue, Npp16sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit integer complex number (16 bit real, 16 bit imaginary)signal times constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be multiplied by each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_16sc_Sfs_Ctx(const Npp16sc *pSrc, Npp16sc nValue, Npp16sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit integer complex number (16 bit real, 16 bit imaginary)signal times constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_32s_ISfs_Ctx(Npp32s nValue, Npp32s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer in place signal times constant and scale.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be multiplied by each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_32s_Sfs_Ctx(const Npp32s *pSrc, Npp32s nValue, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal times constant and scale.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_32sc_ISfs_Ctx(Npp32sc nValue, Npp32sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit integer complex number (32 bit real, 32 bit imaginary) in place signal times constant and scale.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be multiplied by each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_32sc_Sfs_Ctx(const Npp32sc *pSrc, Npp32sc nValue, Npp32sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit integer complex number (32 bit real, 32 bit imaginary) signal times constant and scale.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_32f_I_Ctx(Npp32f nValue, Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point in place signal times constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be multiplied by each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_32f_Ctx(const Npp32f *pSrc, Npp32f nValue, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal times constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_Low_32f16s_Ctx(const Npp32f *pSrc, Npp32f nValue, Npp16s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal times constant with output converted to 16-bit signed integer.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_32f16s_Sfs_Ctx(const Npp32f *pSrc, Npp32f nValue, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit floating point signal times constant with output converted to 16-bit signed integer with scaling and saturation of output result.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nScaleFactor – Integer Result Scaling.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_32fc_I_Ctx(Npp32fc nValue, Npp32fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point complex number (32 bit real, 32 bit imaginary) in place signal times constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be multiplied by each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_32fc_Ctx(const Npp32fc *pSrc, Npp32fc nValue, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point complex number (32 bit real, 32 bit imaginary) signal times constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_64f_I_Ctx(Npp64f nValue, Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point, in place signal times constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be multiplied by each vector element
nLength – Length of the vectors, number of items.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_64f_Ctx(const Npp64f *pSrc, Npp64f nValue, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal times constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_64f64s_ISfs_Ctx(Npp64f nValue, Npp64s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
64-bit floating point signal times constant with in place conversion to 64-bit signed integer and with scaling and saturation of output result.

Parameters

nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_64fc_I_Ctx(Npp64fc nValue, Npp64fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point complex number (64 bit real, 64 bit imaginary) in place signal times constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be multiplied by each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMulC_64fc_Ctx(const Npp64fc *pSrc, Npp64fc nValue, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point complex number (64 bit real, 64 bit imaginary) signal times constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be multiplied by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal SubC


#### SubC


Subtracts a constant from each sample of a signal.


Functions


NppStatus nppsSubC_8u_ISfs_Ctx(Npp8u nValue, Npp8u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal subtract constant, scale, then clamp to saturated value

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be subtracted from each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_8u_Sfs_Ctx(const Npp8u *pSrc, Npp8u nValue, Npp8u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char signal subtract constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be subtracted from each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_16u_ISfs_Ctx(Npp16u nValue, Npp16u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal subtract constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be subtracted from each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_16u_Sfs_Ctx(const Npp16u *pSrc, Npp16u nValue, Npp16u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal subtract constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be subtracted from each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_16s_ISfs_Ctx(Npp16s nValue, Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short in place signal subtract constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be subtracted from each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_16s_Sfs_Ctx(const Npp16s *pSrc, Npp16s nValue, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal subtract constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be subtracted from each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_16sc_ISfs_Ctx(Npp16sc nValue, Npp16sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit integer complex number (16 bit real, 16 bit imaginary) signal subtract constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be subtracted from each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_16sc_Sfs_Ctx(const Npp16sc *pSrc, Npp16sc nValue, Npp16sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit integer complex number (16 bit real, 16 bit imaginary) signal subtract constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be subtracted from each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_32s_ISfs_Ctx(Npp32s nValue, Npp32s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer in place signal subtract constant and scale.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be subtracted from each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_32s_Sfs_Ctx(const Npp32s *pSrc, Npp32s nValue, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal subtract constant and scale.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be subtracted from each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_32sc_ISfs_Ctx(Npp32sc nValue, Npp32sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit integer complex number (32 bit real, 32 bit imaginary) in place signal subtract constant and scale.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be subtracted from each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_32sc_Sfs_Ctx(const Npp32sc *pSrc, Npp32sc nValue, Npp32sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit integer complex number (32 bit real, 32 bit imaginary)signal subtract constant and scale.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be subtracted from each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_32f_I_Ctx(Npp32f nValue, Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point in place signal subtract constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be subtracted from each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_32f_Ctx(const Npp32f *pSrc, Npp32f nValue, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal subtract constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be subtracted from each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_32fc_I_Ctx(Npp32fc nValue, Npp32fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point complex number (32 bit real, 32 bit imaginary) in place signal subtract constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be subtracted from each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_32fc_Ctx(const Npp32fc *pSrc, Npp32fc nValue, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point complex number (32 bit real, 32 bit imaginary) signal subtract constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be subtracted from each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_64f_I_Ctx(Npp64f nValue, Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point, in place signal subtract constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be subtracted from each vector element
nLength – Length of the vectors, number of items.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_64f_Ctx(const Npp64f *pSrc, Npp64f nValue, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal subtract constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be subtracted from each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_64fc_I_Ctx(Npp64fc nValue, Npp64fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point complex number (64 bit real, 64 bit imaginary) in place signal subtract constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be subtracted from each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubC_64fc_Ctx(const Npp64fc *pSrc, Npp64fc nValue, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point complex number (64 bit real, 64 bit imaginary) signal subtract constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be subtracted from each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal SubCRev


#### SubCRev


Subtracts each sample of a signal from a constant.


Functions


NppStatus nppsSubCRev_8u_ISfs_Ctx(Npp8u nValue, Npp8u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal subtract from constant, scale, then clamp to saturated value

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_8u_Sfs_Ctx(const Npp8u *pSrc, Npp8u nValue, Npp8u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char signal subtract from constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_16u_ISfs_Ctx(Npp16u nValue, Npp16u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal subtract from constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_16u_Sfs_Ctx(const Npp16u *pSrc, Npp16u nValue, Npp16u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal subtract from constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_16s_ISfs_Ctx(Npp16s nValue, Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short in place signal subtract from constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_16s_Sfs_Ctx(const Npp16s *pSrc, Npp16s nValue, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal subtract from constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_16sc_ISfs_Ctx(Npp16sc nValue, Npp16sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit integer complex number (16 bit real, 16 bit imaginary) signal subtract from constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_16sc_Sfs_Ctx(const Npp16sc *pSrc, Npp16sc nValue, Npp16sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit integer complex number (16 bit real, 16 bit imaginary) signal subtract from constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_32s_ISfs_Ctx(Npp32s nValue, Npp32s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer in place signal subtract from constant and scale.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_32s_Sfs_Ctx(const Npp32s *pSrc, Npp32s nValue, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integersignal subtract from constant and scale.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_32sc_ISfs_Ctx(Npp32sc nValue, Npp32sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit integer complex number (32 bit real, 32 bit imaginary) in place signal subtract from constant and scale.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_32sc_Sfs_Ctx(const Npp32sc *pSrc, Npp32sc nValue, Npp32sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit integer complex number (32 bit real, 32 bit imaginary) signal subtract from constant and scale.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_32f_I_Ctx(Npp32f nValue, Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point in place signal subtract from constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_32f_Ctx(const Npp32f *pSrc, Npp32f nValue, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal subtract from constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_32fc_I_Ctx(Npp32fc nValue, Npp32fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point complex number (32 bit real, 32 bit imaginary) in place signal subtract from constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_32fc_Ctx(const Npp32fc *pSrc, Npp32fc nValue, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point complex number (32 bit real, 32 bit imaginary) signal subtract from constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_64f_I_Ctx(Npp64f nValue, Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point, in place signal subtract from constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
nLength – Length of the vectors, number of items.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_64f_Ctx(const Npp64f *pSrc, Npp64f nValue, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal subtract from constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_64fc_I_Ctx(Npp64fc nValue, Npp64fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point complex number (64 bit real, 64 bit imaginary) in place signal subtract from constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSubCRev_64fc_Ctx(const Npp64fc *pSrc, Npp64fc nValue, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point complex number (64 bit real, 64 bit imaginary) signal subtract from constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value each vector element is to be subtracted from
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal DivC


#### DivC


Divides each sample of a signal by a constant.


Functions


NppStatus nppsDivC_8u_ISfs_Ctx(Npp8u nValue, Npp8u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal divided by constant, scale, then clamp to saturated value

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be divided into each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_8u_Sfs_Ctx(const Npp8u *pSrc, Npp8u nValue, Npp8u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char signal divided by constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be divided into each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_16u_ISfs_Ctx(Npp16u nValue, Npp16u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal divided by constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be divided into each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_16u_Sfs_Ctx(const Npp16u *pSrc, Npp16u nValue, Npp16u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal divided by constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be divided into each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_16s_ISfs_Ctx(Npp16s nValue, Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short in place signal divided by constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be divided into each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_16s_Sfs_Ctx(const Npp16s *pSrc, Npp16s nValue, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal divided by constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be divided into each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_16sc_ISfs_Ctx(Npp16sc nValue, Npp16sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit integer complex number (16 bit real, 16 bit imaginary)signal divided by constant, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be divided into each vector element
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_16sc_Sfs_Ctx(const Npp16sc *pSrc, Npp16sc nValue, Npp16sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit integer complex number (16 bit real, 16 bit imaginary) signal divided by constant, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be divided into each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_32f_I_Ctx(Npp32f nValue, Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point in place signal divided by constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be divided into each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_32f_Ctx(const Npp32f *pSrc, Npp32f nValue, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal divided by constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be divided into each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_32fc_I_Ctx(Npp32fc nValue, Npp32fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point complex number (32 bit real, 32 bit imaginary) in place signal divided by constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be divided into each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_32fc_Ctx(const Npp32fc *pSrc, Npp32fc nValue, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point complex number (32 bit real, 32 bit imaginary) signal divided by constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be divided into each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_64f_I_Ctx(Npp64f nValue, Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point in place signal divided by constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be divided into each vector element
nLength – Length of the vectors, number of items.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_64f_Ctx(const Npp64f *pSrc, Npp64f nValue, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal divided by constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be divided into each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_64fc_I_Ctx(Npp64fc nValue, Npp64fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point complex number (64 bit real, 64 bit imaginary) in place signal divided by constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be divided into each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivC_64fc_Ctx(const Npp64fc *pSrc, Npp64fc nValue, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point complex number (64 bit real, 64 bit imaginary) signal divided by constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be divided into each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal DivCRev


#### DivCRev


Divides a constant by each sample of a signal.


Functions


NppStatus nppsDivCRev_16u_I_Ctx(Npp16u nValue, Npp16u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short in place constant divided by signal, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be divided by each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivCRev_16u_Ctx(const Npp16u *pSrc, Npp16u nValue, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short signal divided by constant, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be divided by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivCRev_32f_I_Ctx(Npp32f nValue, Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point in place constant divided by signal.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be divided by each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDivCRev_32f_Ctx(const Npp32f *pSrc, Npp32f nValue, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point constant divided by signal.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be divided by each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Add


#### Add


Sample by sample addition of two signals.


Functions


NppStatus nppsAdd_16s_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp16s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short signal add signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be added to signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_16u_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short signal add signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be added to signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_32u_Ctx(const Npp32u *pSrc1, const Npp32u *pSrc2, Npp32u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned int signal add signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be added to signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal add signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be added to signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal add signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be added to signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_32fc_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point signal add signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be added to signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_64fc_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point signal add signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be added to signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_8u16u_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char signal add signal with 16-bit unsigned result, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be added to signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_16s32f_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short signal add signal with 32-bit floating point result, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be added to signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_8u_Sfs_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, Npp8u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char add signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be added to signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_16u_Sfs_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, Npp16u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short add signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be added to signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_16s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short add signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be added to signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_32s_Sfs_Ctx(const Npp32s *pSrc1, const Npp32s *pSrc2, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer add signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be added to signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_64s_Sfs_Ctx(const Npp64s *pSrc1, const Npp64s *pSrc2, Npp64s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
64-bit signed integer add signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be added to signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_16sc_Sfs_Ctx(const Npp16sc *pSrc1, const Npp16sc *pSrc2, Npp16sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed complex short add signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be added to signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_32sc_Sfs_Ctx(const Npp32sc *pSrc1, const Npp32sc *pSrc2, Npp32sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed complex integer add signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be added to signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_16s_I_Ctx(const Npp16s *pSrc, Npp16s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short in place signal add signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be added to signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_32f_I_Ctx(const Npp32f *pSrc, Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point in place signal add signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be added to signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_64f_I_Ctx(const Npp64f *pSrc, Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point in place signal add signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be added to signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_32fc_I_Ctx(const Npp32fc *pSrc, Npp32fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point in place signal add signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be added to signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_64fc_I_Ctx(const Npp64fc *pSrc, Npp64fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point in place signal add signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be added to signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_16s32s_I_Ctx(const Npp16s *pSrc, Npp32s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16/32-bit signed short in place signal add signal with 32-bit signed integer results, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be added to signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_8u_ISfs_Ctx(const Npp8u *pSrc, Npp8u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal add signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be added to signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_16u_ISfs_Ctx(const Npp16u *pSrc, Npp16u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal add signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be added to signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_16s_ISfs_Ctx(const Npp16s *pSrc, Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short in place signal add signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be added to signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_32s_ISfs_Ctx(const Npp32s *pSrc, Npp32s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer in place signal add signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be added to signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_16sc_ISfs_Ctx(const Npp16sc *pSrc, Npp16sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit complex signed short in place signal add signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be added to signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAdd_32sc_ISfs_Ctx(const Npp32sc *pSrc, Npp32sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit complex signed integer in place signal add signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be added to signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal AddProduct


#### AddProduct


Adds sample by sample product of two signals to the destination signal.


Functions


NppStatus nppsAddProduct_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal add product of source signal times destination signal to destination signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
pDst – Destination Signal Pointer. product of source1 and source2 signal elements to be added to destination elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddProduct_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal add product of source signal times destination signal to destination signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
pDst – Destination Signal Pointer. product of source1 and source2 signal elements to be added to destination elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddProduct_32fc_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point signal add product of source signal times destination signal to destination signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
pDst – Destination Signal Pointer. product of source1 and source2 signal elements to be added to destination elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddProduct_64fc_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point signal add product of source signal times destination signal to destination signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
pDst – Destination Signal Pointer. product of source1 and source2 signal elements to be added to destination elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddProduct_16s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal add product of source signal1 times source signal2 to destination signal, with scaling, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
pDst – Destination Signal Pointer. product of source1 and source2 signal elements to be added to destination elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddProduct_32s_Sfs_Ctx(const Npp32s *pSrc1, const Npp32s *pSrc2, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed short signal add product of source signal1 times source signal2 to destination signal, with scaling, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
pDst – Destination Signal Pointer. product of source1 and source2 signal elements to be added to destination elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAddProduct_16s32s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal add product of source signal1 times source signal2 to 32-bit signed integer destination signal, with scaling, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
pDst – Destination Signal Pointer. product of source1 and source2 signal elements to be added to destination elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Mul


#### Mul


Sample by sample multiplication the samples of two signals.


Functions


NppStatus nppsMul_16s_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp16s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short signal times signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be multiplied by signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal times signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be multiplied by signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal times signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be multiplied by signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_32fc_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point signal times signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be multiplied by signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_64fc_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point signal times signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be multiplied by signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_8u16u_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char signal times signal with 16-bit unsigned result, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be multiplied by signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_16s32f_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short signal times signal with 32-bit floating point result, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be multiplied by signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_32f32fc_Ctx(const Npp32f *pSrc1, const Npp32fc *pSrc2, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal times 32-bit complex floating point signal with complex 32-bit floating point result, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be multiplied by signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_8u_Sfs_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, Npp8u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char signal times signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be multiplied by signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_16u_Sfs_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, Npp16u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal time signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be multiplied by signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_16s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal times signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be multiplied by signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_32s_Sfs_Ctx(const Npp32s *pSrc1, const Npp32s *pSrc2, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal times signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be multiplied by signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_16sc_Sfs_Ctx(const Npp16sc *pSrc1, const Npp16sc *pSrc2, Npp16sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed complex short signal times signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be multiplied by signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_32sc_Sfs_Ctx(const Npp32sc *pSrc1, const Npp32sc *pSrc2, Npp32sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed complex integer signal times signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be multiplied by signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_16u16s_Sfs_Ctx(const Npp16u *pSrc1, const Npp16s *pSrc2, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal times 16-bit signed short signal, scale, then clamp to 16-bit signed saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be multiplied by signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_16s32s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal times signal, scale, then clamp to 32-bit signed saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be multiplied by signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_32s32sc_Sfs_Ctx(const Npp32s *pSrc1, const Npp32sc *pSrc2, Npp32sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal times 32-bit complex signed integer signal, scale, then clamp to 32-bit complex integer saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be multiplied by signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_Low_32s_Sfs_Ctx(const Npp32s *pSrc1, const Npp32s *pSrc2, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal times signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal2 elements to be multiplied by signal1 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_16s_I_Ctx(const Npp16s *pSrc, Npp16s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short in place signal times signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_32f_I_Ctx(const Npp32f *pSrc, Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point in place signal times signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_64f_I_Ctx(const Npp64f *pSrc, Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point in place signal times signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_32fc_I_Ctx(const Npp32fc *pSrc, Npp32fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point in place signal times signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_64fc_I_Ctx(const Npp64fc *pSrc, Npp64fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point in place signal times signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_32f32fc_I_Ctx(const Npp32f *pSrc, Npp32fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point in place signal times 32-bit floating point signal, then clamp to 32-bit complex floating point saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_8u_ISfs_Ctx(const Npp8u *pSrc, Npp8u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal times signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_16u_ISfs_Ctx(const Npp16u *pSrc, Npp16u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal times signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_16s_ISfs_Ctx(const Npp16s *pSrc, Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short in place signal times signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_32s_ISfs_Ctx(const Npp32s *pSrc, Npp32s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer in place signal times signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_16sc_ISfs_Ctx(const Npp16sc *pSrc, Npp16sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit complex signed short in place signal times signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_32sc_ISfs_Ctx(const Npp32sc *pSrc, Npp32sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit complex signed integer in place signal times signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMul_32s32sc_ISfs_Ctx(const Npp32s *pSrc, Npp32sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit complex signed integer in place signal times 32-bit signed integer signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be multiplied by signal1 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Sub


#### Sub


Sample by sample subtraction of the samples of two signals.


Functions


NppStatus nppsSub_16s_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp16s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short signal subtract signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal1 elements to be subtracted from signal2 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal subtract signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal1 elements to be subtracted from signal2 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal subtract signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal1 elements to be subtracted from signal2 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_32fc_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point signal subtract signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal1 elements to be subtracted from signal2 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_64fc_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point signal subtract signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal1 elements to be subtracted from signal2 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_16s32f_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short signal subtract 16-bit signed short signal, then clamp and convert to 32-bit floating point saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal1 elements to be subtracted from signal2 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_8u_Sfs_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, Npp8u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char signal subtract signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 elements to be subtracted from signal2 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_16u_Sfs_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, Npp16u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal subtract signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 elements to be subtracted from signal2 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_16s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal subtract signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 elements to be subtracted from signal2 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_32s_Sfs_Ctx(const Npp32s *pSrc1, const Npp32s *pSrc2, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal subtract signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 elements to be subtracted from signal2 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_16sc_Sfs_Ctx(const Npp16sc *pSrc1, const Npp16sc *pSrc2, Npp16sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed complex short signal subtract signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 elements to be subtracted from signal2 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_32sc_Sfs_Ctx(const Npp32sc *pSrc1, const Npp32sc *pSrc2, Npp32sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed complex integer signal subtract signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 elements to be subtracted from signal2 elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_16s_I_Ctx(const Npp16s *pSrc, Npp16s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short in place signal subtract signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 elements to be subtracted from signal2 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_32f_I_Ctx(const Npp32f *pSrc, Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point in place signal subtract signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 elements to be subtracted from signal2 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_64f_I_Ctx(const Npp64f *pSrc, Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point in place signal subtract signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 elements to be subtracted from signal2 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_32fc_I_Ctx(const Npp32fc *pSrc, Npp32fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point in place signal subtract signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 elements to be subtracted from signal2 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_64fc_I_Ctx(const Npp64fc *pSrc, Npp64fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point in place signal subtract signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 elements to be subtracted from signal2 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_8u_ISfs_Ctx(const Npp8u *pSrc, Npp8u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal subtract signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 elements to be subtracted from signal2 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_16u_ISfs_Ctx(const Npp16u *pSrc, Npp16u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal subtract signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 elements to be subtracted from signal2 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_16s_ISfs_Ctx(const Npp16s *pSrc, Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short in place signal subtract signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 elements to be subtracted from signal2 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_32s_ISfs_Ctx(const Npp32s *pSrc, Npp32s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer in place signal subtract signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 elements to be subtracted from signal2 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_16sc_ISfs_Ctx(const Npp16sc *pSrc, Npp16sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit complex signed short in place signal subtract signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 elements to be subtracted from signal2 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSub_32sc_ISfs_Ctx(const Npp32sc *pSrc, Npp32sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit complex signed integer in place signal subtract signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 elements to be subtracted from signal2 elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Div


#### Div


Sample by sample division of the samples of two signals.


Functions


NppStatus nppsDiv_8u_Sfs_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, Npp8u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char signal divide signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_16u_Sfs_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, Npp16u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal divide signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_16s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal divide signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_32s_Sfs_Ctx(const Npp32s *pSrc1, const Npp32s *pSrc2, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal divide signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_16sc_Sfs_Ctx(const Npp16sc *pSrc1, const Npp16sc *pSrc2, Npp16sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed complex short signal divide signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_32s16s_Sfs_Ctx(const Npp16s *pSrc1, const Npp32s *pSrc2, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal divided by 16-bit signed short signal, scale, then clamp to 16-bit signed short saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal divide signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal divide signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_32fc_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point signal divide signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_64fc_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point signal divide signal, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_8u_ISfs_Ctx(const Npp8u *pSrc, Npp8u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal divide signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 divisor elements to be divided into signal2 dividend elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_16u_ISfs_Ctx(const Npp16u *pSrc, Npp16u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal divide signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 divisor elements to be divided into signal2 dividend elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_16s_ISfs_Ctx(const Npp16s *pSrc, Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short in place signal divide signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 divisor elements to be divided into signal2 dividend elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_16sc_ISfs_Ctx(const Npp16sc *pSrc, Npp16sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit complex signed short in place signal divide signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 divisor elements to be divided into signal2 dividend elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_32s_ISfs_Ctx(const Npp32s *pSrc, Npp32s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer in place signal divide signal, with scaling, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 divisor elements to be divided into signal2 dividend elements
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_32f_I_Ctx(const Npp32f *pSrc, Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point in place signal divide signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 divisor elements to be divided into signal2 dividend elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_64f_I_Ctx(const Npp64f *pSrc, Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point in place signal divide signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 divisor elements to be divided into signal2 dividend elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_32fc_I_Ctx(const Npp32fc *pSrc, Npp32fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point in place signal divide signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 divisor elements to be divided into signal2 dividend elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_64fc_I_Ctx(const Npp64fc *pSrc, Npp64fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point in place signal divide signal, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 divisor elements to be divided into signal2 dividend elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Div Round


#### Div_Round


Sample by sample division of the samples of two signals with rounding.


Functions


NppStatus nppsDiv_Round_8u_Sfs_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, Npp8u *pDst, size_t nLength, NppRoundMode nRndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char signal divide signal, scale, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nRndMode – various rounding modes.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_Round_16u_Sfs_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, Npp16u *pDst, size_t nLength, NppRoundMode nRndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal divide signal, scale, round, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nRndMode – various rounding modes.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_Round_16s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, Npp16s *pDst, size_t nLength, NppRoundMode nRndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal divide signal, scale, round, then clamp to saturated value.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer, signal1 divisor elements to be divided into signal2 dividend elements.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nRndMode – various rounding modes.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_Round_8u_ISfs_Ctx(const Npp8u *pSrc, Npp8u *pSrcDst, size_t nLength, NppRoundMode nRndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal divide signal, with scaling, rounding then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 divisor elements to be divided into signal2 dividend elements
nLength – Signal Length.
nRndMode – various rounding modes.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_Round_16u_ISfs_Ctx(const Npp16u *pSrc, Npp16u *pSrcDst, size_t nLength, NppRoundMode nRndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal divide signal, with scaling, rounding then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 divisor elements to be divided into signal2 dividend elements
nLength – Signal Length.
nRndMode – various rounding modes.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDiv_Round_16s_ISfs_Ctx(const Npp16s *pSrc, Npp16s *pSrcDst, size_t nLength, NppRoundMode nRndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short in place signal divide signal, with scaling, rounding then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal1 divisor elements to be divided into signal2 dividend elements
nLength – Signal Length.
nRndMode – various rounding modes.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Abs


#### Abs


Absolute value of each sample of a signal.


Functions


NppStatus nppsAbs_16s_Ctx(const Npp16s *pSrc, Npp16s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short signal absolute value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAbs_32s_Ctx(const Npp32s *pSrc, Npp32s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed integer signal absolute value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAbs_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal absolute value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAbs_64f_Ctx(const Npp64f *pSrc, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal absolute value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAbs_16s_I_Ctx(Npp16s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short signal absolute value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAbs_32s_I_Ctx(Npp32s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed integer signal absolute value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAbs_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal absolute value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAbs_64f_I_Ctx(Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal absolute value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Square


#### Sqr


Squares each sample of a signal.


Functions


NppStatus nppsSqr_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal squared.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_64f_Ctx(const Npp64f *pSrc, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal squared.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_32fc_Ctx(const Npp32fc *pSrc, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point signal squared.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_64fc_Ctx(const Npp64fc *pSrc, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point signal squared.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal squared.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_64f_I_Ctx(Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal squared.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_32fc_I_Ctx(Npp32fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point signal squared.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_64fc_I_Ctx(Npp64fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point signal squared.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_8u_Sfs_Ctx(const Npp8u *pSrc, Npp8u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char signal squared, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_16u_Sfs_Ctx(const Npp16u *pSrc, Npp16u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal squared, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_16s_Sfs_Ctx(const Npp16s *pSrc, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal squared, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_16sc_Sfs_Ctx(const Npp16sc *pSrc, Npp16sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit complex signed short signal squared, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_8u_ISfs_Ctx(Npp8u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char signal squared, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_16u_ISfs_Ctx(Npp16u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal squared, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_16s_ISfs_Ctx(Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal squared, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqr_16sc_ISfs_Ctx(Npp16sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit complex signed short signal squared, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Square Root


#### Sqrt


Square root of each sample of a signal.


Functions


NppStatus nppsSqrt_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal square root.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_64f_Ctx(const Npp64f *pSrc, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal square root.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_32fc_Ctx(const Npp32fc *pSrc, Npp32fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point signal square root.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_64fc_Ctx(const Npp64fc *pSrc, Npp64fc *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point signal square root.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal square root.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_64f_I_Ctx(Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal square root.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_32fc_I_Ctx(Npp32fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit complex floating point signal square root.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_64fc_I_Ctx(Npp64fc *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit complex floating point signal square root.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_8u_Sfs_Ctx(const Npp8u *pSrc, Npp8u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char signal square root, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_16u_Sfs_Ctx(const Npp16u *pSrc, Npp16u *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal square root, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_16s_Sfs_Ctx(const Npp16s *pSrc, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal square root, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_16sc_Sfs_Ctx(const Npp16sc *pSrc, Npp16sc *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit complex signed short signal square root, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_64s_Sfs_Ctx(const Npp64s *pSrc, Npp64s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
64-bit signed integer signal square root, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_32s16s_Sfs_Ctx(const Npp32s *pSrc, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal square root, scale, then clamp to 16-bit signed integer saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_64s16s_Sfs_Ctx(const Npp64s *pSrc, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
64-bit signed integer signal square root, scale, then clamp to 16-bit signed integer saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_8u_ISfs_Ctx(Npp8u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
8-bit unsigned char signal square root, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_16u_ISfs_Ctx(Npp16u *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit unsigned short signal square root, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_16s_ISfs_Ctx(Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal square root, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_16sc_ISfs_Ctx(Npp16sc *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit complex signed short signal square root, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSqrt_64s_ISfs_Ctx(Npp64s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
64-bit signed integer signal square root, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Cube Root


#### Cubrt


Cube root of each sample of a signal.


Functions


NppStatus nppsCubrt_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal cube root.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsCubrt_32s16s_Sfs_Ctx(const Npp32s *pSrc, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal cube root, scale, then clamp to 16-bit signed integer saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Exp


#### Exp


E raised to the power of each sample of a signal.


Functions


NppStatus nppsExp_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal exponent.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsExp_64f_Ctx(const Npp64f *pSrc, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal exponent.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsExp_32f64f_Ctx(const Npp32f *pSrc, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal exponent with 64-bit floating point result.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsExp_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal exponent.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsExp_64f_I_Ctx(Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal exponent.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsExp_16s_Sfs_Ctx(const Npp16s *pSrc, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal exponent, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsExp_32s_Sfs_Ctx(const Npp32s *pSrc, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal exponent, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsExp_64s_Sfs_Ctx(const Npp64s *pSrc, Npp64s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
64-bit signed integer signal exponent, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsExp_16s_ISfs_Ctx(Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal exponent, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsExp_32s_ISfs_Ctx(Npp32s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal exponent, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsExp_64s_ISfs_Ctx(Npp64s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
64-bit signed integer signal exponent, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Ln


#### Ln


Natural logarithm of each sample of a signal.


Functions


NppStatus nppsLn_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal natural logarithm.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLn_64f_Ctx(const Npp64f *pSrc, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal natural logarithm.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLn_64f32f_Ctx(const Npp64f *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal natural logarithm with 32-bit floating point result.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLn_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal natural logarithm.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLn_64f_I_Ctx(Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal natural logarithm.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLn_16s_Sfs_Ctx(const Npp16s *pSrc, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal natural logarithm, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLn_32s_Sfs_Ctx(const Npp32s *pSrc, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal natural logarithm, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLn_32s16s_Sfs_Ctx(const Npp32s *pSrc, Npp16s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal natural logarithm, scale, then clamp to 16-bit signed short saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLn_16s_ISfs_Ctx(Npp16s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal natural logarithm, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLn_32s_ISfs_Ctx(Npp32s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal natural logarithm, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal 10Log10


#### 10Log10


Ten times the decimal logarithm of each sample of a signal.


Functions


NppStatus npps10Log10_32s_Sfs_Ctx(const Npp32s *pSrc, Npp32s *pDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal 10 times base 10 logarithm, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus npps10Log10_32s_ISfs_Ctx(Npp32s *pSrcDst, size_t nLength, int nScaleFactor, NppStreamContext nppStreamCtx)
32-bit signed integer signal 10 times base 10 logarithm, scale, then clamp to saturated value.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal SumLn


#### SumLn


Sums up the natural logarithm of each sample of a signal.


Functions


NppStatus nppsSumLnGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for 32f SumLn.
This primitive provides the correct buffer size for nppsSumLn_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSumLn_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit floating point signal sum natural logarithm.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSumLnGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for 64f SumLn.
This primitive provides the correct buffer size for nppsSumLn_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSumLn_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit floating point signal sum natural logarithm.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSumLnGetBufferSize_32f64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for 32f64f SumLn.
This primitive provides the correct buffer size for nppsSumLn_32f64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSumLn_32f64f_Ctx(const Npp32f *pSrc, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit flaoting point input, 64-bit floating point output signal sum natural logarithm.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSumLnGetBufferSize_16s32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for 16s32f SumLn.
This primitive provides the correct buffer size for nppsSumLn_16s32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSumLn_16s32f_Ctx(const Npp16s *pSrc, size_t nLength, Npp32f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer input, 32-bit floating point output signal sum natural logarithm.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal ArcTan


#### Arctan


Inverse tangent of each sample of a signal.


Functions


NppStatus nppsArctan_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal inverse tangent.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsArctan_64f_Ctx(const Npp64f *pSrc, Npp64f *pDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal inverse tangent.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsArctan_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point signal inverse tangent.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsArctan_64f_I_Ctx(Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point signal inverse tangent.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Normalize


#### Normalize


Normalize each sample of a real or complex signal using offset and division operations.


Functions


NppStatus nppsNormalize_32f_Ctx(const Npp32f *pSrc, Npp32f *pDst, size_t nLength, Npp32f vSub, Npp32f vDiv, NppStreamContext nppStreamCtx)
32-bit floating point signal normalize.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
vSub – value subtracted from each signal element before division
vDiv – divisor of post-subtracted signal element dividend
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormalize_32fc_Ctx(const Npp32fc *pSrc, Npp32fc *pDst, size_t nLength, Npp32fc vSub, Npp32f vDiv, NppStreamContext nppStreamCtx)
32-bit complex floating point signal normalize.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
vSub – value subtracted from each signal element before division
vDiv – divisor of post-subtracted signal element dividend
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormalize_64f_Ctx(const Npp64f *pSrc, Npp64f *pDst, size_t nLength, Npp64f vSub, Npp64f vDiv, NppStreamContext nppStreamCtx)
64-bit floating point signal normalize.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
vSub – value subtracted from each signal element before division
vDiv – divisor of post-subtracted signal element dividend
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormalize_64fc_Ctx(const Npp64fc *pSrc, Npp64fc *pDst, size_t nLength, Npp64fc vSub, Npp64f vDiv, NppStreamContext nppStreamCtx)
64-bit complex floating point signal normalize.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
vSub – value subtracted from each signal element before division
vDiv – divisor of post-subtracted signal element dividend
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormalize_16s_Sfs_Ctx(const Npp16s *pSrc, Npp16s *pDst, size_t nLength, Npp16s vSub, int vDiv, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit signed short signal normalize, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
vSub – value subtracted from each signal element before division
vDiv – divisor of post-subtracted signal element dividend
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormalize_16sc_Sfs_Ctx(const Npp16sc *pSrc, Npp16sc *pDst, size_t nLength, Npp16sc vSub, int vDiv, int nScaleFactor, NppStreamContext nppStreamCtx)
16-bit complex signed short signal normalize, scale, then clamp to saturated value.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
vSub – value subtracted from each signal element before division
vDiv – divisor of post-subtracted signal element dividend
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Cauchy, CouchyD, And CouchyDD2


#### Cauchy, CauchyD, and CauchyDD2


Determine Cauchy robust error function and its first and second derivatives for each sample of a signal.


Functions


NppStatus nppsCauchy_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, Npp32f nParam, NppStreamContext nppStreamCtx)
32-bit floating point signal Cauchy error calculation.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nParam – constant used in Cauchy formula
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsCauchyD_32f_I_Ctx(Npp32f *pSrcDst, size_t nLength, Npp32f nParam, NppStreamContext nppStreamCtx)
32-bit floating point signal Cauchy first derivative.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nParam – constant used in Cauchy formula
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsCauchyDD2_32f_I_Ctx(Npp32f *pSrcDst, Npp32f *pD2FVal, size_t nLength, Npp32f nParam, NppStreamContext nppStreamCtx)
32-bit floating point signal Cauchy first and second derivatives.

Parameters

pSrcDst – In-Place Signal Pointer.
pD2FVal – Source Signal Pointer. This signal contains the second derivative of the source signal.
nLength – Signal Length.
nParam – constant used in Cauchy formula
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Logical And Shift Operations


### Logical And Shift Operations


The set of logical and shift operations for signal processing available in the library.


### Signal AndC


#### AndC


Bitwise AND of a constant and each sample of a signal.


Functions


NppStatus nppsAndC_8u_Ctx(const Npp8u *pSrc, Npp8u nValue, Npp8u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char signal and with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be anded with each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAndC_16u_Ctx(const Npp16u *pSrc, Npp16u nValue, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short signal and with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be anded with each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAndC_32u_Ctx(const Npp32u *pSrc, Npp32u nValue, Npp32u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer signal and with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be anded with each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAndC_8u_I_Ctx(Npp8u nValue, Npp8u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal and with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be anded with each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAndC_16u_I_Ctx(Npp16u nValue, Npp16u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal and with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be anded with each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAndC_32u_I_Ctx(Npp32u nValue, Npp32u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned signed integer in place signal and with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be anded with each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal And


#### And


Sample by sample bitwise AND of samples from two signals.


Functions


NppStatus nppsAnd_8u_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, Npp8u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char signal and with signal.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be anded with signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAnd_16u_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short signal and with signal.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be anded with signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAnd_32u_Ctx(const Npp32u *pSrc1, const Npp32u *pSrc2, Npp32u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer signal and with signal.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be anded with signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAnd_8u_I_Ctx(const Npp8u *pSrc, Npp8u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal and with signal.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be anded with signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAnd_16u_I_Ctx(const Npp16u *pSrc, Npp16u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal and with signal.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be anded with signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAnd_32u_I_Ctx(const Npp32u *pSrc, Npp32u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer in place signal and with signal.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be anded with signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal OrC


#### OrC


Bitwise OR of a constant and each sample of a signal.


Functions


NppStatus nppsOrC_8u_Ctx(const Npp8u *pSrc, Npp8u nValue, Npp8u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char signal or with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be ored with each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsOrC_16u_Ctx(const Npp16u *pSrc, Npp16u nValue, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short signal or with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be ored with each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsOrC_32u_Ctx(const Npp32u *pSrc, Npp32u nValue, Npp32u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer signal or with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be ored with each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsOrC_8u_I_Ctx(Npp8u nValue, Npp8u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal or with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be ored with each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsOrC_16u_I_Ctx(Npp16u nValue, Npp16u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal or with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be ored with each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsOrC_32u_I_Ctx(Npp32u nValue, Npp32u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned signed integer in place signal or with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be ored with each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Or


#### Or


Sample by sample bitwise OR of the samples from two signals.


Functions


NppStatus nppsOr_8u_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, Npp8u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char signal or with signal.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be ored with signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsOr_16u_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short signal or with signal.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be ored with signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsOr_32u_Ctx(const Npp32u *pSrc1, const Npp32u *pSrc2, Npp32u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer signal or with signal.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be ored with signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsOr_8u_I_Ctx(const Npp8u *pSrc, Npp8u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal or with signal.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be ored with signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsOr_16u_I_Ctx(const Npp16u *pSrc, Npp16u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal or with signal.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be ored with signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsOr_32u_I_Ctx(const Npp32u *pSrc, Npp32u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer in place signal or with signal.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be ored with signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal XorC


#### XorC


Bitwise XOR of a constant and each sample of a signal.


Functions


NppStatus nppsXorC_8u_Ctx(const Npp8u *pSrc, Npp8u nValue, Npp8u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char signal exclusive or with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be exclusive ored with each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsXorC_16u_Ctx(const Npp16u *pSrc, Npp16u nValue, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short signal exclusive or with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be exclusive ored with each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsXorC_32u_Ctx(const Npp32u *pSrc, Npp32u nValue, Npp32u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer signal exclusive or with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be exclusive ored with each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsXorC_8u_I_Ctx(Npp8u nValue, Npp8u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal exclusive or with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be exclusive ored with each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsXorC_16u_I_Ctx(Npp16u nValue, Npp16u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal exclusive or with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be exclusive ored with each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsXorC_32u_I_Ctx(Npp32u nValue, Npp32u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned signed integer in place signal exclusive or with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be exclusive ored with each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Xor


#### Xor


Sample by sample bitwise XOR of the samples from two signals.


Functions


NppStatus nppsXor_8u_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, Npp8u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char signal exclusive or with signal.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be exclusive ored with signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsXor_16u_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short signal exclusive or with signal.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be exclusive ored with signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsXor_32u_Ctx(const Npp32u *pSrc1, const Npp32u *pSrc2, Npp32u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer signal exclusive or with signal.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer. signal2 elements to be exclusive ored with signal1 elements
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsXor_8u_I_Ctx(const Npp8u *pSrc, Npp8u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal exclusive or with signal.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be exclusive ored with signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsXor_16u_I_Ctx(const Npp16u *pSrc, Npp16u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal exclusive or with signal.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be exclusive ored with signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsXor_32u_I_Ctx(const Npp32u *pSrc, Npp32u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer in place signal exclusive or with signal.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer. signal2 elements to be exclusive ored with signal1 elements
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Not


#### Not


Bitwise NOT of each sample of a signal.


Functions


NppStatus nppsNot_8u_Ctx(const Npp8u *pSrc, Npp8u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char not signal.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNot_16u_Ctx(const Npp16u *pSrc, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short not signal.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNot_32u_Ctx(const Npp32u *pSrc, Npp32u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer not signal.

Parameters

pSrc – Source Signal Pointer.
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNot_8u_I_Ctx(Npp8u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char in place not signal.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNot_16u_I_Ctx(Npp16u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short in place not signal.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNot_32u_I_Ctx(Npp32u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned signed integer in place not signal.

Parameters

pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal LShiftC


#### LShiftC


Left shifts the bits of each sample of a signal by a constant amount.


Functions


NppStatus nppsLShiftC_8u_Ctx(const Npp8u *pSrc, int nValue, Npp8u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char signal left shift with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be used to left shift each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLShiftC_16u_Ctx(const Npp16u *pSrc, int nValue, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short signal left shift with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be used to left shift each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLShiftC_16s_Ctx(const Npp16s *pSrc, int nValue, Npp16s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short signal left shift with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be used to left shift each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLShiftC_32u_Ctx(const Npp32u *pSrc, int nValue, Npp32u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer signal left shift with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be used to left shift each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLShiftC_32s_Ctx(const Npp32s *pSrc, int nValue, Npp32s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed integer signal left shift with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be used to left shift each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLShiftC_8u_I_Ctx(int nValue, Npp8u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal left shift with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be used to left shift each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLShiftC_16u_I_Ctx(int nValue, Npp16u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal left shift with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be used to left shift each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLShiftC_16s_I_Ctx(int nValue, Npp16s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short in place signal left shift with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be used to left shift each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLShiftC_32u_I_Ctx(int nValue, Npp32u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned signed integer in place signal left shift with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be used to left shift each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsLShiftC_32s_I_Ctx(int nValue, Npp32s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed signed integer in place signal left shift with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be used to left shift each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal RShiftC


#### RShiftC


Right shifts the bits of each sample of a signal by a constant amount.


Functions


NppStatus nppsRShiftC_8u_Ctx(const Npp8u *pSrc, int nValue, Npp8u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char signal right shift with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be used to right shift each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsRShiftC_16u_Ctx(const Npp16u *pSrc, int nValue, Npp16u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short signal right shift with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be used to right shift each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsRShiftC_16s_Ctx(const Npp16s *pSrc, int nValue, Npp16s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short signal right shift with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be used to right shift each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsRShiftC_32u_Ctx(const Npp32u *pSrc, int nValue, Npp32u *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned integer signal right shift with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be used to right shift each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsRShiftC_32s_Ctx(const Npp32s *pSrc, int nValue, Npp32s *pDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed integer signal right shift with constant.

Parameters

pSrc – Source Signal Pointer.
nValue – Constant value to be used to right shift each vector element
pDst – Destination Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsRShiftC_8u_I_Ctx(int nValue, Npp8u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit unsigned char in place signal right shift with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be used to right shift each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsRShiftC_16u_I_Ctx(int nValue, Npp16u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short in place signal right shift with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be used to right shift each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsRShiftC_16s_I_Ctx(int nValue, Npp16s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short in place signal right shift with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be used to right shift each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsRShiftC_32u_I_Ctx(int nValue, Npp32u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit unsigned signed integer in place signal right shift with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be used to right shift each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsRShiftC_32s_I_Ctx(int nValue, Npp32s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed signed integer in place signal right shift with constant.

Parameters

pSrcDst – In-Place Signal Pointer.
nValue – Constant value to be used to right shift each vector element
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.