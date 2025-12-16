# Image Arithmetic And Logical Operations


These functions can be found in the nppial library.


Linking to only the sub-libraries that you use can significantly save link time, application load time, and CUDA runtime startup time when using dynamic libraries.


## Arithmetic Operations


### Arithmetic Operations


The set of image processing arithmetic operations available in the library.


### AddC


Adds a constant value to each pixel of an image.


Note: If you use one of the device constant versions of these functions and the function called immediately preceeding that function generates that device constant you MUST either call cudaStreamSynchronize() or cudaDeviceSynchronize() before calling the device constant function.


Functions


NppStatus nppiAddC_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – pointer to device memory Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_8u_C1IRSfs_Ctx(const Npp8u nConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image add constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_8u_C1IRSfs_Ctx(const Npp8u *pConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image add constant, scale, then clamp to saturated value.

Parameters

pConstant – pointer to device memory Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_8u_C3IRSfs_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel 8-bit unsigned char in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_8u_C3IRSfs_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel 8-bit unsigned char in place image add constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_8u_AC4IRSfs_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_8u_AC4IRSfs_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image add constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[4], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_8u_C4IRSfs_Ctx(const Npp8u aConstants[4], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_8u_C4IRSfs_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image add constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u nConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16u_C1IRSfs_Ctx(const Npp16u nConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image add constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16u_C1IRSfs_Ctx(const Npp16u *pConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image add constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16u_C3IRSfs_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16u_C3IRSfs_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image add constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16u_AC4IRSfs_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16u_AC4IRSfs_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image add constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[4], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16u_C4IRSfs_Ctx(const Npp16u aConstants[4], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16u_C4IRSfs_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image add constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s nConstant, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstant, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16s_C1IRSfs_Ctx(const Npp16s nConstant, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image add constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16s_C1IRSfs_Ctx(const Npp16s *pConstant, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image add constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s aConstants[3], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstants, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16s_C3IRSfs_Ctx(const Npp16s aConstants[3], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16s_C3IRSfs_Ctx(const Npp16s *pConstants, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image add constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s aConstants[3], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstants, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16s_AC4IRSfs_Ctx(const Npp16s aConstants[3], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16s_AC4IRSfs_Ctx(const Npp16s *pConstants, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha in place image add constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s aConstants[4], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstants, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16s_C4IRSfs_Ctx(const Npp16s aConstants[4], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16s_C4IRSfs_Ctx(const Npp16s *pConstants, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image add constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16sc_C1RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc nConstant, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16sc_C1IRSfs_Ctx(const Npp16sc nConstant, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image add constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16sc_C3RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc aConstants[3], Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16sc_C3IRSfs_Ctx(const Npp16sc aConstants[3], Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16sc_AC4RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc aConstants[3], Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16sc_AC4IRSfs_Ctx(const Npp16sc aConstants[3], Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32s_C1RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s nConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_32s_C1RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32s_C1IRSfs_Ctx(const Npp32s nConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image add constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_32s_C1IRSfs_Ctx(const Npp32s *pConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image add constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32s_C3RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_32s_C3RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pConstants, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32s_C3IRSfs_Ctx(const Npp32s aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_32s_C3IRSfs_Ctx(const Npp32s *pConstants, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image add constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32sc_C1RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc nConstant, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32sc_C1IRSfs_Ctx(const Npp32sc nConstant, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel in place image add constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32sc_C3RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc aConstants[3], Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32sc_C3IRSfs_Ctx(const Npp32sc aConstants[3], Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32sc_AC4RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc aConstants[3], Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel with unmodified alpha image add constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32sc_AC4IRSfs_Ctx(const Npp32sc aConstants[3], Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel with unmodified alpha in place image add constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f nConstant, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory 32-bit floating point constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f *pConstant, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory 32-bit floating point constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16f_C1IR_Ctx(const Npp32f nConstant, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image add constant.

Parameters

nConstant – host memory 32-bit floating point constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16f_C1IR_Ctx(const Npp32f *pConstant, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image add constant.

Parameters

pConstant – device memory 32-bit floating point constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16f_C3R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f aConstants[3], Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16f_C3R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16f_C3IR_Ctx(const Npp32f aConstants[3], Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image add constant.

Parameters

aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16f_C3IR_Ctx(const Npp32f *pConstants, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image add constant.

Parameters

pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16f_C4R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f aConstants[4], Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16f_C4R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_16f_C4IR_Ctx(const Npp32f aConstants[4], Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image add constant.

Parameters

aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_16f_C4IR_Ctx(const Npp32f *pConstants, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image add constant.

Parameters

pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f nConstant, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstant, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32f_C1IR_Ctx(const Npp32f nConstant, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image add constant.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_32f_C1IR_Ctx(const Npp32f *pConstant, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image add constant.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f aConstants[3], Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32f_C3IR_Ctx(const Npp32f aConstants[3], Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image add constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_32f_C3IR_Ctx(const Npp32f *pConstants, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image add constant.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f aConstants[3], Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32f_AC4IR_Ctx(const Npp32f aConstants[3], Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha in place image add constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_32f_AC4IR_Ctx(const Npp32f *pConstants, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha in place image add constant.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f aConstants[4], Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32f_C4IR_Ctx(const Npp32f aConstants[4], Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image add constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddDeviceC_32f_C4IR_Ctx(const Npp32f *pConstants, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image add constant.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32fc_C1R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc nConstant, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32fc_C1IR_Ctx(const Npp32fc nConstant, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel in place image add constant.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32fc_C3R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc aConstants[3], Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32fc_C3IR_Ctx(const Npp32fc aConstants[3], Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel in place image add constant.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32fc_AC4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc aConstants[3], Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel with unmodified alpha image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32fc_AC4IR_Ctx(const Npp32fc aConstants[3], Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel with unmodified alpha in place image add constant.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32fc_C4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc aConstants[4], Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel image add constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddC_32fc_C4IR_Ctx(const Npp32fc aConstants[4], Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel in place image add constant.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### MulC


Multiplies each pixel of an image by a constant value.


Note: If you use one of the device constant versions of these functions and the function called immediately preceeding that function generates that device constant you MUST either call cudaStreamSynchronize() or cudaDeviceSynchronize() before calling the device constant function.


Functions


NppStatus nppiMulC_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_8u_C1IRSfs_Ctx(const Npp8u nConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_8u_C1IRSfs_Ctx(const Npp8u *pConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_8u_C3IRSfs_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel 8-bit unsigned char in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_8u_C3IRSfs_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel 8-bit unsigned char in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_8u_AC4IRSfs_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_8u_AC4IRSfs_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[4], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_8u_C4IRSfs_Ctx(const Npp8u aConstants[4], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_8u_C4IRSfs_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u nConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16u_C1IRSfs_Ctx(const Npp16u nConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16u_C1IRSfs_Ctx(const Npp16u *pConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16u_C3IRSfs_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16u_C3IRSfs_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16u_AC4IRSfs_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16u_AC4IRSfs_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[4], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16u_C4IRSfs_Ctx(const Npp16u aConstants[4], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16u_C4IRSfs_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s nConstant, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstant, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16s_C1IRSfs_Ctx(const Npp16s nConstant, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16s_C1IRSfs_Ctx(const Npp16s *pConstant, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s aConstants[3], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstants, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16s_C3IRSfs_Ctx(const Npp16s aConstants[3], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16s_C3IRSfs_Ctx(const Npp16s *pConstants, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s aConstants[3], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstants, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16s_AC4IRSfs_Ctx(const Npp16s aConstants[3], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16s_AC4IRSfs_Ctx(const Npp16s *pConstants, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s aConstants[4], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstants, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16s_C4IRSfs_Ctx(const Npp16s aConstants[4], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16s_C4IRSfs_Ctx(const Npp16s *pConstants, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16sc_C1RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc nConstant, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16sc_C1IRSfs_Ctx(const Npp16sc nConstant, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16sc_C3RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc aConstants[3], Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16sc_C3IRSfs_Ctx(const Npp16sc aConstants[3], Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16sc_AC4RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc aConstants[3], Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16sc_AC4IRSfs_Ctx(const Npp16sc aConstants[3], Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32s_C1RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s nConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_32s_C1RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32s_C1IRSfs_Ctx(const Npp32s nConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_32s_C1IRSfs_Ctx(const Npp32s *pConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32s_C3RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_32s_C3RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pConstants, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32s_C3IRSfs_Ctx(const Npp32s aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_32s_C3IRSfs_Ctx(const Npp32s *pConstants, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32sc_C1RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc nConstant, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32sc_C1IRSfs_Ctx(const Npp32sc nConstant, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32sc_C3RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc aConstants[3], Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32sc_C3IRSfs_Ctx(const Npp32sc aConstants[3], Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32sc_AC4RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc aConstants[3], Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel with unmodified alpha image multiply by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32sc_AC4IRSfs_Ctx(const Npp32sc aConstants[3], Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel with unmodified alpha in place image multiply by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f nConstant, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – 32-bit floating point host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f *pConstant, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – 32-bit floating point device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16f_C1IR_Ctx(const Npp32f nConstant, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image multiply by constant.

Parameters

nConstant – 32-bit floating point host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16f_C1IR_Ctx(const Npp32f *pConstant, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image multiply by constant.

Parameters

pConstant – 32-bit floating point device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16f_C3R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f aConstants[3], Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16f_C3R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16f_C3IR_Ctx(const Npp32f aConstants[3], Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image multiply by constant.

Parameters

aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16f_C3IR_Ctx(const Npp32f *pConstants, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image multiply by constant.

Parameters

pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16f_C4R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f aConstants[4], Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16f_C4R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_16f_C4IR_Ctx(const Npp32f aConstants[4], Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image multiply by constant.

Parameters

aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_16f_C4IR_Ctx(const Npp32f *pConstants, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image multiply by constant.

Parameters

pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f nConstant, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstant, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32f_C1IR_Ctx(const Npp32f nConstant, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image multiply by constant.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_32f_C1IR_Ctx(const Npp32f *pConstant, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image multiply by constant.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f aConstants[3], Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32f_C3IR_Ctx(const Npp32f aConstants[3], Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image multiply by constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_32f_C3IR_Ctx(const Npp32f *pConstants, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image multiply by constant.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f aConstants[3], Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32f_AC4IR_Ctx(const Npp32f aConstants[3], Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha in place image multiply by constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_32f_AC4IR_Ctx(const Npp32f *pConstants, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha in place image multiply by constant.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f aConstants[4], Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32f_C4IR_Ctx(const Npp32f aConstants[4], Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image multiply by constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceC_32f_C4IR_Ctx(const Npp32f *pConstants, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image multiply by constant.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32fc_C1R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc nConstant, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32fc_C1IR_Ctx(const Npp32fc nConstant, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel in place image multiply by constant.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32fc_C3R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc aConstants[3], Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32fc_C3IR_Ctx(const Npp32fc aConstants[3], Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel in place image multiply by constant.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32fc_AC4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc aConstants[3], Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel with unmodified alpha image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32fc_AC4IR_Ctx(const Npp32fc aConstants[3], Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel with unmodified alpha in place image multiply by constant.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32fc_C4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc aConstants[4], Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel image multiply by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulC_32fc_C4IR_Ctx(const Npp32fc aConstants[4], Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel in place image multiply by constant.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### MulCScale


Multiplies each pixel of an image by a constant value then scales the result by the maximum value for the data bit width.


Note: If you use one of the device constant versions of these functions and the function called immediately preceeding that function generates that device constant you MUST either call cudaStreamSynchronize() or cudaDeviceSynchronize() before calling the device constant function.


Functions


NppStatus nppiMulCScale_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_8u_C1IR_Ctx(const Npp8u nConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image multiply by constant and scale by max bit width value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_8u_C1IR_Ctx(const Npp8u *pConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image multiply by constant and scale by max bit width value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_8u_C3IR_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel 8-bit unsigned char in place image multiply by constant and scale by max bit width value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_8u_C3IR_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel 8-bit unsigned char in place image multiply by constant and scale by max bit width value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_8u_AC4IR_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image multiply by constant, scale and scale by max bit width value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_8u_AC4IR_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image multiply by constant, scale and scale by max bit width value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[4], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_8u_C4IR_Ctx(const Npp8u aConstants[4], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image multiply by constant and scale by max bit width value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_8u_C4IR_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image multiply by constant and scale by max bit width value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u nConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_16u_C1IR_Ctx(const Npp16u nConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image multiply by constant and scale by max bit width value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_16u_C1IR_Ctx(const Npp16u *pConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image multiply by constant and scale by max bit width value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_16u_C3IR_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image multiply by constant and scale by max bit width value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_16u_C3IR_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image multiply by constant and scale by max bit width value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_16u_AC4IR_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image multiply by constant and scale by max bit width value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_16u_AC4IR_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image multiply by constant and scale by max bit width value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[4], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image multiply by constant and scale by max bit width value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulCScale_16u_C4IR_Ctx(const Npp16u aConstants[4], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image multiply by constant and scale by max bit width value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulDeviceCScale_16u_C4IR_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image multiply by constant and scale by max bit width value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### SubC


Subtracts a constant value from each pixel of an image.


Note: If you use one of the device constant versions of these functions and the function called immediately preceeding that function generates that device constant you MUST either call cudaStreamSynchronize() or cudaDeviceSynchronize() before calling the device constant function.


Functions


NppStatus nppiSubC_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_8u_C1IRSfs_Ctx(const Npp8u nConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_8u_C1IRSfs_Ctx(const Npp8u *pConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_8u_C3IRSfs_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel 8-bit unsigned char in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_8u_C3IRSfs_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel 8-bit unsigned char in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_8u_AC4IRSfs_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_8u_AC4IRSfs_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[4], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_8u_C4IRSfs_Ctx(const Npp8u aConstants[4], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_8u_C4IRSfs_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u nConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16u_C1IRSfs_Ctx(const Npp16u nConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16u_C1IRSfs_Ctx(const Npp16u *pConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16u_C3IRSfs_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16u_C3IRSfs_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16u_AC4IRSfs_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16u_AC4IRSfs_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[4], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16u_C4IRSfs_Ctx(const Npp16u aConstants[4], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16u_C4IRSfs_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s nConstant, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstant, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16s_C1IRSfs_Ctx(const Npp16s nConstant, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16s_C1IRSfs_Ctx(const Npp16s *pConstant, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s aConstants[3], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstants, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16s_C3IRSfs_Ctx(const Npp16s aConstants[3], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16s_C3IRSfs_Ctx(const Npp16s *pConstants, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s aConstants[3], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstants, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16s_AC4IRSfs_Ctx(const Npp16s aConstants[3], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16s_AC4IRSfs_Ctx(const Npp16s *pConstants, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s aConstants[4], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstants, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16s_C4IRSfs_Ctx(const Npp16s aConstants[4], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16s_C4IRSfs_Ctx(const Npp16s *pConstants, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16sc_C1RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc nConstant, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16sc_C1IRSfs_Ctx(const Npp16sc nConstant, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16sc_C3RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc aConstants[3], Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16sc_C3IRSfs_Ctx(const Npp16sc aConstants[3], Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16sc_AC4RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc aConstants[3], Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16sc_AC4IRSfs_Ctx(const Npp16sc aConstants[3], Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32s_C1RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s nConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_32s_C1RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32s_C1IRSfs_Ctx(const Npp32s nConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_32s_C1IRSfs_Ctx(const Npp32s *pConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32s_C3RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_32s_C3RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pConstants, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32s_C3IRSfs_Ctx(const Npp32s aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_32s_C3IRSfs_Ctx(const Npp32s *pConstants, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32sc_C1RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc nConstant, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32sc_C1IRSfs_Ctx(const Npp32sc nConstant, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32sc_C3RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc aConstants[3], Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32sc_C3IRSfs_Ctx(const Npp32sc aConstants[3], Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32sc_AC4RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc aConstants[3], Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel with unmodified alpha image subtract constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32sc_AC4IRSfs_Ctx(const Npp32sc aConstants[3], Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel with unmodified alpha in place image subtract constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f nConstant, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory 32-bit floating point constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f *pConstant, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory 32-bit floating point constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16f_C1IR_Ctx(const Npp32f nConstant, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image subtract constant.

Parameters

nConstant – host memory 32-bit floating point constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16f_C1IR_Ctx(const Npp32f *pConstant, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image subtract constant.

Parameters

pConstant – device memory 32-bit floating point constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16f_C3R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f aConstants[3], Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16f_C3R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16f_C3IR_Ctx(const Npp32f aConstants[3], Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image subtract constant.

Parameters

aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16f_C3IR_Ctx(const Npp32f *pConstants, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image subtract constant.

Parameters

pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16f_C4R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f aConstants[4], Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16f_C4R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_16f_C4IR_Ctx(const Npp32f aConstants[4], Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image subtract constant.

Parameters

aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_16f_C4IR_Ctx(const Npp32f *pConstants, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image subtract constant.

Parameters

pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f nConstant, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstant, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32f_C1IR_Ctx(const Npp32f nConstant, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image subtract constant.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_32f_C1IR_Ctx(const Npp32f *pConstant, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image subtract constant.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f aConstants[3], Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32f_C3IR_Ctx(const Npp32f aConstants[3], Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image subtract constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_32f_C3IR_Ctx(const Npp32f *pConstants, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image subtract constant.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f aConstants[3], Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32f_AC4IR_Ctx(const Npp32f aConstants[3], Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha in place image subtract constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_32f_AC4IR_Ctx(const Npp32f *pConstants, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha in place image subtract constant.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f aConstants[4], Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32f_C4IR_Ctx(const Npp32f aConstants[4], Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image subtract constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubDeviceC_32f_C4IR_Ctx(const Npp32f *pConstants, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image subtract constant.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32fc_C1R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc nConstant, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32fc_C1IR_Ctx(const Npp32fc nConstant, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel in place image subtract constant.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32fc_C3R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc aConstants[3], Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32fc_C3IR_Ctx(const Npp32fc aConstants[3], Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel in place image subtract constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32fc_AC4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc aConstants[3], Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel with unmodified alpha image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32fc_AC4IR_Ctx(const Npp32fc aConstants[3], Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel with unmodified alpha in place image subtract constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32fc_C4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc aConstants[4], Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel image subtract constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSubC_32fc_C4IR_Ctx(const Npp32fc aConstants[4], Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel in place image subtract constant.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### DivC


Divides each pixel of an image by a constant value.


Note: If you use one of the device constant versions of these functions and the function called immediately preceeding that function generates that device constant you MUST either call cudaStreamSynchronize() or cudaDeviceSynchronize() before calling the device constant function.


Functions


NppStatus nppiDivC_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_8u_C1IRSfs_Ctx(const Npp8u nConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_8u_C1IRSfs_Ctx(const Npp8u *pConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_8u_C3IRSfs_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel 8-bit unsigned char in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_8u_C3IRSfs_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel 8-bit unsigned char in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_8u_AC4IRSfs_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_8u_AC4IRSfs_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[4], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pConstants, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_8u_C4IRSfs_Ctx(const Npp8u aConstants[4], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_8u_C4IRSfs_Ctx(const Npp8u *pConstants, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u nConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16u_C1IRSfs_Ctx(const Npp16u nConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16u_C1IRSfs_Ctx(const Npp16u *pConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16u_C3IRSfs_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16u_C3IRSfs_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16u_AC4IRSfs_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16u_AC4IRSfs_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[4], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pConstants, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16u_C4IRSfs_Ctx(const Npp16u aConstants[4], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16u_C4IRSfs_Ctx(const Npp16u *pConstants, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s nConstant, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstant, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16s_C1IRSfs_Ctx(const Npp16s nConstant, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16s_C1IRSfs_Ctx(const Npp16s *pConstant, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s aConstants[3], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstants, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16s_C3IRSfs_Ctx(const Npp16s aConstants[3], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16s_C3IRSfs_Ctx(const Npp16s *pConstants, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s aConstants[3], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstants, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16s_AC4IRSfs_Ctx(const Npp16s aConstants[3], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16s_AC4IRSfs_Ctx(const Npp16s *pConstants, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s aConstants[4], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pConstants, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16s_C4IRSfs_Ctx(const Npp16s aConstants[4], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16s_C4IRSfs_Ctx(const Npp16s *pConstants, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16sc_C1RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc nConstant, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16sc_C1IRSfs_Ctx(const Npp16sc nConstant, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16sc_C3RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc aConstants[3], Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16sc_C3IRSfs_Ctx(const Npp16sc aConstants[3], Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16sc_AC4RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc aConstants[3], Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16sc_AC4IRSfs_Ctx(const Npp16sc aConstants[3], Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32s_C1RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s nConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32s_C1RSfs(const Npp32s *pSrc1, int nSrc1Step, const Npp32s nConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor)
One 32-bit signed integer channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_32s_C1RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32s_C1IRSfs_Ctx(const Npp32s nConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_32s_C1IRSfs_Ctx(const Npp32s *pConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32s_C3RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_32s_C3RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pConstants, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32s_C3IRSfs_Ctx(const Npp32s aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_32s_C3IRSfs_Ctx(const Npp32s *pConstants, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32sc_C1RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc nConstant, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32sc_C1IRSfs_Ctx(const Npp32sc nConstant, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32sc_C3RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc aConstants[3], Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32sc_C3IRSfs_Ctx(const Npp32sc aConstants[3], Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32sc_AC4RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc aConstants[3], Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel with unmodified alpha image divided by constant, scale, then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32sc_AC4IRSfs_Ctx(const Npp32sc aConstants[3], Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed complex integer (32-bit real, 32-bit imaginary) channel with unmodified alpha in place image divided by constant, scale, then clamp to saturated value.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f nConstant, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory 32-bit floating point constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f *pConstant, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory 32-bit floating point constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16f_C1IR_Ctx(const Npp32f nConstant, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image divided by constant.

Parameters

nConstant – host memory 32-bit floating point constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16f_C1IR_Ctx(const Npp32f *pConstant, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image divided by constant.

Parameters

pConstant – device memory 32-bit floating point constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16f_C3R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f aConstants[3], Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16f_C3R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16f_C3IR_Ctx(const Npp32f aConstants[3], Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image divided by constant.

Parameters

aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16f_C3IR_Ctx(const Npp32f *pConstants, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image divided by constant.

Parameters

pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16f_C4R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f aConstants[4], Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16f_C4R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_16f_C4IR_Ctx(const Npp32f aConstants[4], Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image divided by constant.

Parameters

aConstants – fixed size host memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_16f_C4IR_Ctx(const Npp32f *pConstants, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image divided by constant.

Parameters

pConstants – fixed size device memory array of 32-bit floating point constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f nConstant, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstant, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32f_C1IR_Ctx(const Npp32f nConstant, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image divided by constant.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_32f_C1IR_Ctx(const Npp32f *pConstant, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image divided by constant.

Parameters

pConstant – device memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f aConstants[3], Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32f_C3IR_Ctx(const Npp32f aConstants[3], Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image divided by constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_32f_C3IR_Ctx(const Npp32f *pConstants, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image divided by constant.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f aConstants[3], Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32f_AC4IR_Ctx(const Npp32f aConstants[3], Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha in place image divided by constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_32f_AC4IR_Ctx(const Npp32f *pConstants, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha in place image divided by constant.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f aConstants[4], Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size host memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pConstants, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstants – fixed size device memory array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32f_C4IR_Ctx(const Npp32f aConstants[4], Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image divided by constant.

Parameters

aConstants – fixed size host memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivDeviceC_32f_C4IR_Ctx(const Npp32f *pConstants, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image divided by constant.

Parameters

pConstants – fixed size device memory array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32fc_C1R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc nConstant, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32fc_C1IR_Ctx(const Npp32fc nConstant, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel in place image divided by constant.

Parameters

nConstant – host memory constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32fc_C3R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc aConstants[3], Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32fc_C3IR_Ctx(const Npp32fc aConstants[3], Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel in place image divided by constant.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32fc_AC4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc aConstants[3], Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel with unmodified alpha image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32fc_AC4IR_Ctx(const Npp32fc aConstants[3], Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel with unmodified alpha in place image divided by constant.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32fc_C4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc aConstants[4], Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel image divided by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of host memory constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDivC_32fc_C4IR_Ctx(const Npp32fc aConstants[4], Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit complex floating point (32-bit floating point real, 32-bit floating point imaginary) channel in place image divided by constant.

Parameters

aConstants – fixed size array of host memory constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### AbsDiffC


Determines absolute difference between each pixel of an image and a constant value.


Note: If you use one of the device constant versions of these functions and the function called immediately preceeding that function generates that device constant you MUST either call cudaStreamSynchronize() or cudaDeviceSynchronize() before calling the device constant function.


Functions


NppStatus nppiAbsDiffC_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nConstant, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image absolute difference with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbsDiffDeviceC_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u *pConstant, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image absolute difference with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbsDiffC_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, Npp16u nConstant, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image absolute difference with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbsDiffDeviceC_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, Npp16u *pConstant, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image absolute difference with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbsDiffC_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, Npp32f nConstant, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image absolute difference with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – host memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbsDiffDeviceC_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, Npp32f *pConstant, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image absolute difference with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pConstant – device memory constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Add


Pixel by pixel addition of two images.


Functions


NppStatus nppiAdd_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_8u_C1IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_8u_C3IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_8u_AC4IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_8u_C4IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16u_C1IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16u_C3IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16u_AC4IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16u_C4IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16s_C1IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16s_C3IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16s_AC4IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16s_C4IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16sc_C1RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16sc_C1IRSfs_Ctx(const Npp16sc *pSrc, int nSrcStep, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16sc_C3RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16sc_C3IRSfs_Ctx(const Npp16sc *pSrc, int nSrcStep, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16sc_AC4RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16sc_AC4RSfs(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16sc_AC4IRSfs_Ctx(const Npp16sc *pSrc, int nSrcStep, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32s_C1RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Note: This function is to be deprecated in future NPP releases, use the function above with a scale factor of 0 instead.
32-bit image add. Add the pixel values of corresponding pixels in the ROI and write them to the output image.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32s_C1IRSfs_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32s_C3RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32s_C3IRSfs_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32sc_C1RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32sc_C1IRSfs_Ctx(const Npp32sc *pSrc, int nSrcStep, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32sc_C3RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32sc_C3IRSfs_Ctx(const Npp32sc *pSrc, int nSrcStep, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32sc_AC4RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32sc_AC4IRSfs_Ctx(const Npp32sc *pSrc, int nSrcStep, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha in place image addition, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image addition.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16f_C1IR_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image addition.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16f_C3R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image addition.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16f_C3IR_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image addition.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16f_C4R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image addition.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_16f_C4IR_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image addition.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image addition.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32f_C1IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image addition.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image addition.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32f_C3IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image addition.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha image addition.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32f_AC4IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha in place image addition.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image addition.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32f_C4IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image addition.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32fc_C1R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel image addition.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32fc_C1IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel in place image addition.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32fc_C3R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel image addition.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32fc_C3IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel in place image addition.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32fc_AC4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha image addition.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32fc_AC4IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha in place image addition.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32fc_C4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel image addition.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAdd_32fc_C4IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel in place image addition.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### AddSquare


Pixel by pixel addition of squared pixels from source image to floating point pixel values of destination image.


Functions


NppStatus nppiAddSquare_8u32f_C1IMR_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image squared then added to in place floating point destination image using filter mask (updates destination when mask is non-zero).

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pMask – Mask-Image Pointer.
nMaskStep – Mask-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddSquare_8u32f_C1IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image squared then added to in place floating point destination image.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddSquare_16u32f_C1IMR_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image squared then added to in place floating point destination image using filter mask (updates destination when mask is non-zero).

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pMask – Mask-Image Pointer.
nMaskStep – Mask-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddSquare_16u32f_C1IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image squared then added to in place floating point destination image.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddSquare_32f_C1IMR_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image squared then added to in place floating point destination image using filter mask (updates destination when mask is non-zero).

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pMask – Mask-Image Pointer.
nMaskStep – Mask-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddSquare_32f_C1IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image squared then added to in place floating point destination image.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### AddProduct


Pixel by pixel addition of product of pixels from two source images to floating point pixel values of destination image.


Functions


NppStatus nppiAddProduct_8u32f_C1IMR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image product added to in place floating point destination image using filter mask (updates destination when mask is non-zero).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pMask – Mask-Image Pointer.
nMaskStep – Mask-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddProduct_8u32f_C1IR_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image product added to in place floating point destination image.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddProduct_16u32f_C1IMR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image product added to in place floating point destination image using filter mask (updates destination when mask is non-zero).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pMask – Mask-Image Pointer.
nMaskStep – Mask-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddProduct_16u32f_C1IR_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image product added to in place floating point destination image.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddProduct_32f_C1IMR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, const Npp8u *pMask, int nMaskStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image product added to in place floating point destination image using filter mask (updates destination when mask is non-zero).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pMask – Mask-Image Pointer.
nMaskStep – Mask-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddProduct_32f_C1IR_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image product added to in place floating point destination image.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddProduct_16f_C1IR_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image product added to in place floating point destination image.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### AddWeighted


Pixel by pixel addition of alpha weighted pixel values from a source image to floating point pixel values of destination image.


Functions


NppStatus nppiAddWeighted_8u32f_C1IMR_Ctx(const Npp8u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, Npp32f nAlpha, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel alpha weighted image added to in place floating point destination image using filter mask (updates destination when mask is non-zero).

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pMask – Mask-Image Pointer.
nMaskStep – Mask-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAlpha – Alpha weight to be applied to source image pixels (0.0F to 1.0F)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddWeighted_8u32f_C1IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, Npp32f nAlpha, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel alpha weighted image added to in place floating point destination image.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAlpha – Alpha weight to be applied to source image pixels (0.0F to 1.0F)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddWeighted_16u32f_C1IMR_Ctx(const Npp16u *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, Npp32f nAlpha, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel alpha weighted image added to in place floating point destination image using filter mask (updates destination when mask is non-zero).

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pMask – Mask-Image Pointer.
nMaskStep – Mask-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAlpha – Alpha weight to be applied to source image pixels (0.0F to 1.0F)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddWeighted_16u32f_C1IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, Npp32f nAlpha, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel alpha weighted image added to in place floating point destination image.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAlpha – Alpha weight to be applied to source image pixels (0.0F to 1.0F)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddWeighted_32f_C1IMR_Ctx(const Npp32f *pSrc, int nSrcStep, const Npp8u *pMask, int nMaskStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, Npp32f nAlpha, NppStreamContext nppStreamCtx)
One 32-bit floating point channel alpha weighted image added to in place floating point destination image using filter mask (updates destination when mask is non-zero).

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pMask – Mask-Image Pointer.
nMaskStep – Mask-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAlpha – Alpha weight to be applied to source image pixels (0.0F to 1.0F)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAddWeighted_32f_C1IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, Npp32f nAlpha, NppStreamContext nppStreamCtx)
One 32-bit floating point channel alpha weighted image added to in place floating point destination image.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAlpha – Alpha weight to be applied to source image pixels (0.0F to 1.0F)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Mul


Pixel by pixel multiply of two images.


Functions


NppStatus nppiMul_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_8u_C1IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_8u_C3IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_8u_AC4IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_8u_C4IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16u_C1IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16u_C3IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16u_AC4IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16u_C4IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16s_C1IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16s_C3IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16s_AC4IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16s_C4IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16sc_C1RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16sc_C1IRSfs_Ctx(const Npp16sc *pSrc, int nSrcStep, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16sc_C3RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16sc_C3IRSfs_Ctx(const Npp16sc *pSrc, int nSrcStep, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16sc_AC4RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16sc_AC4IRSfs_Ctx(const Npp16sc *pSrc, int nSrcStep, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32s_C1RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Note: This function is to be deprecated in future NPP releases, use the function above with a scale factor of 0 instead.
1 channel 32-bit image multiplication. Multiply corresponding pixels in ROI.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32s_C1IRSfs_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32s_C3RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32s_C3IRSfs_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32sc_C1RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32sc_C1IRSfs_Ctx(const Npp32sc *pSrc, int nSrcStep, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32sc_C3RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32sc_C3IRSfs_Ctx(const Npp32sc *pSrc, int nSrcStep, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32sc_AC4RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32sc_AC4IRSfs_Ctx(const Npp32sc *pSrc, int nSrcStep, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha in place image multiplication, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image multiplication.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16f_C1IR_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image multiplication.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16f_C3R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image multiplication.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16f_C3IR_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image multiplication.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16f_C4R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image multiplication.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_16f_C4IR_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image multiplication.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image multiplication.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32f_C1IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image multiplication.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image multiplication.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32f_C3IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image multiplication.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha image multiplication.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32f_AC4IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha in place image multiplication.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image multiplication.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32f_C4IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image multiplication.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32fc_C1R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel image multiplication.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32fc_C1IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel in place image multiplication.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32fc_C3R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel image multiplication.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32fc_C3IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel in place image multiplication.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32fc_AC4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha image multiplication.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32fc_AC4IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha in place image multiplication.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32fc_C4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel image multiplication.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMul_32fc_C4IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel in place image multiplication.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### MulScale


Pixel by pixel multiplies each pixel of two images then scales the result by the maximum value for the data bit width.


Functions


NppStatus nppiMulScale_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_8u_C1IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_8u_C3IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_8u_AC4IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_8u_C4IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_16u_C1IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_16u_C3IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_16u_AC4IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiMulScale_16u_C4IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image multiplication then scale by maximum value for pixel bit width.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Sub


Pixel by pixel subtraction of two images.


Functions


NppStatus nppiSub_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_8u_C1IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_8u_C3IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_8u_AC4IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_8u_C4IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16u_C1IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16u_C3IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16u_AC4IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16u_C4IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16s_C1IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16s_C3IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16s_AC4IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16s_C4IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16sc_C1RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16sc_C1IRSfs_Ctx(const Npp16sc *pSrc, int nSrcStep, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16sc_C3RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16sc_C3IRSfs_Ctx(const Npp16sc *pSrc, int nSrcStep, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16sc_AC4RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16sc_AC4IRSfs_Ctx(const Npp16sc *pSrc, int nSrcStep, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32s_C1RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Note: This function is to be deprecated in future NPP releases, use the function above with a scale factor of 0 instead.
32-bit image subtraction. Subtract pSrc1’s pixels from corresponding pixels in pSrc2.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32s_C1IRSfs_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32s_C3RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32s_C3IRSfs_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32s_C4RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32s_C4IRSfs_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32sc_C1RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32sc_C1IRSfs_Ctx(const Npp32sc *pSrc, int nSrcStep, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32sc_C3RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32sc_C3IRSfs_Ctx(const Npp32sc *pSrc, int nSrcStep, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32sc_AC4RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32sc_AC4IRSfs_Ctx(const Npp32sc *pSrc, int nSrcStep, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha in place image subtraction, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image subtraction.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16f_C1IR_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image subtraction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16f_C3R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image subtraction.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16f_C3IR_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image subtraction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16f_C4R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image subtraction.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_16f_C4IR_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image subtraction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image subtraction.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32f_C1IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image subtraction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image subtraction.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32f_C3IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image subtraction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha image subtraction.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32f_AC4IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha in place image subtraction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image subtraction.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32f_C4IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image subtraction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32fc_C1R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel image subtraction.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32fc_C1IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel in place image subtraction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32fc_C3R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel image subtraction.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32fc_C3IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel in place image subtraction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32fc_AC4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha image subtraction.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32fc_AC4IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha in place image subtraction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32fc_C4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel image subtraction.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSub_32fc_C4IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel in place image subtraction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Div


Pixel by pixel division of two images.


Functions


NppStatus nppiDiv_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_8u_C1IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_8u_C3IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_8u_AC4IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel with unmodified alpha in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_8u_C4IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16u_C1RSfs(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor)
One 16-bit unsigned short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16u_C1IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16u_C3IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16u_AC4IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel with unmodified alpha in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16u_C4IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16s_C1IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16s_C3IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16s_AC4IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel with unmodified alpha in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16s_C4IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16sc_C1RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16sc_C1IRSfs_Ctx(const Npp16sc *pSrc, int nSrcStep, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16sc_C3RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16sc_C3IRSfs_Ctx(const Npp16sc *pSrc, int nSrcStep, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16sc_AC4RSfs_Ctx(const Npp16sc *pSrc1, int nSrc1Step, const Npp16sc *pSrc2, int nSrc2Step, Npp16sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16sc_AC4IRSfs_Ctx(const Npp16sc *pSrc, int nSrcStep, Npp16sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short complex number (16-bit real, 16-bit imaginary) channel with unmodified alpha in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32s_C1RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Note: This function is to be deprecated in future NPP releases, use the function above with a scale factor of 0 instead.
32-bit image division. Divide pixels in pSrc2 by pSrc1’s pixels.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32s_C1IRSfs_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32s_C3RSfs_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32s_C3IRSfs_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32sc_C1RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32sc_C1IRSfs_Ctx(const Npp32sc *pSrc, int nSrcStep, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32sc_C3RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32sc_C3IRSfs_Ctx(const Npp32sc *pSrc, int nSrcStep, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32sc_AC4RSfs_Ctx(const Npp32sc *pSrc1, int nSrc1Step, const Npp32sc *pSrc2, int nSrc2Step, Npp32sc *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32sc_AC4IRSfs_Ctx(const Npp32sc *pSrc, int nSrcStep, Npp32sc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 32-bit signed integer complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image division.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16f_C1IR_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image division.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16f_C3R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image division.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16f_C3IR_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image division.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16f_C4R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image division.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_16f_C4IR_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image division.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image division.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32f_C1IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image division.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32f_C3R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image division.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32f_C3IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image division.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha image division.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32f_AC4IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel with unmodified alpha in place image division.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32f_C4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image division.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32f_C4IR_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image division.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32fc_C1R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel image division.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32fc_C1IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel in place image division.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32fc_C3R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel image division.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32fc_C3IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel in place image division.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32fc_AC4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha image division.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32fc_AC4IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel with unmodified alpha in place image division.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32fc_C4R_Ctx(const Npp32fc *pSrc1, int nSrc1Step, const Npp32fc *pSrc2, int nSrc2Step, Npp32fc *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel image division.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_32fc_C4IR_Ctx(const Npp32fc *pSrc, int nSrcStep, Npp32fc *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point complex number (32-bit real, 32-bit imaginary) channel in place image division.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Div_Round


Pixel by pixel division of two images using result rounding modes.


Functions


NppStatus nppiDiv_Round_8u_C1RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_8u_C1IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_8u_C3RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_8u_C3IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_8u_AC4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image division with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_8u_AC4IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image division with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_8u_C4RSfs_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_8u_C4IRSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16u_C1RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16u_C1IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16u_C3RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16u_C3IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16u_AC4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image division with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL)
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16u_AC4IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image division with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL)
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16u_C4RSfs_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL)
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16u_C4IRSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL)
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16s_C1RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL)
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16s_C1IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL)
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16s_C3RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL)
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16s_C3IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL)
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16s_AC4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image division with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL)
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16s_AC4IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image division with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16s_C4RSfs_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiDiv_Round_16s_C4IRSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppRoundMode rndMode, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image division, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
rndMode – Result Rounding mode to be used (NPP_RND_ZERO, NPP_RND_NEAR, or NP_RND_FINANCIAL).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Abs


Absolute value of each pixel value in an image.


Functions


NppStatus nppiAbs_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image absolute value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16s_C1IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image absolute value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image absolute value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16s_C3IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image absolute value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image absolute value with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16s_AC4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image absolute value with unmodified alpha.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image absolute value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16s_C4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image absolute value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16f_C1R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image absolute value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16f_C1IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image absolute value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16f_C3R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image absolute value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16f_C3IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image absolute value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16f_C4R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image absolute value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_16f_C4IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image absolute value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image absolute value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image absolute value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image absolute value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image absolute value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image absolute value with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image absolute value with unmodified alpha.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image absolute value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbs_32f_C4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image absolute value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### AbsDiff


Pixel by pixel absolute difference between two images.


Functions


NppStatus nppiAbsDiff_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel absolute difference of image1 minus image2.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbsDiff_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channels absolute difference of image1 minus image2.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbsDiff_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channels absolute difference of image1 minus image2.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbsDiff_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel absolute difference of image1 minus image2.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbsDiff_16f_C1R_Ctx(const Npp16f *pSrc1, int nSrc1Step, const Npp16f *pSrc2, int nSrc2Step, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel absolute difference of image1 minus image2.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAbsDiff_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel absolute difference of image1 minus image2.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Sqr


Square each pixel in an image.


Functions


NppStatus nppiSqr_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_8u_C1IRSfs_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_8u_C3IRSfs_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_8u_AC4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image squared with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_8u_AC4IRSfs_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image squared with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_8u_C4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_8u_C4IRSfs_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16u_C1RSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16u_C1IRSfs_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16u_C3RSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16u_C3IRSfs_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16u_AC4RSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image squared with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16u_AC4IRSfs_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image squared with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16u_C4RSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16u_C4IRSfs_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16s_C1RSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16s_C1IRSfs_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16s_C3RSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16s_C3IRSfs_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16s_AC4RSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image squared with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16s_AC4IRSfs_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image squared with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16s_C4RSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16s_C4IRSfs_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image squared, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16f_C1R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image squared.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16f_C1IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image squared.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16f_C3R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image squared.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16f_C3IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image squared.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16f_C4R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image squared.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_16f_C4IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image squared.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image squared.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image squared.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image squared.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image squared.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image squared with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image squared with unmodified alpha.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image squared.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqr_32f_C4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image squared.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Sqrt


Pixel by pixel square root of each pixel in an image.


Functions


NppStatus nppiSqrt_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image square root, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_8u_C1IRSfs_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image square root, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image square root, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_8u_C3IRSfs_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image square root, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_8u_AC4RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image square root with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_8u_AC4IRSfs_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image square root with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16u_C1RSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image square root, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16u_C1IRSfs_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image square root, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16u_C3RSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image square root, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16u_C3IRSfs_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image square root, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16u_AC4RSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image square root with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16u_AC4IRSfs_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image square root with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16s_C1RSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image square root, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16s_C1IRSfs_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image square root, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16s_C3RSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image square root, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16s_C3IRSfs_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image square root, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16s_AC4RSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image square root with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16s_AC4IRSfs_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image square root with unmodified alpha, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16f_C1R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image square root.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16f_C1IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image square root.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16f_C3R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image square root.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16f_C3IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image square root.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16f_C4R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel image square root.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_16f_C4IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit floating point channel in place image square root.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image square root.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image square root.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image square root.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image square root.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image square root with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image square root with unmodified alpha.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image square root.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiSqrt_32f_C4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel in place image square root.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Ln


Pixel by pixel natural logarithm of each pixel in an image.


Functions


NppStatus nppiLn_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image natural logarithm, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_8u_C1IRSfs_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image natural logarithm, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image natural logarithm, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_8u_C3IRSfs_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image natural logarithm, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_16u_C1RSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image natural logarithm, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_16u_C1IRSfs_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image natural logarithm, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_16u_C3RSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image natural logarithm, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_16u_C3IRSfs_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image natural logarithm, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_16s_C1RSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image natural logarithm, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_16s_C1IRSfs_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image natural logarithm, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_16s_C3RSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image natural logarithm, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_16s_C3IRSfs_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image natural logarithm, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_16f_C1R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel image natural logarithm.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_16f_C1IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit floating point channel in place image natural logarithm.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_16f_C3R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel image natural logarithm.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_16f_C3IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit floating point channel in place image natural logarithm.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image natural logarithm.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image natural logarithm.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image natural logarithm.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLn_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image natural logarithm.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Exp


Exponential value of each pixel in an image.


Functions


NppStatus nppiExp_8u_C1RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image exponential, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_8u_C1IRSfs_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image exponential, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_8u_C3RSfs_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image exponential, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_8u_C3IRSfs_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image exponential, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_16u_C1RSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image exponential, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_16u_C1IRSfs_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image exponential, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_16u_C3RSfs_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image exponential, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_16u_C3IRSfs_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image exponential, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_16s_C1RSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image exponential, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_16s_C1IRSfs_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image exponential, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_16s_C3RSfs_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image exponential, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_16s_C3IRSfs_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, int nScaleFactor, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image exponential, scale by \(2^(-nScaleFactor)\), then clamp to saturated value.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nScaleFactor – Integer Result Scaling.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image exponential.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit floating point channel in place image exponential.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel image exponential.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiExp_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit floating point channel in place image exponential.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


## Logical Operations


### Logical Operations


The set of image processing logical operations available in the library.


### AndC


Pixel by pixel logical and of an image with a constant.


Functions


NppStatus nppiAndC_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image logical and with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_8u_C1IR_Ctx(const Npp8u nConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image logical and with constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image logical and with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_8u_C3IR_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image logical and with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical and with constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_8u_AC4IR_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical and with constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[4], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical and with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_8u_C4IR_Ctx(const Npp8u aConstants[4], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical and with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u nConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image logical and with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_16u_C1IR_Ctx(const Npp16u nConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image logical and with constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image logical and with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_16u_C3IR_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image logical and with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image logical and with constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_16u_AC4IR_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image logical and with constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[4], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image logical and with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_16u_C4IR_Ctx(const Npp16u aConstants[4], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image logical and with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s nConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image logical and with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_32s_C1IR_Ctx(const Npp32s nConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image logical and with constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_32s_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image logical and with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_32s_C3IR_Ctx(const Npp32s aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image logical and with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_32s_AC4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image logical and with constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_32s_AC4IR_Ctx(const Npp32s aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image logical and with constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_32s_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[4], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image logical and with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAndC_32s_C4IR_Ctx(const Npp32s aConstants[4], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image logical and with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### OrC


Pixel by pixel logical or of an image with a constant.


Functions


NppStatus nppiOrC_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image logical or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_8u_C1IR_Ctx(const Npp8u nConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image logical or with constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image logical or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_8u_C3IR_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image logical or with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical or with constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_8u_AC4IR_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical or with constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[4], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_8u_C4IR_Ctx(const Npp8u aConstants[4], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical or with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u nConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image logical or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_16u_C1IR_Ctx(const Npp16u nConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image logical or with constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image logical or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_16u_C3IR_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image logical or with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image logical or with constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_16u_AC4IR_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image logical or with constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[4], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image logical or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_16u_C4IR_Ctx(const Npp16u aConstants[4], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image logical or with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s nConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image logical or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_32s_C1IR_Ctx(const Npp32s nConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image logical or with constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_32s_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image logical or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_32s_C3IR_Ctx(const Npp32s aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image logical or with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_32s_AC4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image logical or with constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_32s_AC4IR_Ctx(const Npp32s aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image logical or with constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_32s_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[4], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image logical or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOrC_32s_C4IR_Ctx(const Npp32s aConstants[4], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image logical or with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### XorC


Pixel by pixel logical exclusive or of an image with a constant.


Functions


NppStatus nppiXorC_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image logical exclusive or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_8u_C1IR_Ctx(const Npp8u nConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image logical exclusive or with constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image logical exclusive or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_8u_C3IR_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image logical exclusive or with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical exclusive or with constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_8u_AC4IR_Ctx(const Npp8u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical exclusive or with constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u aConstants[4], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical exclusive or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_8u_C4IR_Ctx(const Npp8u aConstants[4], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical exclusive or with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u nConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image logical exclusive or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_16u_C1IR_Ctx(const Npp16u nConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image logical exclusive or with constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image logical exclusive or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_16u_C3IR_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image logical exclusive or with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image logical exclusive or with constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_16u_AC4IR_Ctx(const Npp16u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image logical exclusive or with constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u aConstants[4], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image logical exclusive or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_16u_C4IR_Ctx(const Npp16u aConstants[4], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image logical exclusive or with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s nConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image logical exclusive or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_32s_C1IR_Ctx(const Npp32s nConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image logical exclusive or with constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_32s_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image logical exclusive or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_32s_C3IR_Ctx(const Npp32s aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image logical exclusive or with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_32s_AC4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image logical exclusive or with constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_32s_AC4IR_Ctx(const Npp32s aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image logical exclusive or with constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_32s_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s aConstants[4], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image logical exclusive or with constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXorC_32s_C4IR_Ctx(const Npp32s aConstants[4], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image logical exclusive or with constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### RShiftC


Pixel by pixel right shift of an image by a constant value.


Functions


NppStatus nppiRShiftC_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp32u nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8u_C1IR_Ctx(const Npp32u nConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image right shift by constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8u_C3IR_Ctx(const Npp32u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image right shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image right shift by constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8u_AC4IR_Ctx(const Npp32u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image right shift by constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp32u aConstants[4], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8u_C4IR_Ctx(const Npp32u aConstants[4], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image right shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8s_C1R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp32u nConstant, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit signed char channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8s_C1IR_Ctx(const Npp32u nConstant, Npp8s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit signed char channel in place image right shift by constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8s_C3R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp8s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit signed char channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8s_C3IR_Ctx(const Npp32u aConstants[3], Npp8s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit signed char channel in place image right shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8s_AC4R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp8s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit signed char channel image right shift by constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8s_AC4IR_Ctx(const Npp32u aConstants[3], Npp8s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit signed char channel in place image right shift by constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8s_C4R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp32u aConstants[4], Npp8s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit signed char channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_8s_C4IR_Ctx(const Npp32u aConstants[4], Npp8s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit signed char channel in place image right shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp32u nConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16u_C1IR_Ctx(const Npp32u nConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image right shift by constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16u_C3IR_Ctx(const Npp32u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image right shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image right shift by constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16u_AC4IR_Ctx(const Npp32u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image right shift by constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp32u aConstants[4], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16u_C4IR_Ctx(const Npp32u aConstants[4], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image right shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp32u nConstant, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16s_C1IR_Ctx(const Npp32u nConstant, Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit signed short channel in place image right shift by constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16s_C3R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16s_C3IR_Ctx(const Npp32u aConstants[3], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit signed short channel in place image right shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16s_AC4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image right shift by constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16s_AC4IR_Ctx(const Npp32u aConstants[3], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image right shift by constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16s_C4R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp32u aConstants[4], Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_16s_C4IR_Ctx(const Npp32u aConstants[4], Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit signed short channel in place image right shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32u nConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_32s_C1IR_Ctx(const Npp32u nConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image right shift by constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_32s_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_32s_C3IR_Ctx(const Npp32u aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image right shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_32s_AC4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image right shift by constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_32s_AC4IR_Ctx(const Npp32u aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image right shift by constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_32s_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32u aConstants[4], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image right shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiRShiftC_32s_C4IR_Ctx(const Npp32u aConstants[4], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image right shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### LShiftC


Pixel by pixel left shift of an image by a constant value.


Functions


NppStatus nppiLShiftC_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp32u nConstant, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image left shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_8u_C1IR_Ctx(const Npp32u nConstant, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image left shift by constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image left shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_8u_C3IR_Ctx(const Npp32u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image left shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image left shift by constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_8u_AC4IR_Ctx(const Npp32u aConstants[3], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image left shift by constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp32u aConstants[4], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image left shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_8u_C4IR_Ctx(const Npp32u aConstants[4], Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image left shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp32u nConstant, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image left shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_16u_C1IR_Ctx(const Npp32u nConstant, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image left shift by constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image left shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_16u_C3IR_Ctx(const Npp32u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image left shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image left shift by constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_16u_AC4IR_Ctx(const Npp32u aConstants[3], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image left shift by constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp32u aConstants[4], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image left shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_16u_C4IR_Ctx(const Npp32u aConstants[4], Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image left shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32u nConstant, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image left shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nConstant – Constant.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_32s_C1IR_Ctx(const Npp32u nConstant, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image left shift by constant.

Parameters

nConstant – Constant.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_32s_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image left shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_32s_C3IR_Ctx(const Npp32u aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image left shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_32s_AC4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32u aConstants[3], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image left shift by constant with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_32s_AC4IR_Ctx(const Npp32u aConstants[3], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image left shift by constant with unmodified alpha.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_32s_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32u aConstants[4], Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image left shift by constant.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
aConstants – fixed size array of constant values, one per channel.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiLShiftC_32s_C4IR_Ctx(const Npp32u aConstants[4], Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image left shift by constant.

Parameters

aConstants – fixed size array of constant values, one per channel.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### And


Pixel by pixel logical and of images.


Functions


NppStatus nppiAnd_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image logical and.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_8u_C1IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image logical and.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image logical and.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_8u_C3IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image logical and.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical and with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_8u_AC4IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical and with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical and.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_8u_C4IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical and.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image logical and.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_16u_C1IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image logical and.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image logical and.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_16u_C3IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image logical and.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image logical and with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_16u_AC4IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image logical and with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image logical and.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_16u_C4IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image logical and.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image logical and.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_32s_C1IR_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image logical and.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_32s_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image logical and.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_32s_C3IR_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image logical and.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_32s_AC4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image logical and with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_32s_AC4IR_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image logical and with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_32s_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image logical and.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAnd_32s_C4IR_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image logical and.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Or


Pixel by pixel logical or of images.


Functions


NppStatus nppiOr_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image logical or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_8u_C1IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image logical or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image logical or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_8u_C3IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image logical or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical or with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_8u_AC4IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical or with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_8u_C4IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image logical or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_16u_C1IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image logical or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image logical or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_16u_C3IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image logical or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image logical or with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_16u_AC4IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image logical or with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image logical or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_16u_C4IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image logical or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image logical or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_32s_C1IR_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image logical or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_32s_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image logical or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_32s_C3IR_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image logical or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_32s_AC4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image logical or with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_32s_AC4IR_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image logical or with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_32s_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image logical or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiOr_32s_C4IR_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image logical or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Xor


Pixel by pixel logical exclusive or of images.


Functions


NppStatus nppiXor_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image logical exclusive or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_8u_C1IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image logical exclusive or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image logical exclusive or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_8u_C3IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image logical exclusive or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical exclusive or with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_8u_AC4IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical exclusive or with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical exclusive or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_8u_C4IR_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical exclusive or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image logical exclusive or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_16u_C1IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image logical exclusive or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image logical exclusive or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_16u_C3IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image logical exclusive or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image logical exclusive or with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_16u_AC4IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image logical exclusive or with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image logical exclusive or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_16u_C4IR_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image logical exclusive or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image logical exclusive or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_32s_C1IR_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel in place image logical exclusive or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_32s_C3R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel image logical exclusive or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_32s_C3IR_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 32-bit signed integer channel in place image logical exclusive or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_32s_AC4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image logical exclusive or with unmodified alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_32s_AC4IR_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image logical exclusive or with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_32s_C4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image logical exclusive or.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiXor_32s_C4IR_Ctx(const Npp32s *pSrc, int nSrcStep, Npp32s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel in place image logical exclusive or.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### Not


Pixel by pixel logical not of image.


Functions


NppStatus nppiNot_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image logical not.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiNot_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image logical not.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiNot_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image logical not.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiNot_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image logical not.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiNot_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical not with unmodified alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiNot_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical not with unmodified alpha.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiNot_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image logical not.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiNot_8u_C4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image logical not.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


## Image Alpha Composition Operations


### AlphaCompC


Composite two images using constant alpha values.


Functions


NppStatus nppiAlphaCompC_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, Npp8u nAlpha1, const Npp8u *pSrc2, int nSrc2Step, Npp8u nAlpha2, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image composition using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaCompC_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, Npp8u nAlpha1, const Npp8u *pSrc2, int nSrc2Step, Npp8u nAlpha2, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image composition using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaCompC_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, Npp8u nAlpha1, const Npp8u *pSrc2, int nSrc2Step, Npp8u nAlpha2, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image composition using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaCompC_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, Npp8u nAlpha1, const Npp8u *pSrc2, int nSrc2Step, Npp8u nAlpha2, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image composition with alpha using constant source alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaCompC_8s_C1R_Ctx(const Npp8s *pSrc1, int nSrc1Step, Npp8s nAlpha1, const Npp8s *pSrc2, int nSrc2Step, Npp8s nAlpha2, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 8-bit signed char channel image composition using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaCompC_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, Npp16u nAlpha1, const Npp16u *pSrc2, int nSrc2Step, Npp16u nAlpha2, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image composition using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaCompC_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, Npp16u nAlpha1, const Npp16u *pSrc2, int nSrc2Step, Npp16u nAlpha2, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image composition using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaCompC_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, Npp16u nAlpha1, const Npp16u *pSrc2, int nSrc2Step, Npp16u nAlpha2, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image composition using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaCompC_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, Npp16u nAlpha1, const Npp16u *pSrc2, int nSrc2Step, Npp16u nAlpha2, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image composition with alpha using constant source alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaCompC_16s_C1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, Npp16s nAlpha1, const Npp16s *pSrc2, int nSrc2Step, Npp16s nAlpha2, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image composition using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaCompC_32u_C1R_Ctx(const Npp32u *pSrc1, int nSrc1Step, Npp32u nAlpha1, const Npp32u *pSrc2, int nSrc2Step, Npp32u nAlpha2, Npp32u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 32-bit unsigned integer channel image composition using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaCompC_32s_C1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, Npp32s nAlpha1, const Npp32s *pSrc2, int nSrc2Step, Npp32s nAlpha2, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image composition using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaCompC_32f_C1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, Npp32f nAlpha1, const Npp32f *pSrc2, int nSrc2Step, Npp32f nAlpha2, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image composition using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0.0 - 1.0).
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
nAlpha2 – Image alpha opacity (0.0 - 1.0).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


Premultiplies pixels of an image using a constant alpha value.


Functions


NppStatus nppiAlphaPremulC_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, Npp8u nAlpha1, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image premultiplication using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_8u_C1IR_Ctx(Npp8u nAlpha1, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel in place image premultiplication using constant alpha.

Parameters

nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, Npp8u nAlpha1, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel image premultiplication using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_8u_C3IR_Ctx(Npp8u nAlpha1, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 8-bit unsigned char channel in place image premultiplication using constant alpha.

Parameters

nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, Npp8u nAlpha1, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image premultiplication using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_8u_C4IR_Ctx(Npp8u nAlpha1, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image premultiplication using constant alpha.

Parameters

nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, Npp8u nAlpha1, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image premultiplication with alpha using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_8u_AC4IR_Ctx(Npp8u nAlpha1, Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image premultiplication with alpha using constant alpha.

Parameters

nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_16u_C1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, Npp16u nAlpha1, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image premultiplication using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_16u_C1IR_Ctx(Npp16u nAlpha1, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel in place image premultiplication using constant alpha.

Parameters

nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_16u_C3R_Ctx(const Npp16u *pSrc1, int nSrc1Step, Npp16u nAlpha1, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel image premultiplication using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_16u_C3IR_Ctx(Npp16u nAlpha1, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Three 16-bit unsigned short channel in place image premultiplication using constant alpha.

Parameters

nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_16u_C4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, Npp16u nAlpha1, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image premultiplication using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_16u_C4IR_Ctx(Npp16u nAlpha1, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image premultiplication using constant alpha.

Parameters

nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, Npp16u nAlpha1, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image premultiplication with alpha using constant alpha.

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremulC_16u_AC4IR_Ctx(Npp16u nAlpha1, Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image premultiplication with alpha using constant alpha.

Parameters

nAlpha1 – Image alpha opacity (0 - max channel pixel value).
pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


### AlphaComp


Composite two images using alpha opacity values contained in each image.


Functions


NppStatus nppiAlphaComp_8u_AC1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 8-bit unsigned char channel image composition using image alpha values (0 - max channel pixel value).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaComp_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image composition using image alpha values (0 - max channel pixel value).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaComp_8s_AC1R_Ctx(const Npp8s *pSrc1, int nSrc1Step, const Npp8s *pSrc2, int nSrc2Step, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 8-bit signed char channel image composition using image alpha values (0 - max channel pixel value).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaComp_16u_AC1R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 16-bit unsigned short channel image composition using image alpha values (0 - max channel pixel value).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaComp_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, const Npp16u *pSrc2, int nSrc2Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image composition using image alpha values (0 - max channel pixel value).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaComp_16s_AC1R_Ctx(const Npp16s *pSrc1, int nSrc1Step, const Npp16s *pSrc2, int nSrc2Step, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 16-bit signed short channel image composition using image alpha values (0 - max channel pixel value).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaComp_32u_AC1R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, Npp32u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 32-bit unsigned integer channel image composition using image alpha values (0 - max channel pixel value).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaComp_32u_AC4R_Ctx(const Npp32u *pSrc1, int nSrc1Step, const Npp32u *pSrc2, int nSrc2Step, Npp32u *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
Four 32-bit unsigned integer channel image composition using image alpha values (0 - max channel pixel value).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaComp_32s_AC1R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 32-bit signed integer channel image composition using image alpha values (0 - max channel pixel value).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaComp_32s_AC4R_Ctx(const Npp32s *pSrc1, int nSrc1Step, const Npp32s *pSrc2, int nSrc2Step, Npp32s *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
Four 32-bit signed integer channel image composition using image alpha values (0 - max channel pixel value).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaComp_32f_AC1R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
One 32-bit floating point channel image composition using image alpha values (0.0 - 1.0).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaComp_32f_AC4R_Ctx(const Npp32f *pSrc1, int nSrc1Step, const Npp32f *pSrc2, int nSrc2Step, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppiAlphaOp eAlphaOp, NppStreamContext nppStreamCtx)
Four 32-bit floating point channel image composition using image alpha values (0.0 - 1.0).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pSrc2 – Source-Image Pointer.
nSrc2Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eAlphaOp – alpha-blending operation.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


Premultiplies image pixels by image alpha opacity values.


Functions


NppStatus nppiAlphaPremul_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel image premultiplication with pixel alpha (0 - max channel pixel value).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremul_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 8-bit unsigned char channel in place image premultiplication with pixel alpha (0 - max channel pixel value).

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremul_16u_AC4R_Ctx(const Npp16u *pSrc1, int nSrc1Step, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel image premultiplication with pixel alpha (0 - max channel pixel value).

Parameters

pSrc1 – Source-Image Pointer.
nSrc1Step – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.


NppStatus nppiAlphaPremul_16u_AC4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Four 16-bit unsigned short channel in place image premultiplication with pixel alpha (0 - max channel pixel value).

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes.