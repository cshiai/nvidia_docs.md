# Signal Filtering Functions


Functions that provide functionality of generating output signal based on the input signal like signal integral, etc.


## Integral


Compute the indefinite integral of a given signal. The i-th element is computed to be

  \[ s'_i = \sum_0^i s_j \]
Functions


NppStatus nppsIntegralGetBufferSize_32s(size_t nLength, size_t *hpBufferSize)
Device scratch buffer size (in bytes) for 32s nppsIntegral.
This primitive provides the correct buffer size for nppsIntegral_32s.

Parameters

nLength – Signal Length.
hpBufferSize – Required buffer size. Important: hpBufferSize is a host pointer. Scratch Buffer and Host Pointer.


NppStatus nppsIntegral_32s_Ctx(const Npp32s *pSrc, Npp32s *pDst, size_t nLength, Npp8u *pDeviceBuffer, NppStreamContext nppStreamCtx)
Compute cumulative sum of 32-bit signed integer signal.

Parameters

pSrc – Source Signal Pointer.
pDst – Pointer to the output result.
nLength – Signal Length.
pDeviceBuffer – Pointer to the required device memory allocation.
nppStreamCtx – Application Managed Stream Context.

Returns

Signal Data Related Error Codes, Length Related Error Codes.