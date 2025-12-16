# Image Linear Transforms Functions — npp 13.1 documentation

>


# Image Linear Transforms Functions


Linear image transformations.


These functions can be found in the nppist library. Linking to only the sub-libraries that you use can significantly save link time, application load time, and CUDA runtime startup time when using dynamic libraries.


## Fourier Transforms


The set of Fourier transform functions available in the library.


Functions


NppStatus nppiMagnitude_32fc32f_C1R_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
32-bit floating point complex to 32-bit floating point magnitude.
Converts complex-number pixel image to single channel image computing the result pixels as the magnitude of the complex values.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiMagnitudeSqr_32fc32f_C1R_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
32-bit floating point complex to 32-bit floating point squared magnitude.
Converts complex-number pixel image to single channel image computing the result pixels as the squared magnitude of the complex values.
The squared magnitude is an itermediate result of magnitude computation and can thus be computed faster than actual magnitude. If magnitudes are required for sorting/comparing only, using this function instead of nppiMagnitude_32fc32f_C1R can be a worthwhile performance optimization.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context

Returns

Image Data Related Error Codes, ROI Related Error Codes