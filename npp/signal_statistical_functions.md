# Signal Statistical Functions


Functions that provide global signal statistics like: sum, mean, standard deviation, min, max, etc.


## Signal Min Every Or Max Every


### MinEvery And MaxEvery Functions


Performs the min or max operation on the samples of a signal.




Functions


NppStatus nppsMinEvery_8u_I_Ctx(const Npp8u *pSrc, Npp8u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit in place min value for each pair of elements.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinEvery_16u_I_Ctx(const Npp16u *pSrc, Npp16u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short integer in place min value for each pair of elements.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinEvery_16s_I_Ctx(const Npp16s *pSrc, Npp16s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short integer in place min value for each pair of elements.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinEvery_32s_I_Ctx(const Npp32s *pSrc, Npp32s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed integer in place min value for each pair of elements.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinEvery_32f_I_Ctx(const Npp32f *pSrc, Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point in place min value for each pair of elements.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinEvery_64f_I_Ctx(const Npp64f *pSrc, Npp64f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
64-bit floating point in place min value for each pair of elements.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxEvery_8u_I_Ctx(const Npp8u *pSrc, Npp8u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
8-bit in place max value for each pair of elements.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxEvery_16u_I_Ctx(const Npp16u *pSrc, Npp16u *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit unsigned short integer in place max value for each pair of elements.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxEvery_16s_I_Ctx(const Npp16s *pSrc, Npp16s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
16-bit signed short integer in place max value for each pair of elements.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxEvery_32s_I_Ctx(const Npp32s *pSrc, Npp32s *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit signed integer in place max value for each pair of elements.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxEvery_32f_I_Ctx(const Npp32f *pSrc, Npp32f *pSrcDst, size_t nLength, NppStreamContext nppStreamCtx)
32-bit floating point in place max value for each pair of elements.

Parameters

pSrc – Source Signal Pointer.
pSrcDst – In-Place Signal Pointer.
nLength – Signal Length.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Sum


signal_min_every_or_max_every


### Sum


Performs the sum operation on the samples of a signal.


Functions


NppStatus nppsSumGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsSum_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSumGetBufferSize_32fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsSum_32fc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSumGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsSum_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSumGetBufferSize_64fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsSum_64fc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSumGetBufferSize_16s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsSum_16s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSumGetBufferSize_16sc_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsSum_16sc_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSumGetBufferSize_16sc32sc_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsSum_16sc32sc_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSumGetBufferSize_32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsSum_32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSumGetBufferSize_16s32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsSum_16s32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsSum_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pSum, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float vector sum method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pSum – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsSumGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSum_32fc_Ctx(const Npp32fc *pSrc, size_t nLength, Npp32fc *pSum, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float complex vector sum method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pSum – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsSumGetBufferSize_32fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSum_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pSum, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit double vector sum method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pSum – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsSumGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSum_64fc_Ctx(const Npp64fc *pSrc, size_t nLength, Npp64fc *pSum, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit double complex vector sum method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pSum – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsSumGetBufferSize_64fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSum_16s_Sfs_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pSum, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit short vector sum with integer scaling method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pSum – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsSumGetBufferSize_16s_Sfs_Ctx to determine the minium number of bytes required.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSum_32s_Sfs_Ctx(const Npp32s *pSrc, size_t nLength, Npp32s *pSum, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit integer vector sum with integer scaling method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pSum – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsSumGetBufferSize_32s_Sfs_Ctx to determine the minium number of bytes required.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSum_16sc_Sfs_Ctx(const Npp16sc *pSrc, size_t nLength, Npp16sc *pSum, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit short complex vector sum with integer scaling method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pSum – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsSumGetBufferSize_16sc_Sfs_Ctx to determine the minium number of bytes required.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSum_16sc32sc_Sfs_Ctx(const Npp16sc *pSrc, size_t nLength, Npp32sc *pSum, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit short complex vector sum (32bit int complex) with integer scaling method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pSum – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsSumGetBufferSize_16sc32sc_Sfs_Ctx to determine the minium number of bytes required.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsSum_16s32s_Sfs_Ctx(const Npp16s *pSrc, size_t nLength, Npp32s *pSum, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit integer vector sum (32bit) with integer scaling method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pSum – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsSumGetBufferSize_16s32s_Sfs_Ctx to determine the minium number of bytes required.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Maximum


### Maximum


Performs the maximum operation on the samples of a signal.


Functions


NppStatus nppsMaxGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMax_16s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaxGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMax_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaxGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMax_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaxGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMax_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMax_16s_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit integer vector max method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMax – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaxGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMax_32s_Ctx(const Npp32s *pSrc, size_t nLength, Npp32s *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit integer vector max method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMax – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaxGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMax_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float vector max method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMax – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaxGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMax_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float vector max method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMax – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaxGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxIndxGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMaxIndx_16s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaxIndxGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMaxIndx_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaxIndxGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMaxIndx_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaxIndxGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMaxIndx_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaxIndx_16s_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pMax, int *pIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit integer vector max index method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMax – Pointer to the output result.
pIndx – Pointer to the index value of the first maximum element.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaxIndxGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxIndx_32s_Ctx(const Npp32s *pSrc, size_t nLength, Npp32s *pMax, int *pIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit integer vector max index method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMax – Pointer to the output result.
pIndx – Pointer to the index value of the first maximum element.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaxIndxGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxIndx_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pMax, int *pIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float vector max index method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMax – Pointer to the output result.
pIndx – Pointer to the index value of the first maximum element.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaxIndxGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxIndx_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pMax, int *pIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float vector max index method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMax – Pointer to the output result.
pIndx – Pointer to the index value of the first maximum element.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaxIndxGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxAbsGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMaxAbs_16s_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaxAbsGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMaxAbs_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaxAbs_16s_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pMaxAbs, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit integer vector max absolute method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMaxAbs – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaxAbsGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxAbs_32s_Ctx(const Npp32s *pSrc, size_t nLength, Npp32s *pMaxAbs, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit integer vector max absolute method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMaxAbs – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaxAbsGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxAbsIndxGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMaxAbsIndx_16s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaxAbsIndxGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMaxAbsIndx_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaxAbsIndx_16s_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pMaxAbs, int *pIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit integer vector max absolute index method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMaxAbs – Pointer to the output result.
pIndx – Pointer to the index value of the first maximum element.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaxAbsIndxGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaxAbsIndx_32s_Ctx(const Npp32s *pSrc, size_t nLength, Npp32s *pMaxAbs, int *pIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit integer vector max absolute index method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMaxAbs – Pointer to the output result.
pIndx – Pointer to the index value of the first maximum element.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaxAbsIndxGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Minimum


### Minimum


Performs the minimum operation on the samples of a signal.


Functions


NppStatus nppsMinGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMin_16s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMin_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMin_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMin_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMin_16s_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pMin, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit integer vector min method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMin_32s_Ctx(const Npp32s *pSrc, size_t nLength, Npp32s *pMin, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit integer vector min method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMin_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pMin, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit integer vector min method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMin_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pMin, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit integer vector min method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinIndxGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMinIndx_16s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinIndxGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMinIndx_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinIndxGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMinIndx_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinIndxGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMinIndx_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinIndx_16s_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pMin, int *pIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit integer vector min index method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the output result.
pIndx – Pointer to the index value of the first minimum element.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinIndxGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinIndx_32s_Ctx(const Npp32s *pSrc, size_t nLength, Npp32s *pMin, int *pIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit integer vector min index method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the output result.
pIndx – Pointer to the index value of the first minimum element.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinIndxGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinIndx_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pMin, int *pIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float vector min index method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the output result.
pIndx – Pointer to the index value of the first minimum element.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinIndxGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinIndx_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pMin, int *pIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float vector min index method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the output result.
pIndx – Pointer to the index value of the first minimum element.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinIndxGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinAbsGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMinAbs_16s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinAbsGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMinAbs_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinAbs_16s_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pMinAbs, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit integer vector min absolute method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMinAbs – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinAbsGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinAbs_32s_Ctx(const Npp32s *pSrc, size_t nLength, Npp32s *pMinAbs, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit integer vector min absolute method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMinAbs – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinAbsGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinAbsIndxGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMinAbsIndx_16s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinAbsIndxGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMinAbsIndx_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinAbsIndx_16s_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pMinAbs, int *pIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit integer vector min absolute index method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMinAbs – Pointer to the output result.
pIndx – Pointer to the index value of the first minimum element.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinAbsIndxGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinAbsIndx_32s_Ctx(const Npp32s *pSrc, size_t nLength, Npp32s *pMinAbs, int *pIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit integer vector min absolute index method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMinAbs – Pointer to the output result.
pIndx – Pointer to the index value of the first minimum element.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinAbsIndxGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Mean


### Mean


Performs the mean operation on the samples of a signal.


Functions


NppStatus nppsMeanGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMean_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMeanGetBufferSize_32fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMean_32fc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMeanGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMean_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMeanGetBufferSize_64fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMean_64fc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMeanGetBufferSize_16s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMean_16s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMeanGetBufferSize_32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMean_32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMeanGetBufferSize_16sc_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMean_16sc_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMean_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pMean, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float vector mean method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMean – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMeanGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMean_32fc_Ctx(const Npp32fc *pSrc, size_t nLength, Npp32fc *pMean, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float complex vector mean method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMean – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMeanGetBufferSize_32fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMean_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pMean, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit double vector mean method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMean – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMeanGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMean_64fc_Ctx(const Npp64fc *pSrc, size_t nLength, Npp64fc *pMean, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit double complex vector mean method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMean – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMeanGetBufferSize_64fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMean_16s_Sfs_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pMean, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit short vector mean with integer scaling method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMean – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMeanGetBufferSize_16s_Sfs_Ctx to determine the minium number of bytes required.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMean_32s_Sfs_Ctx(const Npp32s *pSrc, size_t nLength, Npp32s *pMean, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit integer vector mean with integer scaling method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMean – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMeanGetBufferSize_32s_Sfs_Ctx to determine the minium number of bytes required.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMean_16sc_Sfs_Ctx(const Npp16sc *pSrc, size_t nLength, Npp16sc *pMean, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit short complex vector mean with integer scaling method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMean – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMeanGetBufferSize_16sc_Sfs_Ctx to determine the minium number of bytes required.
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal StdDev


### Standard Deviation


Calculates the standard deviation for the samples of a signal.


Functions


NppStatus nppsStdDevGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsStdDev_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsStdDevGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsStdDev_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsStdDevGetBufferSize_16s32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsStdDev_16s32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsStdDevGetBufferSize_16s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsStdDev_16s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsStdDev_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pStdDev, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float vector standard deviation method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pStdDev – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsStdDevGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsStdDev_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pStdDev, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float vector standard deviation method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pStdDev – Pointer to the output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsStdDevGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsStdDev_16s32s_Sfs_Ctx(const Npp16s *pSrc, size_t nLength, Npp32s *pStdDev, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit float vector standard deviation method (return value is 32-bit)

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pStdDev – Pointer to the output result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsStdDevGetBufferSize_16s32s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsStdDev_16s_Sfs_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pStdDev, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit float vector standard deviation method (return value is also 16-bit)

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pStdDev – Pointer to the output result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsStdDevGetBufferSize_16s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Mean And StdDev


### Mean And Standard Deviation


Performs the mean and calculates the standard deviation for the samples of a signal.


Functions


NppStatus nppsMeanStdDevGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMeanStdDev_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMeanStdDevGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMeanStdDev_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMeanStdDevGetBufferSize_16s32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMeanStdDev_16s32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMeanStdDevGetBufferSize_16s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device scratch buffer size (in bytes) for nppsMeanStdDev_16s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMeanStdDev_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pMean, Npp32f *pStdDev, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float vector mean and standard deviation method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMean – Pointer to the output mean value.
pStdDev – Pointer to the output standard deviation value.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMeanStdDevGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMeanStdDev_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pMean, Npp64f *pStdDev, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float vector mean and standard deviation method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMean – Pointer to the output mean value.
pStdDev – Pointer to the output standard deviation value.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMeanStdDevGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMeanStdDev_16s32s_Sfs_Ctx(const Npp16s *pSrc, size_t nLength, Npp32s *pMean, Npp32s *pStdDev, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit float vector mean and standard deviation method (return values are 32-bit)

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMean – Pointer to the output mean value.
pStdDev – Pointer to the output standard deviation value.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMeanStdDevGetBufferSize_16s32s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMeanStdDev_16s_Sfs_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pMean, Npp16s *pStdDev, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit float vector mean and standard deviation method (return values are also 16-bit)

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMean – Pointer to the output mean value.
pStdDev – Pointer to the output standard deviation value.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMeanStdDevGetBufferSize_16s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal MinMax


### Minimum Maximum


Performs the maximum and the minimum operation on the samples of a signal.


Functions


NppStatus nppsMinMaxGetBufferSize_8u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMax_8u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMax_16s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxGetBufferSize_16u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMax_16u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMax_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxGetBufferSize_32u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMax_32u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMax_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMax_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMax_8u_Ctx(const Npp8u *pSrc, size_t nLength, Npp8u *pMin, Npp8u *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
8-bit char vector min and max method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMax – Pointer to the max output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxGetBufferSize_8u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMax_16s_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pMin, Npp16s *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short vector min and max method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMax – Pointer to the max output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMax_16u_Ctx(const Npp16u *pSrc, size_t nLength, Npp16u *pMin, Npp16u *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit unsigned short vector min and max method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMax – Pointer to the max output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxGetBufferSize_16u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMax_32u_Ctx(const Npp32u *pSrc, size_t nLength, Npp32u *pMin, Npp32u *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit unsigned int vector min and max method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMax – Pointer to the max output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxGetBufferSize_32u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMax_32s_Ctx(const Npp32s *pSrc, size_t nLength, Npp32s *pMin, Npp32s *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit signed int vector min and max method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMax – Pointer to the max output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMax_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pMin, Npp32f *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float vector min and max method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMax – Pointer to the max output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMax_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pMin, Npp64f *pMax, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit double vector min and max method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMax – Pointer to the max output result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMaxIndxGetBufferSize_8u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMaxIndx_8u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxIndxGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMaxIndx_16s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxIndxGetBufferSize_16u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMaxIndx_16u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxIndxGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMaxIndx_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxIndxGetBufferSize_32u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMaxIndx_32u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxIndxGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMaxIndx_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxIndxGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMinMaxIndx_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMinMaxIndx_8u_Ctx(const Npp8u *pSrc, size_t nLength, Npp8u *pMin, int *pMinIndx, Npp8u *pMax, int *pMaxIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
8-bit char vector min and max with indices method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMinIndx – Pointer to the index of the first min value.
pMax – Pointer to the max output result.
pMaxIndx – Pointer to the index of the first max value.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxIndxGetBufferSize_8u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMaxIndx_16s_Ctx(const Npp16s *pSrc, size_t nLength, Npp16s *pMin, int *pMinIndx, Npp16s *pMax, int *pMaxIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short vector min and max with indices method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMinIndx – Pointer to the index of the first min value.
pMax – Pointer to the max output result.
pMaxIndx – Pointer to the index of the first max value.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxIndxGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMaxIndx_16u_Ctx(const Npp16u *pSrc, size_t nLength, Npp16u *pMin, int *pMinIndx, Npp16u *pMax, int *pMaxIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit unsigned short vector min and max with indices method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMinIndx – Pointer to the index of the first min value.
pMax – Pointer to the max output result.
pMaxIndx – Pointer to the index of the first max value.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxIndxGetBufferSize_16u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMaxIndx_32s_Ctx(const Npp32s *pSrc, size_t nLength, Npp32s *pMin, int *pMinIndx, Npp32s *pMax, int *pMaxIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit signed short vector min and max with indices method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMinIndx – Pointer to the index of the first min value.
pMax – Pointer to the max output result.
pMaxIndx – Pointer to the index of the first max value.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxIndxGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMaxIndx_32u_Ctx(const Npp32u *pSrc, size_t nLength, Npp32u *pMin, int *pMinIndx, Npp32u *pMax, int *pMaxIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit unsigned short vector min and max with indices method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMinIndx – Pointer to the index of the first min value.
pMax – Pointer to the max output result.
pMaxIndx – Pointer to the index of the first max value.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxIndxGetBufferSize_32u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMaxIndx_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pMin, int *pMinIndx, Npp32f *pMax, int *pMaxIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float vector min and max with indices method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMinIndx – Pointer to the index of the first min value.
pMax – Pointer to the max output result.
pMaxIndx – Pointer to the index of the first max value.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxIndxGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMinMaxIndx_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pMin, int *pMinIndx, Npp64f *pMax, int *pMaxIndx, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float vector min and max with indices method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pMin – Pointer to the min output result.
pMinIndx – Pointer to the index of the first min value.
pMax – Pointer to the max output result.
pMaxIndx – Pointer to the index of the first max value.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMinMaxIndxGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Norms


### Signal Norm Inf


#### Infinity Norm


Performs the infinity norm on the samples of a signal.


Functions


NppStatus nppsNormInfGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_Inf_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_Inf_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float vector C norm method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormInfGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormInfGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_Inf_64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_Inf_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float vector C norm method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormInfGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormInfGetBufferSize_16s32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_Inf_16s32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_Inf_16s32f_Ctx(const Npp16s *pSrc, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer vector C norm method, return value is 32-bit float.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormInfGetBufferSize_16s32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormInfGetBufferSize_32fc32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_Inf_32fc32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_Inf_32fc32f_Ctx(const Npp32fc *pSrc, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float complex vector C norm method, return value is 32-bit float.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormInfGetBufferSize_32fc32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormInfGetBufferSize_64fc64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_Inf_64fc64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_Inf_64fc64f_Ctx(const Npp64fc *pSrc, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float complex vector C norm method, return value is 64-bit float.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormInfGetBufferSize_64fc64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormInfGetBufferSize_16s32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_Inf_16s32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_Inf_16s32s_Sfs_Ctx(const Npp16s *pSrc, size_t nLength, Npp32s *pNorm, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer vector C norm method, return value is 32-bit signed integer.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormInfGetBufferSize_16s32s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Norm L1


#### L1 Norm


Performs the L1 norm on the samples of a signal.


Functions


NppStatus nppsNormL1GetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L1_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L1_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float vector L1 norm method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL1GetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormL1GetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L1_64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L1_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float vector L1 norm method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL1GetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormL1GetBufferSize_16s32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L1_16s32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L1_16s32f_Ctx(const Npp16s *pSrc, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer vector L1 norm method, return value is 32-bit float.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the L1 norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL1GetBufferSize_16s32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormL1GetBufferSize_32fc64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L1_32fc64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L1_32fc64f_Ctx(const Npp32fc *pSrc, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float complex vector L1 norm method, return value is 64-bit float.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL1GetBufferSize_32fc64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormL1GetBufferSize_64fc64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L1_64fc64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L1_64fc64f_Ctx(const Npp64fc *pSrc, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float complex vector L1 norm method, return value is 64-bit float.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL1GetBufferSize_64fc64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormL1GetBufferSize_16s32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L1_16s32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L1_16s32s_Sfs_Ctx(const Npp16s *pSrc, size_t nLength, Npp32s *pNorm, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer vector L1 norm method, return value is 32-bit signed integer.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL1GetBufferSize_16s32s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormL1GetBufferSize_16s64s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L1_16s64s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L1_16s64s_Sfs_Ctx(const Npp16s *pSrc, size_t nLength, Npp64s *pNorm, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer vector L1 norm method, return value is 64-bit signed integer.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL1GetBufferSize_16s64s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Norm L2


#### L2 Norm


Performs the L2 norm on the samples of a signal.


Functions


NppStatus nppsNormL2GetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L2_32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L2_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float vector L2 norm method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL2GetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormL2GetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L2_64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L2_64f_Ctx(const Npp64f *pSrc, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float vector L2 norm method

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL2GetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormL2GetBufferSize_16s32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L2_16s32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L2_16s32f_Ctx(const Npp16s *pSrc, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer vector L2 norm method, return value is 32-bit float.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL2GetBufferSize_16s32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormL2GetBufferSize_32fc64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L2_32fc64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L2_32fc64f_Ctx(const Npp32fc *pSrc, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float complex vector L2 norm method, return value is 64-bit float.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL2GetBufferSize_32fc64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormL2GetBufferSize_64fc64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L2_64fc64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L2_64fc64f_Ctx(const Npp64fc *pSrc, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float complex vector L2 norm method, return value is 64-bit float.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL2GetBufferSize_64fc64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormL2GetBufferSize_16s32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L2_16s32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L2_16s32s_Sfs_Ctx(const Npp16s *pSrc, size_t nLength, Npp32s *pNorm, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer vector L2 norm method, return value is 32-bit signed integer.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL2GetBufferSize_16s32s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormL2SqrGetBufferSize_16s64s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNorm_L2Sqr_16s64s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNorm_L2Sqr_16s64s_Sfs_Ctx(const Npp16s *pSrc, size_t nLength, Npp64s *pNorm, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer vector L2 Square norm method, return value is 64-bit signed integer.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormL2SqrGetBufferSize_16s64s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Norm Inf NormDiff


#### Infinity Norm Diff


Performs the infinity norm on the samples of two input signals’ difference.


Functions


NppStatus nppsNormDiffInfGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_Inf_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_Inf_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float C norm method on two vectors’ difference

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffInfGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffInfGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_Inf_64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_Inf_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float C norm method on two vectors’ difference

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffInfGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffInfGetBufferSize_16s32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_Inf_16s32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_Inf_16s32f_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer C norm method on two vectors’ difference, return value is 32-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffInfGetBufferSize_16s32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffInfGetBufferSize_32fc32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_Inf_32fc32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_Inf_32fc32f_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float complex C norm method on two vectors’ difference, return value is 32-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffInfGetBufferSize_32fc32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffInfGetBufferSize_64fc64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_Inf_64fc64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_Inf_64fc64f_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float complex C norm method on two vectors’ difference, return value is 64-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffInfGetBufferSize_64fc64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffInfGetBufferSize_16s32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_Inf_16s32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_Inf_16s32s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp32s *pNorm, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer C norm method on two vectors’ difference, return value is 32-bit signed integer.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffInfGetBufferSize_16s32s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Norm L1 NormDiff


#### L1 Norm Diff


Performs the L1 norm on the samples of two input signals’ difference.


Functions


NppStatus nppsNormDiffL1GetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L1_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L1_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float L1 norm method on two vectors’ difference

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL1GetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffL1GetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L1_64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L1_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float L1 norm method on two vectors’ difference

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL1GetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffL1GetBufferSize_16s32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L1_16s32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L1_16s32f_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer L1 norm method on two vectors’ difference, return value is 32-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the L1 norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL1GetBufferSize_16s32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffL1GetBufferSize_32fc64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L1_32fc64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L1_32fc64f_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float complex L1 norm method on two vectors’ difference, return value is 64-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL1GetBufferSize_32fc64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffL1GetBufferSize_64fc64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L1_64fc64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L1_64fc64f_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float complex L1 norm method on two vectors’ difference, return value is 64-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL1GetBufferSize_64fc64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffL1GetBufferSize_16s32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L1_16s32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L1_16s32s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp32s *pNorm, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer L1 norm method on two vectors’ difference, return value is 32-bit signed integer.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer..
nLength – Signal Length.
pNorm – Pointer to the norm result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL1GetBufferSize_16s32s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffL1GetBufferSize_16s64s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L1_16s64s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L1_16s64s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp64s *pNorm, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer L1 norm method on two vectors’ difference, return value is 64-bit signed integer.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL1GetBufferSize_16s64s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


### Signal Norm L2 NormDiff


#### L2 Norm Diff


Performs the L2 norm on the samples of two input signals’ difference.


Functions


NppStatus nppsNormDiffL2GetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L2_32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L2_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float L2 norm method on two vectors’ difference

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL2GetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffL2GetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L2_64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L2_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float L2 norm method on two vectors’ difference

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL2GetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffL2GetBufferSize_16s32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L2_16s32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L2_16s32f_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp32f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer L2 norm method on two vectors’ difference, return value is 32-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL2GetBufferSize_16s32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffL2GetBufferSize_32fc64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L2_32fc64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L2_32fc64f_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float complex L2 norm method on two vectors’ difference, return value is 64-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL2GetBufferSize_32fc64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffL2GetBufferSize_64fc64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L2_64fc64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L2_64fc64f_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, size_t nLength, Npp64f *pNorm, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float complex L2 norm method on two vectors’ difference, return value is 64-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL2GetBufferSize_64fc64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffL2GetBufferSize_16s32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L2_16s32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L2_16s32s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp32s *pNorm, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer L2 norm method on two vectors’ difference, return value is 32-bit signed integer.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL2GetBufferSize_16s32s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsNormDiffL2SqrGetBufferSize_16s64s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsNormDiff_L2Sqr_16s64s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsNormDiff_L2Sqr_16s64s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp64s *pNorm, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer L2 Square norm method on two vectors’ difference, return value is 64-bit signed integer.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pNorm – Pointer to the norm result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsNormDiffL2SqrGetBufferSize_16s64s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Dot Product


### Dot Product


Performs the dot product operation on the samples of two input signals.


Functions


NppStatus nppsDotProdGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, size_t nLength, Npp32f *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float dot product method, return value is 32-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_32fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_32fc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_32fc_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, size_t nLength, Npp32fc *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float complex dot product method, return value is 32-bit float complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_32fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_32f32fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_32f32fc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_32f32fc_Ctx(const Npp32f *pSrc1, const Npp32fc *pSrc2, size_t nLength, Npp32fc *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float and 32-bit float complex dot product method, return value is 32-bit float complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_32f32fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_32f64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_32f64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_32f64f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, size_t nLength, Npp64f *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float dot product method, return value is 64-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_32f64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_32fc64fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_32fc64fc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_32fc64fc_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, size_t nLength, Npp64fc *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float complex dot product method, return value is 64-bit float complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_32fc64fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_32f32fc64fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_32f32fc64fc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_32f32fc64fc_Ctx(const Npp32f *pSrc1, const Npp32fc *pSrc2, size_t nLength, Npp64fc *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit float and 32-bit float complex dot product method, return value is 64-bit float complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_32f32fc64fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, size_t nLength, Npp64f *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float dot product method, return value is 64-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_64fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_64fc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_64fc_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, size_t nLength, Npp64fc *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float complex dot product method, return value is 64-bit float complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_64fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_64f64fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_64f64fc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_64f64fc_Ctx(const Npp64f *pSrc1, const Npp64fc *pSrc2, size_t nLength, Npp64fc *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit float and 64-bit float complex dot product method, return value is 64-bit float complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_64f64fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16s64s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16s64s_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16s64s_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp64s *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer dot product method, return value is 64-bit signed integer.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16s64s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16sc64sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16sc64sc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16sc64sc_Ctx(const Npp16sc *pSrc1, const Npp16sc *pSrc2, size_t nLength, Npp64sc *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer complex dot product method, return value is 64-bit signed integer complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16sc64sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16s16sc64sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16s16sc64sc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16s16sc64sc_Ctx(const Npp16s *pSrc1, const Npp16sc *pSrc2, size_t nLength, Npp64sc *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer and 16-bit signed short integer short dot product method, return value is 64-bit signed integer complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16s16sc64sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16s32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16s32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16s32f_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp32f *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer dot product method, return value is 32-bit float.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16s32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16sc32fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16sc32fc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16sc32fc_Ctx(const Npp16sc *pSrc1, const Npp16sc *pSrc2, size_t nLength, Npp32fc *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer complex dot product method, return value is 32-bit float complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16sc32fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16s16sc32fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16s16sc32fc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16s16sc32fc_Ctx(const Npp16s *pSrc1, const Npp16sc *pSrc2, size_t nLength, Npp32fc *pDp, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer and 16-bit signed short integer complex dot product method, return value is 32-bit float complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16s16sc32fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp16s *pDp, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer dot product method, return value is 16-bit signed short integer.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16sc_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16sc_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16sc_Sfs_Ctx(const Npp16sc *pSrc1, const Npp16sc *pSrc2, size_t nLength, Npp16sc *pDp, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer complex dot product method, return value is 16-bit signed short integer complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16sc_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_32s_Sfs_Ctx(const Npp32s *pSrc1, const Npp32s *pSrc2, size_t nLength, Npp32s *pDp, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit signed integer dot product method, return value is 32-bit signed integer.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_32s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_32sc_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_32sc_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_32sc_Sfs_Ctx(const Npp32sc *pSrc1, const Npp32sc *pSrc2, size_t nLength, Npp32sc *pDp, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit signed integer complex dot product method, return value is 32-bit signed integer complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_32sc_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16s32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16s32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16s32s_Sfs_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp32s *pDp, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer dot product method, return value is 32-bit signed integer.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16s32s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16s16sc32sc_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16s16sc32sc_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16s16sc32sc_Sfs_Ctx(const Npp16s *pSrc1, const Npp16sc *pSrc2, size_t nLength, Npp32sc *pDp, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer and 16-bit signed short integer complex dot product method, return value is 32-bit signed integer complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16s16sc32sc_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16s32s32s_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16s32s32s_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16s32s32s_Sfs_Ctx(const Npp16s *pSrc1, const Npp32s *pSrc2, size_t nLength, Npp32s *pDp, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer and 32-bit signed integer dot product method, return value is 32-bit signed integer.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16s32s32s_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16s16sc_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16s16sc_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16s16sc_Sfs_Ctx(const Npp16s *pSrc1, const Npp16sc *pSrc2, size_t nLength, Npp16sc *pDp, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer and 16-bit signed short integer complex dot product method, return value is 16-bit signed short integer complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16s16sc_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_16sc32sc_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_16sc32sc_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_16sc32sc_Sfs_Ctx(const Npp16sc *pSrc1, const Npp16sc *pSrc2, size_t nLength, Npp32sc *pDp, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer complex dot product method, return value is 32-bit signed integer complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_16sc32sc_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsDotProdGetBufferSize_32s32sc_Sfs_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsDotProd_32s32sc_Sfs_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsDotProd_32s32sc_Sfs_Ctx(const Npp32s *pSrc1, const Npp32sc *pSrc2, size_t nLength, Npp32sc *pDp, int nScaleFactor, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit signed short integer and 32-bit signed short integer complex dot product method, return value is 32-bit signed integer complex.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDp – Pointer to the dot product result.
nScaleFactor – Integer Result Scaling.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsDotProdGetBufferSize_32s32sc_Sfs_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Count In Range


### Count In Range


Calculates the number of elements from specified range in the samples of a signal.


Functions


NppStatus nppsCountInRangeGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsCountInRange_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsCountInRange_32s_Ctx(const Npp32s *pSrc, size_t nLength, int *pCounts, Npp32s nLowerBound, Npp32s nUpperBound, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Computes the number of elements whose values fall into the specified range on a 32-bit signed integer array.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pCounts – Pointer to the number of elements.
nLowerBound – Lower bound of the specified range.
nUpperBound – Upper bound of the specified range.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsCountInRangeGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Count Zero Crossings


### Count Zero Crossings


Calculates the number of zero crossings in a signal.


Functions


NppStatus nppsZeroCrossingGetBufferSize_16s32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsZeroCrossing_16s32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsZeroCrossing_16s32f_Ctx(const Npp16s *pSrc, size_t nLength, Npp32f *pValZC, NppsZCType tZCType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer zero crossing method, return value is 32-bit floating point.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pValZC – Pointer to the output result.
tZCType – Type of the zero crossing measure: nppZCR, nppZCXor or nppZCC.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsZeroCrossingGetBufferSize_16s32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsZeroCrossingGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsZeroCrossing_32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsZeroCrossing_32f_Ctx(const Npp32f *pSrc, size_t nLength, Npp32f *pValZC, NppsZCType tZCType, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit floating-point zero crossing method, return value is 32-bit floating point.

Parameters

pSrc – Source Signal Pointer.
nLength – Signal Length.
pValZC – Pointer to the output result.
tZCType – Type of the zero crossing measure: nppZCR, nppZCXor or nppZCC.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsZeroCrossingGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


## Signal Maximum Error


### MaximumError


Primitives for computing the maximum error between two signals. Given two signals \(pSrc1\) and \(pSrc2\) both with length \(N\), the maximum error is defined as the largest absolute difference between the corresponding elements of two signals.


If the signal is in complex format, the absolute value of the complex number is used.


Functions


NppStatus nppsMaximumError_8u_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
8-bit unsigned char maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_8u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_8s_Ctx(const Npp8s *pSrc1, const Npp8s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
8-bit signed char maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_8s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_16u_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit unsigned short integer maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_16u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_16s_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_16sc_Ctx(const Npp16sc *pSrc1, const Npp16sc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit unsigned short complex integer maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_16sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_32u_Ctx(const Npp32u *pSrc1, const Npp32u *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit unsigned short integer maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_32u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_32s_Ctx(const Npp32s *pSrc1, const Npp32s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit signed short integer maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_32sc_Ctx(const Npp32sc *pSrc1, const Npp32sc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit unsigned short complex integer maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_32sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_64s_Ctx(const Npp64s *pSrc1, const Npp64s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit signed short integer maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_64s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_64sc_Ctx(const Npp64sc *pSrc1, const Npp64sc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit unsigned short complex integer maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_64sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit floating point maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_32fc_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit floating point complex maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_32fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit floating point maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumError_64fc_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit floating point complex maximum method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumErrorGetBufferSize_64fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumErrorGetBufferSize_8u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_8u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_8s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_8s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_16u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_16u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_16s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_16sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_16sc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_32u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_32u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_32sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_32sc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_64s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_64s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_64sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_64sc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_32fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_32fc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumErrorGetBufferSize_64fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumError_64fc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


## Signal Average Error


### AverageError


Primitives for computing the Average error between two signals. Given two signals \(pSrc1\) and \(pSrc2\) both with length \(N\), the average error is defined as

  \[Average Error = \frac{1}{N}\sum_{n=0}^{N-1}\left|pSrc1(n) - pSrc2(n)\right|\]
If the signal is in complex format, the absolute value of the complex number is used.


Functions


NppStatus nppsAverageError_8u_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
8-bit unsigned char Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_8u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_8s_Ctx(const Npp8s *pSrc1, const Npp8s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
8-bit signed char Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_8s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_16u_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit unsigned short integer Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_16u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_16s_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_16sc_Ctx(const Npp16sc *pSrc1, const Npp16sc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit unsigned short complex integer Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_16sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_32u_Ctx(const Npp32u *pSrc1, const Npp32u *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit unsigned short integer Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_32u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_32s_Ctx(const Npp32s *pSrc1, const Npp32s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit signed short integer Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_32sc_Ctx(const Npp32sc *pSrc1, const Npp32sc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit unsigned short complex integer Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_32sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_64s_Ctx(const Npp64s *pSrc1, const Npp64s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit signed short integer Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_64s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_64sc_Ctx(const Npp64sc *pSrc1, const Npp64sc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit unsigned short complex integer Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_64sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit floating point Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_32fc_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit floating point complex Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_32fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit floating point Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageError_64fc_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit floating point complex Average method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageErrorGetBufferSize_64fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageErrorGetBufferSize_8u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_8u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_8s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_8s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_16u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_16u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_16s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_16sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_16sc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_32u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_32u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_32sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_32sc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_64s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_64s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_64sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_64sc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_32fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_32fc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageErrorGetBufferSize_64fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageError_64fc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


## Signal Maximum Relative Error


### MaximumRelativeError


Primitives for computing the MaximumRelative error between two signals. Given two signals \(pSrc1\) and \(pSrc2\) both with length \(N\), the maximum relative error is defined as

  \[MaximumRelativeError = max{\frac{\left|pSrc1(n) - pSrc2(n)\right|}{max(\left|pSrc1(n)\right|, \left|pSrc2(n)\right|)}}\]
If the signal is in complex format, the absolute value of the complex number is used.


Functions


NppStatus nppsMaximumRelativeError_8u_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
8-bit unsigned char MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_8u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_8s_Ctx(const Npp8s *pSrc1, const Npp8s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
8-bit signed char MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_8s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_16u_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit unsigned short integer MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_16u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_16s_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_16sc_Ctx(const Npp16sc *pSrc1, const Npp16sc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit unsigned short complex integer MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_16sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_32u_Ctx(const Npp32u *pSrc1, const Npp32u *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit unsigned short integer MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_32u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_32s_Ctx(const Npp32s *pSrc1, const Npp32s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit signed short integer MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_32sc_Ctx(const Npp32sc *pSrc1, const Npp32sc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit unsigned short complex integer MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_32sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_64s_Ctx(const Npp64s *pSrc1, const Npp64s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit signed short integer MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_64s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_64sc_Ctx(const Npp64sc *pSrc1, const Npp64sc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit unsigned short complex integer MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_64sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit floating point MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_32fc_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit floating point complex MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_32fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit floating point MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeError_64fc_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit floating point complex MaximumRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsMaximumRelativeErrorGetBufferSize_64fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsMaximumRelativeErrorGetBufferSize_8u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_8u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_8s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_8s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_16u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_16u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_16s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_16sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_16sc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_32u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_32u.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_32sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_32sc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_64s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_64s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_64sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_64sc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_32f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_32fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_32fc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_64f.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsMaximumRelativeErrorGetBufferSize_64fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsMaximumRelativeError_64fc.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


## Signal Average Relative Error


### AverageRelativeError


Primitives for computing the AverageRelative error between two signals. Given two signals \(pSrc1\) and \(pSrc2\) both with length \(N\), the average relative error is defined as

  \[AverageRelativeError = \frac{1}{N}\sum_{n=0}^{N-1}\frac{\left|pSrc1(n) - pSrc2(n)\right|}{max(\left|pSrc1(n)\right|, \left|pSrc2(n)\right|)}\]
If the signal is in complex format, the absolute value of the complex number is used.


Functions


NppStatus nppsAverageRelativeError_8u_Ctx(const Npp8u *pSrc1, const Npp8u *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
8-bit unsigned char AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_8u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_8s_Ctx(const Npp8s *pSrc1, const Npp8s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
8-bit signed char AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_8s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_16u_Ctx(const Npp16u *pSrc1, const Npp16u *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit unsigned short integer AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_16u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_16s_Ctx(const Npp16s *pSrc1, const Npp16s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit signed short integer AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_16s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_16sc_Ctx(const Npp16sc *pSrc1, const Npp16sc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
16-bit unsigned short complex integer AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_16sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_32u_Ctx(const Npp32u *pSrc1, const Npp32u *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit unsigned short integer AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_32u_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_32s_Ctx(const Npp32s *pSrc1, const Npp32s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit signed short integer AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_32s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_32sc_Ctx(const Npp32sc *pSrc1, const Npp32sc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit unsigned short complex integer AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_32sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_64s_Ctx(const Npp64s *pSrc1, const Npp64s *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit signed short integer AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_64s_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_64sc_Ctx(const Npp64sc *pSrc1, const Npp64sc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit unsigned short complex integer AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_64sc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_32f_Ctx(const Npp32f *pSrc1, const Npp32f *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit floating point AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_32f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_32fc_Ctx(const Npp32fc *pSrc1, const Npp32fc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
32-bit floating point complex AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_32fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_64f_Ctx(const Npp64f *pSrc1, const Npp64f *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit floating point AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_64f_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeError_64fc_Ctx(const Npp64fc *pSrc1, const Npp64fc *pSrc2, size_t nLength, Npp64f *pDst, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
64-bit floating point complex AverageRelative method.

Parameters

pSrc1 – Source Signal Pointer.
pSrc2 – Source Signal Pointer.
nLength – Signal Length.
pDst – Pointer to the error result.
pDeviceBuffer – Pointer to the required device memory allocation, Scratch Buffer and Host Pointer. Use nppsAverageRelativeErrorGetBufferSize_64fc_Ctx to determine the minium number of bytes required.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.


NppStatus nppsAverageRelativeErrorGetBufferSize_8u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_8u_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_8s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_8s_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_16u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_16u_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_16s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_16s_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_16sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_16sc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_32u_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_32u_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_32s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_32s_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_32sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_32sc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_64s_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_64s_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_64sc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_64sc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_32f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_32f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_32fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_32fc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_64f_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_64f_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS


NppStatus nppsAverageRelativeErrorGetBufferSize_64fc_Ctx(size_t nLength, size_t *hpBufferSize, NppStreamContext nppStreamCtx)
Device-buffer size (in bytes) for nppsAverageRelativeError_64fc_Ctx.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer.
nppStreamCtx – Application Managed Stream Context.

Returns

NPP_SUCCESS