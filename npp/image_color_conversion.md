# Image Color Conversion Functions


Routines manipulating an image’s color model and sampling format.


These functions can be found in the nppicc library. Linking to only the sub-libraries that you use can significantly save link time, application load time, and CUDA runtime startup time when using dynamic libraries.


## Color Processing Functions


Routines for performing image color manipulation.


RGBToYUVColorTwist


Normally, color twist is a 3-channel operation that takes place on RGB data.


The following functions also perform the color twist operation, but while converting between image formats: RGBToYUV420, RGBToYUV422, and RGBToNV12.


To recap color twist pixel processing: Color twist consists of applying the following formula to each image pixel using coefficients from the user supplied color twist host matrix array as follows where dst[x] and src[x] represent destination pixel and source pixel channel or plane x. The full sized coefficient matrix should be sent for all pixel channel sizes, the function will process the appropriate coefficients and channels for the corresponding pixel size.


This is how the matrix works for a RGB->YUV420/YUV422/NV12 forward transform:




```
dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3]
```


NppStatus nppiRGBToYUV420_8u_ColorTwist32f_P3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned planar RGB convertion to three channel 8-bit unsigned planar YUV 4:2:0, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV420_16u_ColorTwist32f_P3R_Ctx(const Npp16u *const pSrc[3], int aSrcStep[3], Npp16u *pDst[3], int aDstStep[3], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned planar RGB convertion to three channel 16-bit unsigned planar YUV 4:2:0, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV420_8u_ColorTwist32f_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned packed RGB convertion to three channel 8-bit unsigned planar YUV 4:2:0, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV420_16u_ColorTwist32f_C3P3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst[3], int aDstStep[3], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned packed RGB convertion to three channel 16-bit unsigned planar YUV 4:2:0, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV422_8u_ColorTwist32f_P3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned planar RGB convertion to three channel 8-bit unsigned planar YUV 4:2:2, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV422_16u_ColorTwist32f_P3R_Ctx(const Npp16u *const pSrc[3], int aSrcStep[3], Npp16u *pDst[3], int aDstStep[3], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned planar RGB convertion to three channel 16-bit unsigned planar YUV 4:2:2, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV422_8u_ColorTwist32f_C3C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned packed RGB convertion to two channel 8-bit unsigned packed YUV 4:2:2, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV422_16u_ColorTwist32f_C3C2R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned packed RGB convertion to two channel 16-bit unsigned packed YUV 4:2:2, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV422_8u_ColorTwist32f_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned packed RGB convertion to three channel 8-bit unsigned planar YUV 4:2:2, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV422_16u_ColorTwist32f_C3P3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst[3], int aDstStep[3], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned packed RGB convertion to three channel 16-bit unsigned planar YUV 4:2:2, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToNV12_8u_ColorTwist32f_C3P2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[2], int aDstStep[2], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned packed RGB convertion to two channel 8-bit unsigned planar NV12, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToNV12_16u_ColorTwist32f_C3P2R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst[2], int aDstStep[2], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned packed RGB convertion to two channel 16-bit unsigned planar NV12, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToNV12_8u_ColorTwist32f_P3P2R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst[2], int aDstStep[2], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned planar RGB convertion to two channel 8-bit unsigned planar NV12, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToNV12_16u_ColorTwist32f_P3P2R_Ctx(const Npp16u *const pSrc[3], int aSrcStep[3], Npp16u *pDst[2], int aDstStep[2], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned planar RGB convertion to two channel 16-bit unsigned planar NV12, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


YUVToRGBColorTwist


This is the inverse color twist, a 3-channel operation that takes place on YUV/NV12 data to produce RGB data, supporting the following conversions: YUV420ToRGB, YUV422ToRGB, and NV12ToRGB.


The INVERSE Color twist consists of applying the following formula to each image pixel using coefficients from the user supplied color twist host matrix array as follows where dst[x] and src[x] represent destination pixel and source pixel channel or plane x. The full sized coefficient matrix should be sent for all pixel channel sizes, the function will process the appropriate coefficients and channels for the corresponding pixel size.


This is how the matrix works for the YUV420/YUV/422/NV12->RGB INVERSE transform:


(note- do the offsets first):




```
src[0]' = src[0] + aTwist[0][3]
src[1]' = src[1] + aTwist[1][3]
src[2]' = src[2] + aTwist[2][3]
```


And then the remaining 3x3 twist matrix is applied using those modified values:




```
dst[0] = aTwist[0][0] * src[0]' + aTwist[0][1] * src[1]' + aTwist[0][2] * src[2]'
dst[1] = aTwist[1][0] * src[0]' + aTwist[1][1] * src[1]' + aTwist[1][2] * src[2]'
dst[2] = aTwist[2][0] * src[0]' + aTwist[2][1] * src[1]' + aTwist[2][2] * src[2]'
```


Since the 4th column of the matrix is the offsets (either 0 or half-max to shift the values to be positive), as they’re applied last in the forward transform (to YUV), they need to be applied FIRST in the inverse transform (back to RGB). This does mean that +-16384 has to be used for 16u images where there was a +-128 for 8u images in both forward and inverse cases.


NppStatus nppiYUV420ToRGB_8u_ColorTwist32f_P3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned planar YUV4:2:0 convertion to three channel 8-bit unsigned planar RGB, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV420ToRGB_16u_ColorTwist32f_P3R_Ctx(const Npp16u *const pSrc[3], int aSrcStep[3], Npp16u *pDst[3], int aDstStep[3], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned planar YUV4:2:0 convertion to three channel 16-bit unsigned planar RGB, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV420ToRGB_8u_ColorTwist32f_P3C3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned planar YUV4:2:0 convertion to three channel 8-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV420ToRGB_16u_ColorTwist32f_P3C3R_Ctx(const Npp16u *const pSrc[3], int aSrcStep[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned planar YUV4:2:0 convertion to three channel 16-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV420ToRGB_8u_ColorTwist32f_P3C4R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned planar YUV4:2:0 convertion to four channel 8-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic, with constant alpha (0xFF).

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV420ToRGB_16u_ColorTwist32f_P3C4R_Ctx(const Npp16u *const pSrc[3], int aSrcStep[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned planar YUV4:2:0 convertion to four channel 16-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic, with constant alpha (0xFFFF).

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV420ToRGB_8u_ColorTwist32f_P3AC4R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], const Npp8u nAlpha, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned planar YUV4:2:0 convertion to four channel 8-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic, with user set alpha.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nAlpha – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV420ToRGB_16u_ColorTwist32f_P3AC4R_Ctx(const Npp16u *const pSrc[3], int aSrcStep[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], const Npp16u nAlpha, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned planar YUV4:2:0 convertion to four channel 16-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic, with user set alpha.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nAlpha – 16-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV422ToRGB_8u_ColorTwist32f_C2C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Two channel 8-bit unsigned packed YUV4:2:2 convertion to three channel 8-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV422ToRGB_16u_ColorTwist32f_C2C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Two channel 16-bit unsigned packed YUV4:2:2 convertion to three channel 16-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV422ToRGB_8u_ColorTwist32f_P3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned planar YUV4:2:2 convertion to three channel 8-bit unsigned planar RGB, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV422ToRGB_16u_ColorTwist32f_P3R_Ctx(const Npp16u *const pSrc[3], int aSrcStep[3], Npp16u *pDst[3], int aDstStep[3], NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned planar YUV4:2:2 convertion to three channel 16-bit unsigned planar RGB, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV422ToRGB_8u_ColorTwist32f_P3C3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned planar YUV4:2:2 convertion to three channel 8-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV422ToRGB_16u_ColorTwist32f_P3C3R_Ctx(const Npp16u *const pSrc[3], int aSrcStep[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned planar YUV4:2:2 convertion to three channel 8-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV422ToRGB_8u_ColorTwist32f_P3AC4R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], const Npp8u nAlpha, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned planar YUV4:2:2 convertion to three channel 8-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic, with user set alpha.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nAlpha – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV422ToRGB_16u_ColorTwist32f_P3AC4R_Ctx(const Npp16u *const pSrc[3], int aSrcStep[3], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], const Npp16u nAlpha, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned planar YUV4:2:2 convertion to three channel 16-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic, with user set alpha.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nAlpha – 16-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiNV12ToRGB_8u_ColorTwist32f_P2C3R_Ctx(const Npp8u *const pSrc[2], int aSrcStep[2], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Two channel 8-bit unsigned planar NV12 convertion to three channel 8-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiNV12ToRGB_16u_ColorTwist32f_P2C3R_Ctx(const Npp16u *const pSrc[2], int aSrcStep[2], Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
Two channel 16-bit unsigned planar NV12 convertion to three channel 16-bit unsigned packed RGB, using a Color Twist to compute the exact color space arithmetic.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Color To Gray Conversion


Routines for converting color images to grayscale.


RGBToGray


RGB to CCIR601 Gray conversion.


Here is how NPP converts gamma corrected RGB to CCIR601 Gray.




```
nGray =  0.299F * R + 0.587F * G + 0.114F * B;
```


NppStatus nppiRGBToGray_8u_C3C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 1 channel 8-bit unsigned packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToGray_8u_AC4C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGB with alpha to 1 channel 8-bit unsigned packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToGray_16u_C3C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned packed RGB to 1 channel 16-bit unsigned packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToGray_16u_AC4C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned packed RGB with alpha to 1 channel 16-bit unsigned packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToGray_16s_C3C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 16-bit signed packed RGB to 1 channel 16-bit signed packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToGray_16s_AC4C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 16-bit signed packed RGB with alpha to 1 channel 16-bit signed packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToGray_32f_C3C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point packed RGB to 1 channel 32-bit floating point packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToGray_32f_AC4C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point packed RGB with alpha to 1 channel 32-bit floating point packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


ColorToGray


RGB Color to Gray conversion using user supplied conversion coefficients.


Here is how NPP converts gamma corrected RGB Color to Gray using user supplied conversion coefficients.




```
nGray =  aCoeffs[0] * R + aCoeffs[1] * G + aCoeffs[2] * B;
```




For the C4C1R versions of the functions the calculations are as follows.


For BGRA or other formats with alpha just rearrange the coefficients accordingly.




```
nGray =  aCoeffs[0] * R + aCoeffs[1] * G + aCoeffs[2] * B + aCoeffs[3] * A;
```


NppStatus nppiColorToGray_8u_C3C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aCoeffs[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 1 channel 8-bit unsigned packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aCoeffs – fixed size array of constant floating point conversion coefficient values, one per color channel.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorToGray_8u_AC4C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aCoeffs[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGB with alpha to 1 channel 8-bit unsigned packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aCoeffs – fixed size array of constant floating point conversion coefficient values, one per color channel.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorToGray_8u_C4C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aCoeffs[4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGBA to 1 channel 8-bit unsigned packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aCoeffs – fixed size array of constant floating point conversion coefficient values, one per color channel.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorToGray_16u_C3C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aCoeffs[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned packed RGB to 1 channel 16-bit unsigned packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aCoeffs – fixed size array of constant floating point conversion coefficient values, one per color channel.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorToGray_16u_AC4C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aCoeffs[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned packed RGB with alpha to 1 channel 16-bit unsigned packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aCoeffs – fixed size array of constant floating point conversion coefficient values, one per color channel.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorToGray_16u_C4C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aCoeffs[4], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned packed RGBA to 1 channel 16-bit unsigned packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aCoeffs – fixed size array of constant floating point conversion coefficient values, one per color channel.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorToGray_16s_C3C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aCoeffs[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed packed RGB to 1 channel 16-bit signed packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aCoeffs – fixed size array of constant floating point conversion coefficient values, one per color channel.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorToGray_16s_AC4C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aCoeffs[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed packed RGB with alpha to 1 channel 16-bit signed packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aCoeffs – fixed size array of constant floating point conversion coefficient values, one per color channel.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorToGray_16s_C4C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aCoeffs[4], NppStreamContext nppStreamCtx)
4 channel 16-bit signed packed RGBA to 1 channel 16-bit signed packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aCoeffs – fixed size array of constant floating point conversion coefficient values, one per color channel.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorToGray_32f_C3C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aCoeffs[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point packed RGB to 1 channel 32-bit floating point packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aCoeffs – fixed size array of constant floating point conversion coefficient values, one per color channel.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorToGray_32f_AC4C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aCoeffs[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point packed RGB with alpha to 1 channel 32-bit floating point packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aCoeffs – fixed size array of constant floating point conversion coefficient values, one per color channel.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorToGray_32f_C4C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aCoeffs[4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point packed RGBA to 1 channel 32-bit floating point packed Gray conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aCoeffs – fixed size array of constant floating point conversion coefficient values, one per color channel.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


GradientColorToGray


RGB Color to Gray Gradient conversion using user selected gradient distance method.


NppStatus nppiGradientColorToGray_8u_C3C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppiNorm eNorm, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 1 channel 8-bit unsigned packed Gray Gradient conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eNorm – Gradient distance method to use.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGradientColorToGray_16u_C3C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, NppiNorm eNorm, NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned packed RGB to 1 channel 16-bit unsigned packed Gray Gradient conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eNorm – Gradient distance method to use.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGradientColorToGray_16s_C3C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, NppiNorm eNorm, NppStreamContext nppStreamCtx)
3 channel 16-bit signed packed RGB to 1 channel 16-bit signed packed Gray Gradient conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eNorm – Gradient distance method to use.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGradientColorToGray_32f_C3C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, NppiNorm eNorm, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point packed RGB to 1 channel 32-bit floating point packed Gray Gradient conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
eNorm – Gradient distance method to use.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Color Debayer


Grayscale Color Filter Array to RGB Color Debayer conversion.


Generates one RGB color pixel for every grayscale source pixel. Source and destination images must have even width and height. Missing pixel colors are generated using bilinear interpolation with chroma correlation of generated green values (eInterpolation MUST be set to 0). eGrid allows the user to specify the Bayer grid registration position at source image location oSrcROI.x, oSrcROI.y relative to pSrc. Possible registration positions are:




```
NPPI_BAYER_BGGR  NPPI_BAYER_RGGB  NPPI_BAYER_GBRG  NPPI_BAYER_GRBG

      B G              R G              G B              G R
      G R              G B              R G              B G
```


If it becomes necessary to access source pixels outside source image then the source image borders are mirrored.


Here is how the algorithm works. R, G, and B base pixels from the source image are used unmodified. To generate R values for those G pixels, the average of R(x - 1, y) and R(x + 1, y) or R(x, y - 1) and R(x, y + 1) is used depending on whether the left and right or top and bottom pixels are R base pixels. To generate B values for those G pixels, the same algorithm is used using nearest B values. For an R base pixel, if there are no B values in the upper, lower, left, or right adjacent pixels then B is the average of B values in the 4 diagonal (G base) pixels. The same algorithm is used using R values to generate the R value of a B base pixel. Chroma correlation is applied to generated G values only, for a B base pixel G(x - 1, y) and G(x + 1, y) are averaged or G(x, y - 1) and G(x, y + 1) are averaged depending on whether the absolute difference between B(x, y) and the average of B(x - 2, y) and B(x + 2, y) is smaller than the absolute difference between B(x, y) and the average of B(x, y - 2) and B(x, y + 2). For an R base pixel the same algorithm is used testing against the surrounding R values at those offsets. If the horizontal and vertical differences are the same at one of those pixels then the average of the four left, right, upper and lower G values is used instead.


Functions


NppStatus nppiCFAToRGB_8u_C1C3R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiRect oSrcROI, Npp8u *pDst, int nDstStep, NppiBayerGridPosition eGrid, NppiInterpolationMode eInterpolation, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned packed CFA grayscale Bayer pattern to 3 channel 8-bit unsigned packed RGB conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
oSrcSize – full source image width and height relative to pSrc.
oSrcROI – rectangle specifying starting source image pixel x and y location relative to pSrc and ROI width and height.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
eGrid – enumeration value specifying bayer grid registration position at location oSrcROI.x, oSrcROI.y relative to pSrc.
eInterpolation – MUST be NPPI_INTER_UNDEFINED
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiCFAToRGBA_8u_C1AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiRect oSrcROI, Npp8u *pDst, int nDstStep, NppiBayerGridPosition eGrid, NppiInterpolationMode eInterpolation, Npp8u nAlpha, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned packed CFA grayscale Bayer pattern to 4 channel 8-bit unsigned packed RGB conversion with alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
oSrcSize – full source image width and height relative to pSrc.
oSrcROI – rectangle specifying starting source image pixel x and y location relative to pSrc and ROI width and height.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
eGrid – enumeration value specifying bayer grid registration position at location oSrcROI.x, oSrcROI.y relative to pSrc.
eInterpolation – MUST be NPPI_INTER_UNDEFINED
nAlpha – constant alpha value to be written to each destination pixel
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiCFAToRGB_16u_C1C3R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiRect oSrcROI, Npp16u *pDst, int nDstStep, NppiBayerGridPosition eGrid, NppiInterpolationMode eInterpolation, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned packed CFA grayscale Bayer pattern to 3 channel 16-bit unsigned packed RGB conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
oSrcSize – full source image width and height relative to pSrc.
oSrcROI – rectangle specifying starting source image pixel x and y location relative to pSrc and ROI width and height.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
eGrid – enumeration value specifying bayer grid registration position at location oSrcROI.x, oSrcROI.y relative to pSrc.
eInterpolation – MUST be NPPI_INTER_UNDEFINED
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiCFAToRGBA_16u_C1AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiRect oSrcROI, Npp16u *pDst, int nDstStep, NppiBayerGridPosition eGrid, NppiInterpolationMode eInterpolation, Npp16u nAlpha, NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned packed CFA grayscale Bayer pattern to 4 channel 16-bit unsigned packed RGB conversion with alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
oSrcSize – full source image width and height relative to pSrc.
oSrcROI – rectangle specifying starting source image pixel x and y location relative to pSrc and ROI width and height.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
eGrid – enumeration value specifying bayer grid registration position at location oSrcROI.x, oSrcROI.y relative to pSrc.
eInterpolation – MUST be NPPI_INTER_UNDEFINED
nAlpha – constant alpha value to be written to each destination pixel
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiCFAToRGB_32u_C1C3R_Ctx(const Npp32u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiRect oSrcROI, Npp32u *pDst, int nDstStep, NppiBayerGridPosition eGrid, NppiInterpolationMode eInterpolation, NppStreamContext nppStreamCtx)
1 channel 32-bit unsigned packed CFA grayscale Bayer pattern to 3 channel 32-bit unsigned packed RGB conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
oSrcSize – full source image width and height relative to pSrc.
oSrcROI – rectangle specifying starting source image pixel x and y location relative to pSrc and ROI width and height.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
eGrid – enumeration value specifying bayer grid registration position at location oSrcROI.x, oSrcROI.y relative to pSrc.
eInterpolation – MUST be NPPI_INTER_UNDEFINED
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiCFAToRGBA_32u_C1AC4R_Ctx(const Npp32u *pSrc, int nSrcStep, NppiSize oSrcSize, NppiRect oSrcROI, Npp32u *pDst, int nDstStep, NppiBayerGridPosition eGrid, NppiInterpolationMode eInterpolation, Npp32u nAlpha, NppStreamContext nppStreamCtx)
1 channel 32-bit unsigned packed CFA grayscale Bayer pattern to 4 channel 32-bit unsigned packed RGB conversion with alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
oSrcSize – full source image width and height relative to pSrc.
oSrcROI – rectangle specifying starting source image pixel x and y location relative to pSrc and ROI width and height.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
eGrid – enumeration value specifying bayer grid registration position at location oSrcROI.x, oSrcROI.y relative to pSrc.
eInterpolation – MUST be NPPI_INTER_UNDEFINED
nAlpha – constant alpha value to be written to each destination pixel
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Color Gamma Correction


Routines for correcting image color gamma.


GammaFwd


Forward gamma correction.


NppStatus nppiGammaFwd_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed color not in place forward gamma correction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGammaFwd_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed color in place forward gamma correction.

Parameters

pSrcDst – in place packed pixel image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGammaFwd_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed color with alpha not in place forward gamma correction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGammaFwd_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed color with alpha in place forward gamma correction.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGammaFwd_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar color not in place forward gamma correction.

Parameters

pSrc – source planar pixel format image pointer array.
nSrcStep – source planar pixel format image line step.
pDst – destination planar pixel format image pointer array.
nDstStep – destination planar pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGammaFwd_8u_IP3R_Ctx(Npp8u *const pSrcDst[3], int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar color in place forward gamma correction.

Parameters

pSrcDst – in place planar pixel format image pointer array.
nSrcDstStep – in place planar pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


GammaInv


Inverse gamma correction.


NppStatus nppiGammaInv_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed color not in place inverse gamma correction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGammaInv_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed color in place inverse gamma correction.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGammaInv_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed color with alpha not in place inverse gamma correction.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGammaInv_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed color with alpha in place inverse gamma correction.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGammaInv_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar color not in place inverse gamma correction.

Parameters

pSrc – source planar pixel format image pointer array.
nSrcStep – source planar pixel format image line step.
pDst – destination planar pixel format image pointer array.
nDstStep – destination planar pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiGammaInv_8u_IP3R_Ctx(Npp8u *const pSrcDst[3], int nSrcDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar color in place inverse gamma correction.

Parameters

pSrcDst – in place planar pixel format image pointer array.
nSrcDstStep – in place planar pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### Complement Color Key


Routines for performing complement color key replacement.


CompColorKey


Complement color key replacement.


NppStatus nppiCompColorKey_8u_C1R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nColorKeyConst, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned packed color complement color key replacement of source image 1 by source image 2.

Parameters

pSrc1 – source1 packed pixel format image pointer.
nSrc1Step – source1 packed pixel format image line step.
pSrc2 – source2 packed pixel format image pointer.
nSrc2Step – source2 packed pixel format image line step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nColorKeyConst – color key constant
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiCompColorKey_8u_C3R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nColorKeyConst[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed color complement color key replacement of source image 1 by source image 2.

Parameters

pSrc1 – source1 packed pixel format image pointer.
nSrc1Step – source1 packed pixel format image line step.
pSrc2 – source2 packed pixel format image pointer.
nSrc2Step – source2 packed pixel format image line step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nColorKeyConst – color key constant array
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiCompColorKey_8u_C4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, const Npp8u *pSrc2, int nSrc2Step, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nColorKeyConst[4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed color complement color key replacement of source image 1 by source image 2.

Parameters

pSrc1 – source1 packed pixel format image pointer.
nSrc1Step – source1 packed pixel format image line step.
pSrc2 – source2 packed pixel format image pointer.
nSrc2Step – source2 packed pixel format image line step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nColorKeyConst – color key constant array
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiAlphaCompColorKey_8u_AC4R_Ctx(const Npp8u *pSrc1, int nSrc1Step, Npp8u nAlpha1, const Npp8u *pSrc2, int nSrc2Step, Npp8u nAlpha2, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nColorKeyConst[4], NppiAlphaOp nppAlphaOp, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed color complement color key replacement of source image 1 by source image 2 with alpha blending.

Parameters

pSrc1 – source1 packed pixel format image pointer.
nSrc1Step – source1 packed pixel format image line step.
nAlpha1 – source1 image alpha opacity (0 - max channel pixel value).
pSrc2 – source2 packed pixel format image pointer.
nSrc2Step – source2 packed pixel format image line step.
nAlpha2 – source2 image alpha opacity (0 - max channel pixel value).
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nColorKeyConst – color key constant array
nppAlphaOp – NppiAlphaOp alpha compositing operation selector (excluding premul ops).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### ColorTwist


Routines for converting between various image color models using user supplied matrix coefficients.


ColorTwist


Perform color twist pixel processing.


Color twist consists of applying the following formula to each image pixel using coefficients from the user supplied color twist host matrix array as follows where dst[x] and src[x] represent destination pixel and source pixel channel or plane x. The full sized coefficient matrix should be sent for all pixel channel sizes, the function will process the appropriate coefficients and channels for the corresponding pixel size.




```
dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3]
```


NppStatus nppiColorTwist32f_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8u_C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8u_C2IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned color twist, with alpha copy.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is copied unmodified from the source pixel to the destination pixel.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8u_C4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned in place color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is unmodified.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned in place color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32fC_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[4][4], const Npp32f aConstants[4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned color twist with 4x4 matrix and constant vector addition.
An input 4x4 color twist matrix with floating-point coefficient values with an additional constant vector addition is applied within ROI. For this particular version of the function the result is generated as shown below.

dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3] * src[3] + aConstants[0]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3] * src[3] + aConstants[1]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3] * src[3] + aConstants[2]
dst[3] = aTwist[3][0] * src[0] + aTwist[3][1] * src[1] + aTwist[3][2] * src[2] + aTwist[3][3] * src[3] + aConstants[3]

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
aConstants – fixed size array of constant values, one per channel..
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32fC_8u_C4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[4][4], const Npp32f aConstants[4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned in place color twist with 4x4 matrix and an additional constant vector addition.
An input 4x4 color twist matrix with floating-point coefficient values with an additional constant vector addition is applied within ROI. For this particular version of the function the result is generated as shown below.

dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3] * src[3] + aConstants[0]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3] * src[3] + aConstants[1]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3] * src[3] + aConstants[2]
dst[3] = aTwist[3][0] * src[0] + aTwist[3][1] * src[1] + aTwist[3][2] * src[2] + aTwist[3][3] * src[3] + aConstants[3]

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
aConstants – fixed size array of constant values, one per channel..
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *const pDst[3], int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8u_IP3R_Ctx(Npp8u *const pSrcDst[3], int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place planar pixel format image pointer array, one pointer per plane.
nSrcDstStep – in place planar pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8s_C1R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
1 channel 8-bit signed color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8s_C1IR_Ctx(Npp8s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
1 channel 8-bit signed in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8s_C2R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
2 channel 8-bit signed color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8s_C2IR_Ctx(Npp8s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
2 channel 8-bit signed in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8s_C3R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 8-bit signed color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8s_C3IR_Ctx(Npp8s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 8-bit signed in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8s_C4R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 8-bit signed color twist, with alpha copy.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is copied unmodified from the source pixel to the destination pixel.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8s_C4IR_Ctx(Npp8s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 8-bit signed in place color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is unmodified.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8s_AC4R_Ctx(const Npp8s *pSrc, int nSrcStep, Npp8s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 8-bit signed color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8s_AC4IR_Ctx(Npp8s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 8-bit signed in place color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8s_P3R_Ctx(const Npp8s *const pSrc[3], int nSrcStep, Npp8s *const pDst[3], int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 8-bit signed planar color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_8s_IP3R_Ctx(Npp8s *const pSrcDst[3], int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 8-bit signed planar in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place planar pixel format image pointer array, one pointer per plane.
nSrcDstStep – in place planar pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
1 channel 16-bit unsigned in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16u_C2R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
2 channel 16-bit unsigned color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16u_C2IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
2 channel 16-bit unsigned in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16u_AC4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned in place color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16u_P3R_Ctx(const Npp16u *const pSrc[3], int nSrcStep, Npp16u *const pDst[3], int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned planar color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16u_IP3R_Ctx(Npp16u *const pSrcDst[3], int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned planar in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place planar pixel format image pointer array, one pointer per plane.
nSrcDstStep – in place planar pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
1 channel 16-bit signed color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16s_C1IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
1 channel 16-bit signed in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16s_C2R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
2 channel 16-bit signed color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16s_C2IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
2 channel 16-bit signed in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 16-bit signed color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16s_C3IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 16-bit signed in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 16-bit signed color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16s_AC4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 16-bit signed in place color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16s_P3R_Ctx(const Npp16s *const pSrc[3], int nSrcStep, Npp16s *const pDst[3], int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 16-bit signed planar color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16s_IP3R_Ctx(Npp16s *const pSrcDst[3], int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 16-bit signed planar in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place planar pixel format image pointer array, one pointer per plane.
nSrcDstStep – in place planar pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16f_C1R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
1 channel 16-bit floating point color twist.
An input color twist matrix with 32-bit floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16f_C1IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
1 channel 16-bit floating point in place color twist.
An input color twist matrix with 32-bit floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16f_C2R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
2 channel 16-bit floating point color twist.
An input color twist matrix with 32-bit floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16f_C2IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
2 channel 16-bit floating point in place color twist.
An input color twist matrix with 32-bit floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16f_C3R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 16-bit floating point color twist.
An input color twist matrix with 32-bit floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16f_C3IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 16-bit floating point in place color twist.
An input color twist matrix with 32-bit floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16f_C4R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 16-bit floating point color twist, with alpha copy.
An input color twist matrix with 32-bit floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is copied unmodified from the source pixel to the destination pixel.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32f_16f_C4IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 16-bit floating point in place color twist, not affecting Alpha.
An input color twist matrix with 32-bit floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is not modified.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32fC_16f_C4R_Ctx(const Npp16f *pSrc, int nSrcStep, Npp16f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[4][4], const Npp32f aConstants[4], NppStreamContext nppStreamCtx)
4 channel 16-bit floating point color twist with 4x4 matrix and constant vector addition.
An input 4x4 color twist matrix with 32-bit floating-point coefficient values with an additional 32-bit floating point constant vector addition is applied within ROI. For this particular version of the function the result is generated as shown below.

dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3] * src[3] + aConstants[0]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3] * src[3] + aConstants[1]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3] * src[3] + aConstants[2]
dst[3] = aTwist[3][0] * src[0] + aTwist[3][1] * src[1] + aTwist[3][2] * src[2] + aTwist[3][3] * src[3] + aConstants[3]

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
aConstants – fixed size array of constant values, one per channel..
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist32fC_16f_C4IR_Ctx(Npp16f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[4][4], const Npp32f aConstants[4], NppStreamContext nppStreamCtx)
4 channel 16-bit floating point in place color twist with 4x4 matrix and an additional constant vector addition.
An input 4x4 color twist matrix with 32-bit floating-point coefficient values with an additional 32-bit floating point constant vector addition is applied within ROI. For this particular version of the function the result is generated as shown below.

dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3] * src[3] + aConstants[0]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3] * src[3] + aConstants[1]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3] * src[3] + aConstants[2]
dst[3] = aTwist[3][0] * src[0] + aTwist[3][1] * src[1] + aTwist[3][2] * src[2] + aTwist[3][3] * src[3] + aConstants[3]

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
aConstants – fixed size array of constant values, one per channel..
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
1 channel 32-bit floating point color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
1 channel 32-bit floating point in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32f_C2R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
2 channel 32-bit floating point color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32f_C2IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
2 channel 32-bit floating point in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point color twist, with alpha copy.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is copied unmodified from the source pixel to the destination pixel.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32f_C4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point in place color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is not modified.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point in place color twist, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied with in ROI. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32fC_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[4][4], const Npp32f aConstants[4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point color twist with 4x4 matrix and constant vector addition.
An input 4x4 color twist matrix with floating-point coefficient values with an additional constant vector addition is applied within ROI. For this particular version of the function the result is generated as shown below.

dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3] * src[3] + aConstants[0]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3] * src[3] + aConstants[1]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3] * src[3] + aConstants[2]
dst[3] = aTwist[3][0] * src[0] + aTwist[3][1] * src[1] + aTwist[3][2] * src[2] + aTwist[3][3] * src[3] + aConstants[3]

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
aConstants – fixed size array of constant values, one per channel..
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32fC_C4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[4][4], const Npp32f aConstants[4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point in place color twist with 4x4 matrix and an additional constant vector addition.
An input 4x4 color twist matrix with floating-point coefficient values with an additional constant vector addition is applied within ROI. For this particular version of the function the result is generated as shown below.

dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3] * src[3] + aConstants[0]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3] * src[3] + aConstants[1]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3] * src[3] + aConstants[2]
dst[3] = aTwist[3][0] * src[0] + aTwist[3][1] * src[1] + aTwist[3][2] * src[2] + aTwist[3][3] * src[3] + aConstants[3]

Parameters

pSrcDst – in place packed pixel format image pointer.
nSrcDstStep – in place packed pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
aConstants – fixed size array of constant values, one per channel..
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32f_P3R_Ctx(const Npp32f *const pSrc[3], int nSrcStep, Npp32f *const pDst[3], int nDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point planar color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwist_32f_IP3R_Ctx(Npp32f *const pSrcDst[3], int nSrcDstStep, NppiSize oSizeROI, const Npp32f aTwist[3][4], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point planar in place color twist.
An input color twist matrix with floating-point coefficient values is applied within ROI.

Parameters

pSrcDst – in place planar pixel format image pointer array, one pointer per plane.
nSrcDstStep – in place planar pixel format image line step.
oSizeROI – Region-Of-Interest (ROI).
aTwist – The color twist matrix with floating-point coefficient values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### ColorTwistBatch


Routines for converting between various image color models using user supplied matrix coefficients on batches of images.


ColorTwistBatch


Perform color twist pixel batch processing.


Color twist consists of applying the following formula to each image pixel using coefficients from one or more user supplied color twist device memory matrix arrays as follows where dst[x] and src[x] represent destination pixel and source pixel channel or plane x. The full sized coefficient matrix should be sent for all pixel channel sizes, the function will process the appropriate coefficients and channels for the corresponding pixel size. ColorTwistBatch generally takes the same parameter list as ColorTwist except that there is a list of N instances of those parameters (N > 1) and that list is passed in device memory; The matrix pointers referenced for each image in the batch also need to point to device memory matrix values. A convenient data structure is provided that allows for easy initialization of the parameter lists. The only restriction on these functions is that there is one single ROI which is applied respectively to each image in the batch. The primary purpose of this function is to provide improved performance for batches of smaller images as long as GPU resources are available. Therefore it is recommended that the function not be used for very large images as there may not be resources available for processing several large images simultaneously.




```
dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3]
```


NppStatus nppiColorTwistBatch32f_8u_C1R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer color twist batch.
An input color twist matrix with floating-point coefficient values is applied within the ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_8u_C1IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
1 channel 8-bit unsigned integer in place color twist batch.
An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_8u_C3R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer color twist batch.
An input color twist matrix with floating-point coefficient values is applied within the ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_8u_C3IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned integer in place color twist batch.
An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_8u_C4R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned integer color twist batch.
An input color twist matrix with floating-point coefficient values is applied within the ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_8u_C4IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned integer in place color twist batch.
An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_8u_AC4R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned integer color twist batch, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied within the ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_8u_AC4IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned integer in place color twist batch, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32fC_8u_C4R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned integer color twist with 4x5 matrix including a constant vector (20 coefficients total).
An input 4x5 color twist matrix with floating-point coefficient values including a constant (in the fourth column) vector is applied within ROI. For this particular version of the function the result is generated as shown below.

dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3] * src[3] + aTwist[0][4]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3] * src[3] + aTwist[1][4]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3] * src[3] + aTwist[2][4]
dst[3] = aTwist[3][0] * src[0] + aTwist[3][1] * src[1] + aTwist[3][2] * src[2] + aTwist[3][3] * src[3] + aTwist[3][4]

An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32fC_8u_C4IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned integer in place color twist with 4x5 matrix including a constant vector (20 coefficients total).
An input 4x5 color twist matrix with floating-point coefficient values including a constant (in the fourth column) vector is applied within ROI. For this particular version of the function the result is generated as shown below.

dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3] * src[3] + aTwist[0][4]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3] * src[3] + aTwist[1][4]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3] * src[3] + aTwist[2][4]
dst[3] = aTwist[3][0] * src[0] + aTwist[3][1] * src[1] + aTwist[3][2] * src[2] + aTwist[3][3] * src[3] + aTwist[3][4]

An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch_32f_C1R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point color twist batch.
An input color twist matrix with floating-point coefficient values is applied within the ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch_32f_C1IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
1 channel 32-bit floating point in place color twist batch.
An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch_32f_C3R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point color twist batch.
An input color twist matrix with floating-point coefficient values is applied within the ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch_32f_C3IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
3 channel 32-bit floating point in place color twist batch.
An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch_32f_C4R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point color twist batch.
An input color twist matrix with floating-point coefficient values is applied within the ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch_32f_C4IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point in place color twist batch.
An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch_32f_AC4R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point color twist batch, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied within the ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch_32f_AC4IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point in place color twist batch, not affecting Alpha.
An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch_32fC_C4R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 32-bit floating point color twist with 4x5 matrix including a constant vector (20 coefficients total).
An input 4x5 color twist matrix with floating-point coefficient values including a constant (in the fourth column) vector is applied within ROI. For this particular version of the function the result is generated as shown below.

dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3] * src[3] + aTwist[0][4]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3] * src[3] + aTwist[1][4]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3] * src[3] + aTwist[2][4]
dst[3] = aTwist[3][0] * src[0] + aTwist[3][1] * src[1] + aTwist[3][2] * src[2] + aTwist[3][3] * src[3] + aTwist[3][4]

An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch_32fC_C4IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel in place 32-bit floating point color twist with 4x5 matrix including a constant vector (20 coefficients total).
An input 4x5 color twist matrix with floating-point coefficient values including a constant (in the fourth column) vector is applied within ROI. For this particular version of the function the result is generated as shown below.

dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3] * src[3] + aTwist[0][4]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3] * src[3] + aTwist[1][4]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3] * src[3] + aTwist[2][4]
dst[3] = aTwist[3][0] * src[0] + aTwist[3][1] * src[1] + aTwist[3][2] * src[2] + aTwist[3][3] * src[3] + aTwist[3][4]

An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_16f_C1R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
1 channel 16-bit floating point color twist batch.
An input color twist matrix with 32-bit floating-point coefficient values is applied within the ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_16f_C1IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
1 channel 16-bit floating point in place color twist batch.
An input color twist matrix with 32-bit floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_16f_C3R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
3 channel 16-bit floating point color twist batch.
An input color twist matrix with 32-bit floating-point coefficient values is applied within the ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_16f_C3IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
3 channel 16-bit floating point in place color twist batch.
An input color twist matrix with floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_16f_C4R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 16-bit floating point color twist batch.
An input color twist matrix with 32-bit floating-point coefficient values is applied within the ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32f_16f_C4IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 16-bit floating point in place color twist batch.
An input color twist matrix with 32-bit floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32fC_16f_C4R_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel 16-bit floating point color twist with 4x5 matrix including a constant vector (20 coefficients total).
An input 4x5 color twist matrix with 32-bit floating-point coefficient values including a constant (in the fourth column) vector is applied within ROI. For this particular version of the function the result is generated as shown below.

dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3] * src[3] + aTwist[0][4]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3] * src[3] + aTwist[1][4]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3] * src[3] + aTwist[2][4]
dst[3] = aTwist[3][0] * src[0] + aTwist[3][1] * src[1] + aTwist[3][2] * src[2] + aTwist[3][3] * src[3] + aTwist[3][4]

An input color twist matrix with 32-bit floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiColorTwistBatch32fC_16f_C4IR_Ctx(Npp32f nMin, Npp32f nMax, NppiSize oSizeROI, NppiColorTwistBatchCXR *pBatchList, int nBatchSize, NppStreamContext nppStreamCtx)
4 channel in place 16-bit floating point color twist with 4x5 matrix including a constant vector (20 coefficients total).
An input 4x5 color twist matrix with 32-bitfloating-point coefficient values including a constant (in the fourth column) vector is applied within ROI. For this particular version of the function the result is generated as shown below.

dst[0] = aTwist[0][0] * src[0] + aTwist[0][1] * src[1] + aTwist[0][2] * src[2] + aTwist[0][3] * src[3] + aTwist[0][4]
dst[1] = aTwist[1][0] * src[0] + aTwist[1][1] * src[1] + aTwist[1][2] * src[2] + aTwist[1][3] * src[3] + aTwist[1][4]
dst[2] = aTwist[2][0] * src[0] + aTwist[2][1] * src[1] + aTwist[2][2] * src[2] + aTwist[2][3] * src[3] + aTwist[2][4]
dst[3] = aTwist[3][0] * src[0] + aTwist[3][1] * src[1] + aTwist[3][2] * src[2] + aTwist[3][3] * src[3] + aTwist[3][4]

An input color twist matrix with 32-bit floating-point coefficient values is applied within ROI for each image in batch. Color twist matrix can vary per image. The same ROI is applied to each image.

Parameters

nMin – Minimum clamp value.
nMax – Maximum saturation and clamp value.
oSizeROI – Region-Of-Interest (ROI).
pBatchList – Device memory pointer to nBatchSize list of NppiColorTwistBatchCXR structures.
nBatchSize – Number of NppiColorTwistBatchCXR structures in this call (must be > 1).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### ColorLUT


Perform image color processing using members of various types of color look up tables.


Functions


NppStatus nppiLUT_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
8-bit unsigned look-up-table color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
8-bit unsigned look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned look-up-table color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_8u_C4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned look-up-table in place color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
16-bit unsigned look-up-table color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
16-bit unsigned look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned look-up-table color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16u_C4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16u_AC4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned look-up-table in place color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
16-bit signed look-up-table color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16s_C1IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
16-bit signed look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16s_C3IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 16-bit signed look-up-table color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16s_C4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 16-bit signed look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_16s_AC4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed look-up-table in place color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pValues, const Npp32f *pLevels, int nLevels, NppStreamContext nppStreamCtx)
32-bit floating point look-up-table color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f *pValues, const Npp32f *pLevels, int nLevels, NppStreamContext nppStreamCtx)
32-bit floating point look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pValues[3], const Npp32f *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f *pValues[3], const Npp32f *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pValues[4], const Npp32f *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point look-up-table color conversion.
The LUT is derived from a set of user defined mapping points with no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_32f_C4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f *pValues[4], const Npp32f *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pValues[3], const Npp32f *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f *pValues[3], const Npp32f *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point look-up-table in place color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


### ColorLUTLinear


Perform image color processing using linear interpolation between members of various types of color look up tables.


Functions


NppStatus nppiLUT_Linear_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
8-bit unsigned linear interpolated look-up-table color conversion.
The LUT is derived from a set of user defined mapping points through linear interpolation.

ATTENTION ATTENTION <<<<<<<

NOTE: As of the 5.0 release of NPP, the pValues and pLevels pointers need to be device memory pointers.

 <<<<<<<

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is now a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is now a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Linear_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
8-bit unsigned linear interpolated look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points through linear interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Linear_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned linear interpolated look-up-table color conversion.
The LUT is derived from a set of user defined mapping points through linear interpolation.

ATTENTION ATTENTION <<<<<<<

NOTE: As of the 5.0 release of NPP, the pValues and pLevels pointers need to be host memory pointers to arrays of device memory pointers.

 <<<<<<<

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Linear_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned linear interpolated look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points through linear interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Linear_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned linear interpolated look-up-table color conversion.
The LUT is derived from a set of user defined mapping points through linear interpolation.

ATTENTION ATTENTION <<<<<<<

NOTE: As of the 5.0 release of NPP, the pValues and pLevels pointers need to be host memory pointers to arrays of device memory pointers.

 <<<<<<<

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Linear_8u_C4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned linear interpolated look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points through linear interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Linear_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned linear interpolated look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points through linear interpolation. Alpha channel is the last channel and is not processed.

ATTENTION ATTENTION <<<<<<<

NOTE: As of the 5.0 release of NPP, the pValues and pLevels pointers need to be host memory pointers to arrays of device memory pointers.

 <<<<<<<

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Linear_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned linear interpolated look-up-table in place color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points through linear interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Linear_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
16-bit unsigned look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using linear interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
16-bit unsigned look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using linear interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using linear interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using linear interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16u_C4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16u_AC4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned look-up-table in place color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
16-bit signed look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using linear interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16s_C1IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
16-bit signed look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using linear interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16s_C3IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using linear interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 16-bit signed look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using linear interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16s_C4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 16-bit signed look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_16s_AC4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed look-up-table in place color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pValues, const Npp32f *pLevels, int nLevels, NppStreamContext nppStreamCtx)
32-bit floating point look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using linear interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f *pValues, const Npp32f *pLevels, int nLevels, NppStreamContext nppStreamCtx)
32-bit floating point look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using linear interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pValues[3], const Npp32f *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f *pValues[3], const Npp32f *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using linear interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pValues[4], const Npp32f *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using linear interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_32f_C4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f *pValues[4], const Npp32f *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pValues[3], const Npp32f *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Linear_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f *pValues[3], const Npp32f *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point look-up-table in place color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


### ColorLUTCubic


Perform image color processing using linear interpolation between members of various types of color look up tables.


Functions


NppStatus nppiLUT_Cubic_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
8-bit unsigned cubic interpolated look-up-table color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Cubic_8u_C1IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
8-bit unsigned cubic interpolated look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Cubic_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned cubic interpolated look-up-table color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Cubic_8u_C3IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned cubic interpolated look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Cubic_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned cubic interpolated look-up-table color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Cubic_8u_C4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned cubic interpolated look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Cubic_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned cubic interpolated look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points through cubic interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Cubic_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned cubic interpolated look-up-table in place color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points through cubic interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Cubic_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
16-bit unsigned look-up-table color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16u_C1IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
16-bit unsigned look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16u_C3IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 16-bit unsigned look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned look-up-table color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16u_C4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16u_AC4IR_Ctx(Npp16u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 16-bit unsigned look-up-table in place color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16s_C1R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
16-bit signed look-up-table color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16s_C1IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues, const Npp32s *pLevels, int nLevels, NppStreamContext nppStreamCtx)
16-bit signed look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16s_C3R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16s_C3IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 16-bit signed look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16s_C4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 16-bit signed look-up-table color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16s_C4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[4], const Npp32s *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 16-bit signed look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16s_AC4R_Ctx(const Npp16s *pSrc, int nSrcStep, Npp16s *pDst, int nDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_16s_AC4IR_Ctx(Npp16s *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32s *pValues[3], const Npp32s *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 16-bit signed look-up-table in place color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_32f_C1R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pValues, const Npp32f *pLevels, int nLevels, NppStreamContext nppStreamCtx)
32-bit floating point look-up-table color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_32f_C1IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f *pValues, const Npp32f *pLevels, int nLevels, NppStreamContext nppStreamCtx)
32-bit floating point look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Pointer to an array of user defined OUTPUT values (this is a device memory pointer)
pLevels – Pointer to an array of user defined INPUT values (this is a device memory pointer)
nLevels – Number of user defined number of input/output mapping points (levels)
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_32f_C3R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pValues[3], const Npp32f *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point look-up-table color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_32f_C3IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f *pValues[3], const Npp32f *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
3 channel 32-bit floating point look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_32f_C4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pValues[4], const Npp32f *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point look-up-table color conversion.
The LUT is derived from a set of user defined mapping points through cubic interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_32f_C4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f *pValues[4], const Npp32f *pLevels[4], int nLevels[4], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point look-up-table in place color conversion.
The LUT is derived from a set of user defined mapping points using no interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 4 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_32f_AC4R_Ctx(const Npp32f *pSrc, int nSrcStep, Npp32f *pDst, int nDstStep, NppiSize oSizeROI, const Npp32f *pValues[3], const Npp32f *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


NppStatus nppiLUT_Cubic_32f_AC4IR_Ctx(Npp32f *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, const Npp32f *pValues[3], const Npp32f *pLevels[3], int nLevels[3], NppStreamContext nppStreamCtx)
4 channel 32-bit floating point look-up-table in place color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points using no interpolation. Alpha channel is the last channel and is not processed.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT values.
pLevels – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined INPUT values.
nLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per color CHANNEL.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 1024 (the current size limit).


### ColorLUTTrilinear


Perform image color processing using 3D trilinear interpolation between members of various types of color look up tables.


Functions


NppStatus nppiLUT_Trilinear_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp32u *pValues, Npp8u *pLevels[3], int aLevels[3], NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned 3D trilinear interpolated look-up-table color conversion, with alpha copy.
Alpha channel is the last channel and is copied to the destination unmodified.
The LUT is derived from a set of user defined mapping points through trilinear interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Device pointer to aLevels[2] number of contiguous 2D x,y planes of 4-byte packed RGBX values containing the user defined base OUTPUT values at that x,y, and z (R,G,B) level location. Each level must contain x * y 4-byte packed pixel values (4th byte is used for alignement only and is ignored) in row (x) order.
pLevels – Host pointer to an array of 3 host pointers, one per cube edge, pointing to user defined INPUT level values.
aLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per 3D cube edge. aLevels[0] represents the number of x axis levels (Red), aLevels[1] represents the number of y axis levels (Green), and aLevels[2] represets the number of z axis levels (Blue).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Trilinear_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp32u *pValues, Npp8u *pLevels[3], int aLevels[3], NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned 3D trilinear interpolated look-up-table color conversion, not affecting alpha.
Alpha channel is the last channel and is not processed.
The LUT is derived from a set of user defined mapping points through trilinear interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Device pointer to aLevels[2] number of contiguous 2D x,y planes of 4-byte packed RGBX values containing the user defined base OUTPUT values at that x,y, and z (R,G,B) level location. Each level must contain x * y 4-byte packed pixel values (4th byte is used for alignement only and is ignored) in row (x) order.
pLevels – Host pointer to an array of 3 host pointers, one per cube edge, pointing to user defined INPUT level values.
aLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per 3D cube edge. aLevels[0] represents the number of x axis levels (Red), aLevels[1] represents the number of y axis levels (Green), and aLevels[2] represets the number of z axis levels (Blue).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


NppStatus nppiLUT_Trilinear_8u_AC4IR_Ctx(Npp8u *pSrcDst, int nSrcDstStep, NppiSize oSizeROI, Npp32u *pValues, Npp8u *pLevels[3], int aLevels[3], NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned 3D trilinear interpolated look-up-table in place color conversion, not affecting alpha.
Alpha channel is the last channel and is not processed.
The LUT is derived from a set of user defined mapping points through trilinear interpolation.

Parameters

pSrcDst – In-Place Image Pointer.
nSrcDstStep – In-Place-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pValues – Device pointer aLevels[2] number of contiguous 2D x,y planes of 4-byte packed RGBX values containing the user defined base OUTPUT values at that x,y, and z (R,G,B) level location. Each level must contain x * y 4-byte packed pixel values (4th byte is used for alignement only and is ignored) in row (x) order.
pLevels – Host pointer to an array of 3 host pointers, one per cube edge, pointing to user defined INPUT level values.
aLevels – Host pointer to an array of 3 user defined number of input/output mapping points, one per 3D cube edge. aLevels[0] represents the number of x axis levels (Red), aLevels[1] represents the number of y axis levels (Green), and aLevels[2] represets the number of z axis levels (Blue).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_NUMBER_OF_LEVELS_ERROR if the number of levels is less than 2 or greater than 256.


### ColorLUTPalette


Perform image color processing using various types of bit range restricted palette color look up tables.


Functions


NppStatus nppiLUTPalette_8u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pTable, int nBitSize, NppStreamContext nppStreamCtx)
One channel 8-bit unsigned bit range restricted palette look-up-table color conversion.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pTable – Pointer to an array of user defined OUTPUT palette values (this is a device memory pointer)
nBitSize – Number of least significant bits (must be > 0 and <= 8) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 8.


NppStatus nppiLUTPalette_8u24u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pTable, int nBitSize, NppStreamContext nppStreamCtx)
One channel 8-bit unsigned bit range restricted 24-bit palette look-up-table color conversion with 24-bit destination output per pixel.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step (3 bytes per pixel).
oSizeROI – Region-Of-Interest (ROI).
pTable – Pointer to an array of user defined OUTPUT palette values (this is a device memory pointer)
nBitSize – Number of least significant bits (must be > 0 and <= 8) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 8.


NppStatus nppiLUTPalette_8u32u_C1R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp32u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32u *pTable, int nBitSize, NppStreamContext nppStreamCtx)
One channel 8-bit unsigned bit range restricted 32-bit palette look-up-table color conversion with 32-bit destination output per pixel.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step (4 bytes per pixel).
oSizeROI – Region-Of-Interest (ROI).
pTable – Pointer to an array of user defined OUTPUT palette values (this is a device memory pointer)
nBitSize – Number of least significant bits (must be > 0 and <= 8) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 8.


NppStatus nppiLUTPalette_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pTables[3], int nBitSize, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned bit range restricted palette look-up-table color conversion.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pTables – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT palette values.
nBitSize – Number of least significant bits (must be > 0 and <= 8) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 8.


NppStatus nppiLUTPalette_8u_C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pTables[4], int nBitSize, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned bit range restricted palette look-up-table color conversion.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pTables – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT palette values.
nBitSize – Number of least significant bits (must be > 0 and <= 8) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 8.


NppStatus nppiLUTPalette_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pTables[3], int nBitSize, NppStreamContext nppStreamCtx)
Four channel 8-bit unsigned bit range restricted palette look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pTables – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT palette values.
nBitSize – Number of least significant bits (must be > 0 and <= 8) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 8.


NppStatus nppiLUTPalette_16u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u *pTable, int nBitSize, NppStreamContext nppStreamCtx)
One channel 16-bit unsigned bit range restricted palette look-up-table color conversion.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pTable – Pointer to an array of user defined OUTPUT palette values (this is a device memory pointer)
nBitSize – Number of least significant bits (must be > 0 and <= 16) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 16.


NppStatus nppiLUTPalette_16u8u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pTable, int nBitSize, NppStreamContext nppStreamCtx)
One channel 16-bit unsigned bit range restricted 8-bit unsigned palette look-up-table color conversion with 8-bit unsigned destination output per pixel.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step (1 unsigned byte per pixel).
oSizeROI – Region-Of-Interest (ROI).
pTable – Pointer to an array of user defined OUTPUT palette values (this is a device memory pointer)
nBitSize – Number of least significant bits (must be > 0 and <= 16) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 16.


NppStatus nppiLUTPalette_16u24u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pTable, int nBitSize, NppStreamContext nppStreamCtx)
One channel 16-bit unsigned bit range restricted 24-bit unsigned palette look-up-table color conversion with 24-bit unsigned destination output per pixel.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step (3 unsigned bytes per pixel).
oSizeROI – Region-Of-Interest (ROI).
pTable – Pointer to an array of user defined OUTPUT palette values (this is a device memory pointer)
nBitSize – Number of least significant bits (must be > 0 and <= 16) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 16.


NppStatus nppiLUTPalette_16u32u_C1R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp32u *pDst, int nDstStep, NppiSize oSizeROI, const Npp32u *pTable, int nBitSize, NppStreamContext nppStreamCtx)
One channel 16-bit unsigned bit range restricted 32-bit palette look-up-table color conversion with 32-bit unsigned destination output per pixel.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step (4 bytes per pixel).
oSizeROI – Region-Of-Interest (ROI).
pTable – Pointer to an array of user defined OUTPUT palette values (this is a device memory pointer)
nBitSize – Number of least significant bits (must be > 0 and <= 16) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 16.


NppStatus nppiLUTPalette_16u_C3R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u *pTables[3], int nBitSize, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned bit range restricted palette look-up-table color conversion.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pTables – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT palette values.
nBitSize – Number of least significant bits (must be > 0 and <= 16) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 16.


NppStatus nppiLUTPalette_16u_C4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u *pTables[4], int nBitSize, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned bit range restricted palette look-up-table color conversion.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pTables – Host pointer to an array of 4 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT palette values.
nBitSize – Number of least significant bits (must be > 0 and <= 16) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 16.


NppStatus nppiLUTPalette_16u_AC4R_Ctx(const Npp16u *pSrc, int nSrcStep, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u *pTables[3], int nBitSize, NppStreamContext nppStreamCtx)
Four channel 16-bit unsigned bit range restricted palette look-up-table color conversion, not affecting Alpha.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values. Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pTables – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT palette values.
nBitSize – Number of least significant bits (must be > 0 and <= 16) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 16.


NppStatus nppiLUTPaletteSwap_8u_C3A0C4R_Ctx(const Npp8u *pSrc, int nSrcStep, int nAlphaValue, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, const Npp8u *pTables[3], int nBitSize, NppStreamContext nppStreamCtx)
Three channel 8-bit unsigned source bit range restricted palette look-up-table color conversion to four channel 8-bit unsigned destination output with alpha.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values. This function also reverses the source pixel channel order in the destination so the Alpha channel is the first channel.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step (3 bytes per pixel).
nAlphaValue – Signed alpha value that will be used to initialize the pixel alpha channel position in all modified destination pixels.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step (4 bytes per pixel with alpha).
oSizeROI – Region-Of-Interest (ROI).
pTables – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT palette values. Alpha values < 0 or > 255 will cause destination pixel alpha channel values to be unmodified.
nBitSize – Number of least significant bits (must be > 0 and <= 8) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 8.


NppStatus nppiLUTPaletteSwap_16u_C3A0C4R_Ctx(const Npp16u *pSrc, int nSrcStep, int nAlphaValue, Npp16u *pDst, int nDstStep, NppiSize oSizeROI, const Npp16u *pTables[3], int nBitSize, NppStreamContext nppStreamCtx)
Three channel 16-bit unsigned source bit range restricted palette look-up-table color conversion to four channel 16-bit unsigned destination output with alpha.
The LUT is derived from a set of user defined mapping points in a palette and source pixels are then processed using a restricted bit range when looking up palette values. This function also reverses the source pixel channel order in the destination so the Alpha channel is the first channel.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step (3 unsigned short integers per pixel).
nAlphaValue – Signed alpha value that will be used to initialize the pixel alpha channel position in all modified destination pixels.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step (4 unsigned short integers per pixel with alpha).
oSizeROI – Region-Of-Interest (ROI).
pTables – Host pointer to an array of 3 device memory pointers, one per color CHANNEL, pointing to user defined OUTPUT palette values. Alpha values < 0 or > 65535 will cause destination pixel alpha channel values to be unmodified.
nBitSize – Number of least significant bits (must be > 0 and <= 16) of each source pixel value to use as index into palette table during conversion.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes

NPP_LUT_PALETTE_BITSIZE_ERROR if nBitSize is < 1 or > 16.


## Color Sampling Format Conversion Functions


Routines for converting between various image color sampling formats.


### YCbCr420ToYCbCr411


YCbCr420 to YCbCr411 sampling format conversion.


Functions


NppStatus nppiYCbCr420ToYCbCr411_8u_P3P2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDstY, int nDstYStep, Npp8u *pDstCbCr, int nDstCbCrStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 2 channel 8-bit unsigned planar YCbCr411 sampling format conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDstY – Destination-Planar-Image Pointer.
nDstYStep – Destination-Planar-Image Line Step.
pDstCbCr – Destination-Planar-Image Pointer.
nDstCbCrStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr420ToYCbCr411_8u_P2P3R_Ctx(const Npp8u *pSrcY, int nSrcYStep, const Npp8u *pSrcCbCr, int nSrcCbCrStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned planar YCbCr411 sampling format conversion.

Parameters

pSrcY – Source-Planar-Image Pointer.
nSrcYStep – Source-Planar-Image Line Step.
pSrcCbCr – Source-Planar-Image Pointer.
nSrcCbCrStep – Source-Planar-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr422ToYCbCr422


YCbCr422 to YCbCr422 sampling format conversion.


Functions


NppStatus nppiYCbCr422_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCbCr422 to 3 channel 8-bit unsigned planar YCbCr422 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422_8u_P3C2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 2 channel 8-bit unsigned packed YCbCr422 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr422ToYCrCb422


YCbCr422 to YCrCb422 sampling format conversion.


Functions


NppStatus nppiYCbCr422ToYCrCb422_8u_C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCbCr422 to 2 channel 8-bit unsigned packed YCrCb422 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToYCrCb422_8u_P3C2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 2 channel 8-bit unsigned packed YCrCb422 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr422ToCbYCr422


YCbCr422 to CbYCr422 sampling format conversion.


Functions


NppStatus nppiYCbCr422ToCbYCr422_8u_C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCbCr422 to 2 channel 8-bit unsigned packed CbYCr422 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### CbYCr422ToYCbCr411


CbYCr422 to YCbCr411 sampling format conversion.


Functions


NppStatus nppiCbYCr422ToYCbCr411_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed CbYCr422 to 3 channel 8-bit unsigned planar YCbCr411 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr422ToYCbCr420


YCbCr422 to YCbCr420 sampling format conversion.


Functions


NppStatus nppiYCbCr422ToYCbCr420_8u_P3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst[3], int nDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 3 channel 8-bit unsigned planar YCbCr420 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToYCbCr420_8u_P3P2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDstY, int nDstYStep, Npp8u *pDstCbCr, int nDstCbCrStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 2 channel 8-bit unsigned planar YCbCr420 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDstY – Destination-Planar-Image Pointer.
nDstYStep – Destination-Planar-Image Line Step.
pDstCbCr – Destination-Planar-Image Pointer.
nDstCbCrStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToYCbCr420_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCbCr422 to 3 channel 8-bit unsigned planar YCbCr420 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToYCbCr420_8u_C2P2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDstY, int nDstYStep, Npp8u *pDstCbCr, int nDstCbCrStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCbCr422 to 2 channel 8-bit unsigned planar YCbCr420 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDstY – Destination-Planar-Image Pointer.
nDstYStep – Destination-Planar-Image Line Step.
pDstCbCr – Destination-Planar-Image Pointer.
nDstCbCrStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCrCb420ToYCbCr422


YCrCb420 to YCbCr422 sampling format conversion.


Functions


NppStatus nppiYCrCb420ToYCbCr422_8u_P3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCrCb420 to 3 channel 8-bit unsigned planar YCbCr422 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCrCb420ToYCbCr422_8u_P3C2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCrCb420 to 2 channel 8-bit unsigned packed YCbCr422 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr422ToYCrCb420


YCbCr422 to YCrCb420 sampling format conversion.


Functions


NppStatus nppiYCbCr422ToYCrCb420_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCbCr422 to 3 channel 8-bit unsigned planar YCrCb420 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr422ToYCbCr411


YCbCr422 to YCbCr411 sampling format conversion.


Functions


NppStatus nppiYCbCr422ToYCbCr411_8u_P3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 3 channel 8-bit unsigned planar YCbCr411 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToYCbCr411_8u_P3P2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDstY, int nDstYStep, Npp8u *pDstCbCr, int nDstCbCrStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 2 channel 8-bit unsigned planar YCbCr411 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDstY – Destination-Planar-Image Pointer.
nDstYStep – Destination-Planar-Image Line Step.
pDstCbCr – Destination-Planar-Image Pointer.
nDstCbCrStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToYCbCr411_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCbCr422 to 3 channel 8-bit unsigned planar YCbCr411 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToYCbCr411_8u_C2P2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDstY, int nDstYStep, Npp8u *pDstCbCr, int nDstCbCrStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCbCr422 to 2 channel 8-bit unsigned planar YCbCr411 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDstY – Destination-Planar-Image Pointer.
nDstYStep – Destination-Planar-Image Line Step.
pDstCbCr – Destination-Planar-Image Pointer.
nDstCbCrStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCrCb422ToYCbCr422


YCrCb422 to YCbCr422 sampling format conversion.


Functions


NppStatus nppiYCrCb422ToYCbCr422_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCrCb422 to 3 channel 8-bit unsigned planar YCbCr422 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCrCb422ToYCbCr420


YCrCb422 to YCbCr420 sampling format conversion.


Functions


NppStatus nppiYCrCb422ToYCbCr420_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCrCb422 to 3 channel 8-bit unsigned planar YCbCr420 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCrCb422ToYCbCr411


YCrCb422 to YCbCr411 sampling format conversion.


Functions


NppStatus nppiYCrCb422ToYCbCr411_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCrCb422 to 3 channel 8-bit unsigned planar YCbCr411 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### CbYCr422ToYCbCr422


CbYCr422 to YCbCr422 sampling format conversion.


Functions


NppStatus nppiCbYCr422ToYCbCr422_8u_C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed CbYCr422 to 2 channel 8-bit unsigned packed YCbCr422 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiCbYCr422ToYCbCr422_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed CbYCr422 to 3 channel 8-bit unsigned planar YCbCr422 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### CbYCr422ToYCbCr420


CbYCr422 to YCbCr420 sampling format conversion.


Functions


NppStatus nppiCbYCr422ToYCbCr420_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed CbYCr422 to 3 channel 8-bit unsigned planar YCbCr420 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiCbYCr422ToYCbCr420_8u_C2P2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDstY, int nDstYStep, Npp8u *pDstCbCr, int nDstCbCrStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed CbYCr422 to 2 channel 8-bit unsigned planar YCbCr420 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDstY – Destination-Planar-Image Pointer.
nDstYStep – Destination-Planar-Image Line Step.
pDstCbCr – Destination-Planar-Image Pointer.
nDstCbCrStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### CbYCr422ToYCrCb420


CbYCr422 to YCrCb420 sampling format conversion.


Functions


NppStatus nppiCbYCr422ToYCrCb420_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed CbYCr422 to 3 channel 8-bit unsigned planar YCrCb420 sampling format conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr420ToYCbCr420


YCbCr420 to YCbCr420 sampling format conversion.


Functions


NppStatus nppiYCbCr420_8u_P3P2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDstY, int nDstYStep, Npp8u *pDstCbCr, int nDstCbCrStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 2 channel 8-bit unsigned planar YCbCr420 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDstY – Destination-Planar-Image Pointer.
nDstYStep – Destination-Planar-Image Line Step.
pDstCbCr – Destination-Planar-Image Pointer.
nDstCbCrStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr420_8u_P2P3R_Ctx(const Npp8u *const pSrcY, int nSrcYStep, const Npp8u *pSrcCbCr, int nSrcCbCrStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned planar YCbCr420 sampling format conversion.

Parameters

pSrcY – Source-Planar-Image Pointer.
nSrcYStep – Source-Planar-Image Line Step.
pSrcCbCr – Source-Planar-Image Pointer.
nSrcCbCrStep – Source-Planar-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr420ToYCbCr422


YCbCr420 to YCbCr422 sampling format conversion.


Functions


NppStatus nppiYCbCr420ToYCbCr422_8u_P3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst[3], int nDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned planar YCbCr422 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr420ToYCbCr422_8u_P2P3R_Ctx(const Npp8u *pSrcY, int nSrcYStep, const Npp8u *pSrcCbCr, int nSrcCbCrStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned planar YCbCr422 sampling format conversion.

Parameters

pSrcY – Source-Planar-Image Pointer.
nSrcYStep – Source-Planar-Image Line Step.
pSrcCbCr – Source-Planar-Image Pointer.
nSrcCbCrStep – Source-Planar-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr420ToYCbCr422_8u_P2C2R_Ctx(const Npp8u *pSrcY, int nSrcYStep, const Npp8u *pSrcCbCr, int nSrcCbCrStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar YCbCr420 to 2 channel 8-bit unsigned packed YCbCr422 sampling format conversion.

Parameters

pSrcY – Source-Planar-Image Pointer.
nSrcYStep – Source-Planar-Image Line Step.
pSrcCbCr – Source-Planar-Image Pointer.
nSrcCbCrStep – Source-Planar-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr420ToCbYCr422


YCbCr420 to CbYCr422 sampling format conversion.


Functions


NppStatus nppiYCbCr420ToCbYCr422_8u_P2C2R_Ctx(const Npp8u *pSrcY, int nSrcYStep, const Npp8u *pSrcCbCr, int nSrcCbCrStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar YCbCr420 to 2 channel 8-bit unsigned packed CbYCr422 sampling format conversion.

Parameters

pSrcY – Source-Planar-Image Pointer.
nSrcYStep – Source-Planar-Image Line Step.
pSrcCbCr – Source-Planar-Image Pointer.
nSrcCbCrStep – Source-Planar-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr420ToYCrCb420


YCbCr420 to YCrCb420 sampling format conversion.


Functions


NppStatus nppiYCbCr420ToYCrCb420_8u_P2P3R_Ctx(const Npp8u *pSrcY, int nSrcYStep, const Npp8u *pSrcCbCr, int nSrcCbCrStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned planar YCrCb420 sampling format conversion.

Parameters

pSrcY – Source-Planar-Image Pointer.
nSrcYStep – Source-Planar-Image Line Step.
pSrcCbCr – Source-Planar-Image Pointer.
nSrcCbCrStep – Source-Planar-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCrCb420ToCbYCr422


YCrCb420 to CbYCr422 sampling format conversion.


Functions


NppStatus nppiYCrCb420ToCbYCr422_8u_P3C2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCrCb420 to 2 channel 8-bit unsigned packed CbYCr422 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCrCb420ToYCbYCr420


YCrCb420 to YCbCr420 sampling format conversion.


Functions


NppStatus nppiYCrCb420ToYCbCr420_8u_P3P2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDstY, int nDstYStep, Npp8u *pDstCbCr, int nDstCbCrStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCrCb420 to 2 channel 8-bit unsigned planar YCbCr420 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDstY – Destination-Planar-Image Pointer.
nDstYStep – Destination-Planar-Image Line Step.
pDstCbCr – Destination-Planar-Image Pointer.
nDstCbCrStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCrCb420ToYCbYCr411


YCrCb420 to YCbCr411 sampling format conversion.


Functions


NppStatus nppiYCrCb420ToYCbCr411_8u_P3P2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDstY, int nDstYStep, Npp8u *pDstCbCr, int nDstCbCrStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCrCb420 to 2 channel 8-bit unsigned planar YCbCr411 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDstY – Destination-Planar-Image Pointer.
nDstYStep – Destination-Planar-Image Line Step.
pDstCbCr – Destination-Planar-Image Pointer.
nDstCbCrStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr411ToYCbCr411


YCbCr411 to YCbCr411 sampling format conversion.


Functions


NppStatus nppiYCbCr411_8u_P3P2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDstY, int nDstYStep, Npp8u *pDstCbCr, int nDstCbCrStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 2 channel 8-bit unsigned planar YCbCr411 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDstY – Destination-Planar-Image Pointer.
nDstYStep – Destination-Planar-Image Line Step.
pDstCbCr – Destination-Planar-Image Pointer.
nDstCbCrStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411_8u_P2P3R_Ctx(const Npp8u *pSrcY, int nSrcYStep, const Npp8u *pSrcCbCr, int nSrcCbCrStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar YCbCr411 to 3 channel 8-bit unsigned planar YCbCr411 sampling format conversion.

Parameters

pSrcY – Source-Planar-Image Pointer.
nSrcYStep – Source-Planar-Image Line Step.
pSrcCbCr – Source-Planar-Image Pointer.
nSrcCbCrStep – Source-Planar-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr411ToYCbCr422


YCbCr411 to YCbCr422 sampling format conversion.


Functions


NppStatus nppiYCbCr411ToYCbCr422_8u_P3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst[3], int nDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 3 channel 8-bit unsigned planar YCbCr422 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411ToYCbCr422_8u_P3C2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 2 channel 8-bit unsigned packed YCbCr422 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411ToYCbCr422_8u_P2P3R_Ctx(const Npp8u *const pSrcY, int nSrcYStep, const Npp8u *pSrcCbCr, int nSrcCbCrStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar YCbCr411 to 3 channel 8-bit unsigned planar YCbCr422 sampling format conversion.

Parameters

pSrcY – Source-Planar-Image Pointer.
nSrcYStep – Source-Planar-Image Line Step.
pSrcCbCr – Source-Planar-Image Pointer.
nSrcCbCrStep – Source-Planar-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411ToYCbCr422_8u_P2C2R_Ctx(const Npp8u *pSrcY, int nSrcYStep, const Npp8u *pSrcCbCr, int nSrcCbCrStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar YCbCr411 to 2 channel 8-bit unsigned packed YCbCr422 sampling format conversion.

Parameters

pSrcY – Source-Planar-Image Pointer.
nSrcYStep – Source-Planar-Image Line Step.
pSrcCbCr – Source-Planar-Image Pointer.
nSrcCbCrStep – Source-Planar-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr411ToYCrCb422


YCbCr411 to YCrCb422 sampling format conversion.


Functions


NppStatus nppiYCbCr411ToYCrCb422_8u_P3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst[3], int nDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 3 channel 8-bit unsigned planar YCrCb422 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411ToYCrCb422_8u_P3C2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 2 channel 8-bit unsigned packed YCrCb422 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr411ToYCbCr420


YCbCr411 to YCbCr420 sampling format conversion.


Functions


NppStatus nppiYCbCr411ToYCbCr420_8u_P3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst[3], int nDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 3 channel 8-bit unsigned planar YCbCr420 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411ToYCbCr420_8u_P3P2R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDstY, int nDstYStep, Npp8u *pDstCbCr, int nDstCbCrStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 2 channel 8-bit unsigned planar YCbCr420 sampling format conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDstY – Destination-Planar-Image Pointer.
nDstYStep – Destination-Planar-Image Line Step.
pDstCbCr – Destination-Planar-Image Pointer.
nDstCbCrStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411ToYCbCr420_8u_P2P3R_Ctx(const Npp8u *pSrcY, int nSrcYStep, const Npp8u *pSrcCbCr, int nSrcCbCrStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar YCbCr411 to 3 channel 8-bit unsigned planar YCbCr420 sampling format conversion.

Parameters

pSrcY – Source-Planar-Image Pointer.
nSrcYStep – Source-Planar-Image Line Step.
pSrcCbCr – Source-Planar-Image Pointer.
nSrcCbCrStep – Source-Planar-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr411ToYCrCb420


YCbCr411 to YCrCb420 sampling format conversion.


Functions


NppStatus nppiYCbCr411ToYCrCb420_8u_P2P3R_Ctx(const Npp8u *pSrcY, int nSrcYStep, const Npp8u *pSrcCbCr, int nSrcCbCrStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar YCbCr411 to 3 channel 8-bit unsigned planar YCrCb420 sampling format conversion.

Parameters

pSrcY – Source-Planar-Image Pointer.
nSrcYStep – Source-Planar-Image Line Step.
pSrcCbCr – Source-Planar-Image Pointer.
nSrcCbCrStep – Source-Planar-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### NV12ToYUV420


NV12 to YUV420 color conversion.


Functions


NppStatus nppiNV12ToYUV420_8u_P2P3R_Ctx(const Npp8u *const pSrc[2], int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar NV12 to 3 channel 8-bit unsigned planar YUV420 color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array (one for Y plane, one for UV plane).
nSrcStep – Source-Planar-Image Line Step. Same value is used for each plane.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


## Color Model Conversion Functions


Routines for converting between various image color models.


### RGBToYUV


RGB to YUV color conversion.


Here is how NPP converts gamma corrected RGB or BGR to YUV. For digital RGB values in the range [0..255], Y has the range [0..255], U varies in the range [-112..+112], and V in the range [-157..+157]. To fit in the range of [0..255], a constant value of 128 is added to computed U and V values, and V is then saturated.




```
Npp32f nY =  0.299F * R + 0.587F * G + 0.114F * B;
Npp32f nU = (0.492F * ((Npp32f)nB - nY)) + 128.0F;
Npp32f nV = (0.877F * ((Npp32f)nR - nY)) + 128.0F;
if (nV > 255.0F)
    nV = 255.0F;
```


Functions


NppStatus nppiRGBToYUV_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned packed YUV color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGB with alpha to 4 channel 8-bit unsigned packed YUV color conversion with alpha, not affecting alpha.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar RGB to 3 channel 8-bit unsigned planar YUV color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned planar YUV color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV_8u_AC4P4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[4], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGB with alpha to 4 channel 8-bit unsigned planar YUV color conversion with alpha.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToYUV


BGR to YUV color conversion.


Here is how NPP converts gamma corrected RGB or BGR to YUV. For digital RGB values in the range [0..255], Y has the range [0..255], U varies in the range [-112..+112], and V in the range [-157..+157]. To fit in the range of [0..255], a constant value of 128 is added to computed U and V values, and V is then saturated.




```
Npp32f nY =  0.299F * R + 0.587F * G + 0.114F * B;
Npp32f nU = (0.492F * ((Npp32f)nB - nY)) + 128.0F;
Npp32f nV = (0.877F * ((Npp32f)nR - nY)) + 128.0F;
if (nV > 255.0F)
    nV = 255.0F;
```


Functions


NppStatus nppiBGRToYUV_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned packed YUV color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYUV_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 4 channel 8-bit unsigned packed YUV color conversion with alpha, not affecting alpha.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYUV_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar BGR to 3 channel 8-bit unsigned planar YUV color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYUV_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned planar YUV color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYUV_8u_AC4P4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[4], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 4 channel 8-bit unsigned planar YUV color conversion with alpha.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUVToRGB


YUV to RGB color conversion.


Here is how NPP converts YUV to gamma corrected RGB or BGR.




```
Npp32f nY = (Npp32f)Y;
Npp32f nU = (Npp32f)U - 128.0F;
Npp32f nV = (Npp32f)V - 128.0F;
Npp32f nR = nY + 1.140F * nV;
if (nR < 0.0F)
    nR = 0.0F;
if (nR > 255.0F)
    nR = 255.0F;
Npp32f nG = nY - 0.394F * nU - 0.581F * nV;
if (nG < 0.0F)
    nG = 0.0F;
if (nG > 255.0F)
    nG = 255.0F;
Npp32f nB = nY + 2.032F * nU;
if (nB < 0.0F)
    nB = 0.0F;
if (nB > 255.0F)
    nB = 255.0F;
```


Functions


NppStatus nppiYUVToRGB_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YUV to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUVToRGB_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit packed YUV with alpha to 4 channel 8-bit unsigned packed RGB color conversion with alpha, not affecting alpha.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUVToRGB_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV to 3 channel 8-bit unsigned planar RGB color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUVToRGB_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUVToRGBBatch


YUV to RGB batch color conversion with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input/output images provided in batches.


NPP converts YUV to gamma corrected RGB the same way as in [YUVToRGB](image_color_conversion.html#group__yuvtorgb).


Functions


NppStatus nppiYUVToRGBBatch_8u_C3R_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YUV to 3 channel 8-bit unsigned packed RGB batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input and output images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – Source-Batch-Images Pointer.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUVToRGBBatch_8u_P3C3R_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV to 3 channel 8-bit unsigned packed RGB batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input planes making input images and output packed images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of U planes. The third element of array (pSrcBatchList[2]) represents a batch of V planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – A number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUVToRGBBatchAdvanced


YUV to RGB batch color conversion where each pair of input/output images from provided batches has own [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification).


NPP converts YUV to gamma corrected RGB the same way as in [YUVToRGB](image_color_conversion.html#group__yuvtorgb).


Functions


NppStatus nppiYUVToRGBBatch_8u_C3R_Advanced_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YUV to 3 channel 8-bit unsigned packed RGB batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – Source-Batch-Images Pointer.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUVToRGBBatch_8u_P3C3R_Advanced_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV to 3 channel 8-bit unsigned packed RGB batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of U planes. The third element of array (pSrcBatchList[2]) represents a batch of V planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUVToBGR


YUV to BGR color conversion.


Here is how NPP converts YUV to gamma corrected RGB or BGR.




```
Npp32f nY = (Npp32f)Y;
Npp32f nU = (Npp32f)U - 128.0F;
Npp32f nV = (Npp32f)V - 128.0F;
Npp32f nR = nY + 1.140F * nV;
if (nR < 0.0F)
    nR = 0.0F;
if (nR > 255.0F)
    nR = 255.0F;
Npp32f nG = nY - 0.394F * nU - 0.581F * nV;
if (nG < 0.0F)
    nG = 0.0F;
if (nG > 255.0F)
    nG = 255.0F;
Npp32f nB = nY + 2.032F * nU;
if (nB < 0.0F)
    nB = 0.0F;
if (nB > 255.0F)
    nB = 255.0F;
```


Functions


NppStatus nppiYUVToBGR_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YUV to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUVToBGR_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit packed YUV with alpha to 4 channel 8-bit unsigned packed BGR color conversion with alpha, not affecting alpha.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUVToBGR_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV to 3 channel 8-bit unsigned planar BGR color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUVToBGR_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUVToBGRBatch


YUV to BGR batch color conversion with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input/output images provided in batches.


NPP converts YUV to gamma corrected BGR the same way as in [YUVToBGR](image_color_conversion.html#group__yuvtobgr).


Functions


NppStatus nppiYUVToBGRBatch_8u_C3R_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YUV to 3 channel 8-bit unsigned packed BGR batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input and output images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – Source-Batch-Images Pointer.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUVToBGRBatch_8u_P3C3R_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV to 3 channel 8-bit unsigned packed BGR batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input planes making input images and output packed images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of U planes. The third element of array (pSrcBatchList[2]) represents a batch of V planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – A number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUVToBGRBatchAdvanced


YUV to BGR batch color conversion where each pair of input/output images from provided batches has own [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification).


NPP converts YUV to gamma corrected BGR the same way as in [YUVToBGR](image_color_conversion.html#group__yuvtobgr).


Functions


NppStatus nppiYUVToBGRBatch_8u_C3R_Advanced_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YUV to 3 channel 8-bit unsigned packed BGR batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – Source-Batch-Images Pointer.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUVToBGRBatch_8u_P3C3R_Advanced_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV to 3 channel 8-bit unsigned packed BGR batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of U planes. The third element of array (pSrcBatchList[2]) represents a batch of V planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RGBToYUV422


RGB to YUV422 color conversion.


NPP converts YUV to gamma corrected BGR the same way as in [YUVToBGR](image_color_conversion.html#group__yuvtobgr).


Functions


NppStatus nppiRGBToYUV422_8u_C3C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 2 channel 8-bit unsigned packed YUV422 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV422_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar RGB to 3 channel 8-bit unsigned planar YUV422 color conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV422_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned planar YUV422 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUV422ToRGB


YUV422 to RGB color conversion.


Functions


NppStatus nppiYUV422ToRGB_8u_C2C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YUV422 to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV422ToRGB_8u_P3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV422 to 3 channel 8-bit unsigned planar RGB color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV422ToRGB_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV422 to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV422ToRGB_8u_P3AC4R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV422 to 4 channel 8-bit unsigned packed RGB color conversion with alpha.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUV422ToRGBBatch


Planar YUV422 to packed RGB batch color conversion with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input/output images provided in batches.


Functions


NppStatus nppiYUV422ToRGBBatch_8u_P3C3R_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV422 to 3 channel 8-bit unsigned packed RGB batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input planes making input images and output packed images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of U planes. The third element of array (pSrcBatchList[2]) represents a batch of V planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – A number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUV422ToRGBBatchAdvanced


Planar YUV422 to packed RGB batch color conversion where each pair of input/output images from provided batches has own [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification).


Functions


NppStatus nppiYUV422ToRGBBatch_8u_P3C3R_Advanced_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV422 to 3 channel 8-bit unsigned packed RGB batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of U planes. The third element of array (pSrcBatchList[2]) represents a batch of V planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUV422ToBGRBatch


Planar YUV422 to packed BGR batch color conversion with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input/output images provided in batches.


Functions


NppStatus nppiYUV422ToBGRBatch_8u_P3C3R_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV422 to 3 channel 8-bit unsigned packed BGR batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input planes making input images and output packed images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of U planes. The third element of array (pSrcBatchList[2]) represents a batch of V planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – A number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUV422ToBGRBatchAdvanced


Planar YUV422 to packed BGR batch color conversion where each pair of input/output images from provided batches has own [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification).


Functions


NppStatus nppiYUV422ToBGRBatch_8u_P3C3R_Advanced_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV422 to 3 channel 8-bit unsigned packed BGR batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of U planes. The third element of array (pSrcBatchList[2]) represents a batch of V planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RGBToYUV420


RGB to YUV420 color conversion.


Functions


NppStatus nppiRGBToYUV420_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar RGB to 3 channel 8-bit unsigned planar YUV420 color conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYUV420_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned planar YUV420 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUV420ToRGB


YUV420 to RGB color conversion.


Functions


NppStatus nppiYUV420ToRGB_8u_P3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV420 to 3 channel 8-bit unsigned planar RGB color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Planar-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV420ToRGB_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV420 to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV420ToRGB_8u_P3C4R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV420 to 4 channel 8-bit unsigned packed RGB color conversion with constant alpha (0xFF).

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV420ToRGB_8u_P3AC4R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV420 to 4 channel 8-bit unsigned packed RGB color conversion with alpha.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUV420ToRGBBatch


Planar YUV420 to packed RGB batch color conversion with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input/output images provided in batches.


Functions


NppStatus nppiYUV420ToRGBBatch_8u_P3C3R_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV420 to 3 channel 8-bit unsigned packed RGB batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input planes making input images and output packed images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents Y planes. The second element of array (pSrcBatchList[1]) represents U planes. The third element of array (pSrcBatchList[2]) represents V planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – A number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUV420ToRGBBatchAdvanced


Planar YUV420 to packed RGB batch color conversion where each pair of input/output images from provided batches has own [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification).


Functions


NppStatus nppiYUV420ToRGBBatch_8u_P3C3R_Advanced_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV420 to 3 channel 8-bit unsigned packed RGB batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of U planes. The third element of array (pSrcBatchList[2]) represents a batch of V planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### NV12ToRGB


NV12 to RGB color conversion.


Functions


NppStatus nppiNV12ToRGB_8u_P2C3R_Ctx(const Npp8u *const pSrc[2], int rSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar NV12 to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array (one for Y plane, one for UV plane).
rSrcStep – Source-Planar-Image Line Step. Same value is used for each source plane.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiNV12ToRGB_709HDTV_8u_P2C3R_Ctx(const Npp8u *const pSrc[2], int rSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar NV12 to 3 channel 8-bit unsigned packed RGB 709 HDTV full color conversion.
Note that HDTV conversion assumes full color range of 0 - 255, use CSC version for limited range color.

Parameters

pSrc – Source-Planar-Image Pointer Array (one for Y plane, one for UV plane).
rSrcStep – Source-Planar-Image Line Step. Same value is used for each plane.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiNV12ToRGB_709CSC_8u_P2C3R_Ctx(const Npp8u *const pSrc[2], int rSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar NV12 to 3 channel 8-bit unsigned packed RGB 709 CSC color conversion.
Note that HDTV conversion assumes full color range of 0 - 255, use CSC version for limited range color.

Parameters

pSrc – Source-Planar-Image Pointer Array (one for Y plane, one for UV plane).
rSrcStep – Source-Planar-Image Line Step. Same value is used for each plane.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### NV21ToRGB


NV21 to RGB color conversion.


Functions


NppStatus nppiNV21ToRGB_8u_P2C4R_Ctx(const Npp8u *const pSrc[2], int rSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar NV21 to 4 channel 8-bit unsigned packed RGBA color conversion with constant alpha (0xFF).

Parameters

pSrc – Source-Planar-Image Pointer Array (one for Y plane, one for VU plane).
rSrcStep – Source-Planar-Image Line Step. Same value is used for each plane.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToYUV420


BGR to YUV420 color conversion.


Functions


NppStatus nppiBGRToYUV420_8u_AC4P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned pacmed BGR with alpha to 3 channel 8-bit unsigned planar YUV420 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUV420ToBGR


YUV420 to BGR color conversion.


Functions


NppStatus nppiYUV420ToBGR_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV420 to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYUV420ToBGR_8u_P3C4R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV420 to 4 channel 8-bit unsigned packed BGR color conversion with constant alpha (0xFF).

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUV420ToBGRBatch


Planar YUV420 to packed BGR batch color conversion with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input/output images provided in batches.


Functions


NppStatus nppiYUV420ToBGRBatch_8u_P3C3R_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV420 to 3 channel 8-bit unsigned packed BGR batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input planes making input images and output packed images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents Y planes. The second element of array (pSrcBatchList[1]) represents U planes. The third element of array (pSrcBatchList[2]) represents V planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – A number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YUV420ToBGRBatchAdvanced


Planar YUV420 to packed BGR batch color conversion where each pair of input/output images from provided batches has own [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification).


Functions


NppStatus nppiYUV420ToBGRBatch_8u_P3C3R_Advanced_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YUV420 to 3 channel 8-bit unsigned packed BGR batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of U planes. The third element of array (pSrcBatchList[2]) represents a batch of V planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### NV12ToBGR


NV12 to BGR color conversion.


Functions


NppStatus nppiNV12ToBGR_8u_P2C3R_Ctx(const Npp8u *const pSrc[2], int rSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar NV12 to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array (one for Y plane, one for UV plane).
rSrcStep – Source-Planar-Image Line Step. Same value is used for each plane.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiNV12ToBGR_709HDTV_8u_P2C3R_Ctx(const Npp8u *const pSrc[2], int rSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar NV12 to 3 channel 8-bit unsigned packed RGB 709 HDTV full color conversion.
Note that HDTV conversion assumes full color range of 0 - 255, use CSC version for limited range color.

Parameters

pSrc – Source-Planar-Image Pointer Array (one for Y plane, one for UV plane).
rSrcStep – Source-Planar-Image Line Step. Same value is used for each plane.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiNV12ToBGR_709CSC_8u_P2C3R_Ctx(const Npp8u *const pSrc[2], int rSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar NV12 to 3 channel 8-bit unsigned packed RGB 709 CSC color conversion.
Note that HDTV conversion assumes full color range of 0 - 255, use CSC version for limited range color.

Parameters

pSrc – Source-Planar-Image Pointer Array (one for Y plane, one for UV plane).
rSrcStep – Source-Planar-Image Line Step. Same value is used for each plane.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### NV21ToBGR


NV21 to BGR color conversion.


Functions


NppStatus nppiNV21ToBGR_8u_P2C4R_Ctx(const Npp8u *const pSrc[2], int rSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned planar NV21 to 4 channel 8-bit unsigned packed BGRA color conversion with constant alpha (0xFF).

Parameters

pSrc – Source-Planar-Image Pointer Array (one for Y plane, one for VU plane).
rSrcStep – Source-Planar-Image Line Step. Same value is used for each plane.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RGBToYCbCr


RGB to YCbCr color conversion.


Here is how NPP converts gamma corrected RGB or BGR to YCbCr. In the YCbCr model, Y is defined to have a nominal range [16..235], while Cb and Cr are defined to have a range [16..240], with the value of 128 as corresponding to zero.




```
Npp32f nY  =  0.257F * R + 0.504F * G + 0.098F * B + 16.0F;
Npp32f nCb = -0.148F * R - 0.291F * G + 0.439F * B + 128.0F;
Npp32f nCr =  0.439F * R - 0.368F * G - 0.071F * B + 128.0F;
```


Functions


NppStatus nppiRGBToYCbCr_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel unsigned 8-bit packed YCbCr color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCbCr_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGB with alpha to 4 channel unsigned 8-bit packed YCbCr with alpha color conversion, not affecting alpha.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCbCr_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel planar 8-bit unsigned RGB to 3 channel planar 8-bit YCbCr color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCbCr_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel unsigned 8-bit planar YCbCr color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCbCr_8u_AC4P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGB with alpha to 3 channel 8-bit unsigned planar YCbCr color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCrToRGB


YCbCr to RGB color conversion.


Here is how NPP converts YCbCr to gamma corrected RGB or BGR. The output RGB values are saturated to the range [0..255].




```
Npp32f nY = 1.164F * ((Npp32f)Y - 16.0F);
Npp32f nR = ((Npp32f)Cr - 128.0F); Npp32f nB = ((Npp32f)Cb
- 128.0F); Npp32f nG = nY - 0.813F * nR - 0.392F * nB; if (nG > 255.0F)
    nG = 255.0F;
nR = nY + 1.596F * nR;
if (nR > 255.0F)
    nR = 255.0F;
nB = nY + 2.017F * nB;
if (nB > 255.0F)
    nB = 255.0F;
```


Functions


NppStatus nppiYCbCrToRGB_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YCbCr to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCrToRGB_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed YCbCr with alpha to 4 channel 8-bit unsigned packed RGB with alpha color conversion, not affecting alpha.
Alpha channel is the last channel and is not processed.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCrToRGB_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr to 3 channel 8-bit unsigned planar RGB color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCrToRGB_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCrToRGB_8u_P3C4R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nAval, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr to 4 channel 8-bit unsigned packed RGB color conversion with constant alpha.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAval – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCrToRGBBatch


YCbCr to RGB batch color conversion with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input/output images provided in batches.


NPP converts YCbCr to gamma corrected RGB the same way as in [YCbCr To RGB](image_color_conversion.html#group__ycbcrtorgb).


Functions


NppStatus nppiYCbCrToRGBBatch_8u_C3R_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YCbCr to 3 channel 8-bit unsigned packed RGB batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input and output images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – Source-Batch-Images Pointer.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCrToRGBBatch_8u_P3C3R_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr to 3 channel 8-bit unsigned packed RGB batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input planes making input images and output packed images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of Cb planes. The third element of array (pSrcBatchList[2]) represents a batch of Cr planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – A number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCrToRGBBatchAdvanced


YCbCr to RGB batch color conversion where each pair of input/output images from provided batches has own [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification).


NPP converts YCbCr to gamma corrected RGB the same way as in [YCbCr To RGB](image_color_conversion.html#group__ycbcrtorgb).


Functions


NppStatus nppiYCbCrToRGBBatch_8u_C3R_Advanced_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YCbCr to 3 channel 8-bit unsigned packed RGB batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – Source-Batch-Images Pointer.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCrToRGBBatch_8u_P3C3R_Advanced_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr to 3 channel 8-bit unsigned packed RGB batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of Cb planes. The third element of array (pSrcBatchList[2]) represents a batch of Cr planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCrToBGR


YCbCr to BGR color conversion.


Functions


NppStatus nppiYCbCrToBGR_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCrToBGR_8u_P3C4R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nAval, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr to 4 channel 8-bit unsigned packed BGR color conversion with constant alpha.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAval – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCrToBGRBatch


YCbCr to BGR batch color conversion with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input/output images provided in batches.


NPP converts YCbCr to gamma corrected BGR the same way as in [YCbCrToBGR](image_color_conversion.html#group__ycbcrtobgr).


Functions


NppStatus nppiYCbCrToBGRBatch_8u_C3R_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YCbCr to 3 channel 8-bit unsigned packed BGR batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input and output images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – Source-Batch-Images Pointer.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCrToBGRBatch_8u_P3C3R_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr to 3 channel 8-bit unsigned packed BGR batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input planes making input images and output packed images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of Cb planes. The third element of array (pSrcBatchList[2]) represents a batch of Cr planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – A number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCrToBGRBatchAdvanced


YCbCr to BGR batch color conversion where each pair of input/output images from provided batches has own [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification).


NPP converts YCbCr to gamma corrected BGR the same way as in [YCbCrToBGR](image_color_conversion.html#group__ycbcrtobgr).


Functions


NppStatus nppiYCbCrToBGRBatch_8u_C3R_Advanced_Ctx(const NppiImageDescriptor *pSrcBatchList, NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YCbCr to 3 channel 8-bit unsigned packed BGR batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – Source-Batch-Images Pointer.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCrToBGRBatch_8u_P3C3R_Advanced_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr to 3 channel 8-bit unsigned packed BGR batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of Cb planes. The third element of array (pSrcBatchList[2]) represents a batch of Cr planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCrToBGR709CSC


YCbCr to BGR_709CSC color conversion.


Functions


NppStatus nppiYCbCrToBGR_709CSC_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr to 3 channel 8-bit unsigned packed BGR_709CSC color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCrToBGR_709CSC_8u_P3C4R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nAval, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr to 4 channel 8-bit unsigned packed BGR_709CSC color conversion with constant alpha.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAval – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RGBToYCbCr422


RGB to YCbCr422 color conversion.


Functions


NppStatus nppiRGBToYCbCr422_8u_C3C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 2 channel 8-bit unsigned packed YCbCr422 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCbCr422_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned planar YCbCr422 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCbCr422_8u_P3C2R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar RGB to 2 channel 8-bit unsigned packed YCbCr422 color conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr422ToRGB


YCbCr422 to RGB color conversion.


Functions


NppStatus nppiYCbCr422ToRGB_8u_C2C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCbCr422 to 3 channel 8-bit unsigned packed RGB color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToRGB_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCbCr422 to 3 channel 8-bit unsigned planar RGB color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToRGB_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 3 channel 8-bit unsigned packed RGB color conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr422ToRGBBatch


Planar YCbCr422 to packed RGB batch color conversion with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input/output images provided in batches.


Functions


NppStatus nppiYCbCr422ToRGBBatch_8u_P3C3R_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 3 channel 8-bit unsigned packed RGB batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input planes making input images and output packed images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of Cb planes. The third element of array (pSrcBatchList[2]) represents a batch of Cr planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – A number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr422ToRGBBatchAdvanced


Planar YCbCr422 to packed RGB batch color conversion where each pair of input/output images from provided batches has own [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification).


Functions


NppStatus nppiYCbCr422ToRGBBatch_8u_P3C3R_Advanced_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 3 channel 8-bit unsigned packed RGB batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of Cb planes. The third element of array (pSrcBatchList[2]) represents a batch of Cr planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RGBToYCrCb422


RGB to YCrCb422 color conversion.


Functions


NppStatus nppiRGBToYCrCb422_8u_C3C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 2 channel 8-bit unsigned packed YCrCb422 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCrCb422_8u_P3C2R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar RGB to 2 channel 8-bit unsigned packed YCrCb422 color conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCrCb422ToRGB


YCrCb422 to RGB color conversion.


Functions


NppStatus nppiYCrCb422ToRGB_8u_C2C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCrCb422 to 3 channel 8-bit unsigned packed RGB color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCrCb422ToRGB_8u_C2P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCrCb422 to 3 channel 8-bit unsigned planar RGB color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr422ToBGR


YCbCr422 to BGR color conversion.


Functions


NppStatus nppiYCbCr422ToBGR_8u_C2C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCrCb422 to 3 channel 8-bit unsigned packed BGR color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToBGR_8u_C2C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nAval, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed YCrCb422 to 4 channel 8-bit unsigned packed BGR color conversion with constant alpha.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAval – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToBGR_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 3 channel 8-bit unsigned packed BGR color conversion.
images.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr422ToBGRBatch


Planar YCbCr422 to packed BGR batch color conversion with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input/output images provided in batches.


Functions


NppStatus nppiYCbCr422ToBGRBatch_8u_P3C3R_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 3 channel 8-bit unsigned packed BGR batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input planes making input images and output packed images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of Cb planes. The third element of array (pSrcBatchList[2]) represents a batch of Cr planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – A number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr422ToBGRBatchAdvanced


Planar YCbCr422 to packed BGR batch color conversion where each pair of input/output images from provided batches has own [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification).


Functions


NppStatus nppiYCbCr422ToBGRBatch_8u_P3C3R_Advanced_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 3 channel 8-bit unsigned packed BGR batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of Cb planes. The third element of array (pSrcBatchList[2]) represents a batch of Cr planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RGBToCbYCr422


RGB to CbYCr422 color conversion.


Functions


NppStatus nppiRGBToCbYCr422_8u_C3C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 2 channel 8-bit unsigned packed CbYCr422 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToCbYCr422Gamma_8u_C3C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB first gets forward gamma corrected then converted to 2 channel 8-bit unsigned packed CbYCr422 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### CbYCr422ToRGB


CbYCr422 to RGB color conversion.


Functions


NppStatus nppiCbYCr422ToRGB_8u_C2C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed CbYCrC22 to 3 channel 8-bit unsigned packed RGB color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToCbYCr422


BGR to CbYCr422 color conversion.


Functions


NppStatus nppiBGRToCbYCr422_8u_AC4C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 2 channel 8-bit unsigned packed CbYCr422 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToCbYCr422 709HDTV


BGR to CbYCr422_709HDTV color conversion.


Functions


NppStatus nppiBGRToCbYCr422_709HDTV_8u_C3C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 2 channel 8-bit unsigned packed CbYCr422_709HDTV color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToCbYCr422_709HDTV_8u_AC4C2R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 2 channel 8-bit unsigned packed CbYCr422_709HDTV color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### CbYCr422ToBGR


CbYCr422 to BGR color conversion.


Functions


NppStatus nppiCbYCr422ToBGR_8u_C2C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nAval, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed CbYCr422 to 4 channel 8-bit unsigned packed BGR color conversion with alpha.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAval – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### CbYCr422ToBGR 709HDTV


CbYCr422 to BGR_709HDTV color conversion.


Functions


NppStatus nppiCbYCr422ToBGR_709HDTV_8u_C2C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed CbYCr422 to 3 channel 8-bit unsigned packed BGR_709HDTV color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiCbYCr422ToBGR_709HDTV_8u_C2C4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nAval, NppStreamContext nppStreamCtx)
2 channel 8-bit unsigned packed CbYCr422 to 4 channel 8-bit unsigned packed BGR_709HDTV color conversion with constant alpha.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAval – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RGBToYCbCr420


RGB to YCbCr420 color conversion.


Functions


NppStatus nppiRGBToYCbCr420_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned planar YCbCr420 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr420ToRGB


YCbCr420 to RGB color conversion.


Functions


NppStatus nppiYCbCr420ToRGB_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr420ToRGBBatch


Planar YCbCr420 to packed RGB batch color conversion with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input/output images provided in batches.


Functions


NppStatus nppiYCbCr420ToRGBBatch_8u_P3C3R_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned packed RGB batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input planes making input images and output packed images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of Cb planes. The third element of array (pSrcBatchList[2]) represents a batch of Cr planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – A number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr420ToRGBBatchAdvanced


Planar YCbCr420 to packed RGB batch color conversion where each pair of input/output images from provided batches has own [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification).


Functions


NppStatus nppiYCbCr420ToRGBBatch_8u_P3C3R_Advanced_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned packed RGB batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of Cb planes. The third element of array (pSrcBatchList[2]) represents a batch of Cr planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RGBToYCrCb420


RGB to YCrCb420 color conversion.


Functions


NppStatus nppiRGBToYCrCb420_8u_AC4P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGB with alpha to 3 channel 8-bit unsigned planar YCrCb420 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCrCb420ToRGB


YCrCb420 to RGB color conversion.


Functions


NppStatus nppiYCrCb420ToRGB_8u_P3C4R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nAval, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCrCb420 to 4 channel 8-bit unsigned packed RGB color conversion with constant alpha.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAval – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToYCbCr420


BGR to YCbCr420 color conversion.


Functions


NppStatus nppiBGRToYCbCr420_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned planar YCbCr420 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr420_8u_AC4P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 3 channel 8-bit unsigned planar YCbCr420 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToYCbCr420 709CSC


BGR to YCbCr420_709CSC color conversion.


Functions


NppStatus nppiBGRToYCbCr420_709CSC_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned planar YCbCr420_709CSC color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr420_709CSC_8u_AC4P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 3 channel 8-bit unsigned planar YCbCr420_709CSC color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToYCbCr420 709HDTV


BGR to YCbCr420_709HDTV color conversion.


Functions


NppStatus nppiBGRToYCbCr420_709HDTV_8u_AC4P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 3 channel 8-bit unsigned planar YCbCr420_709HDTV color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToYCrCb420 709CSC


BGR to YCrCb420_709CSC color conversion.


Functions


NppStatus nppiBGRToYCrCb420_709CSC_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned planar YCrCb420_709CSC color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCrCb420_709CSC_8u_AC4P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 3 channel 8-bit unsigned planar YCrCb420_709CSC color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr420ToBGR


YCbCr420 to BGR color conversion.


Functions


NppStatus nppiYCbCr420ToBGR_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr420ToBGR_8u_P3C4R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nAval, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 4 channel 8-bit unsigned packed BGR color conversion with constant alpha.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAval – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr420ToBGRBatch


Planar YCbCr420 to packed BGR batch color conversion with a single [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification) for all pairs of input/output images provided in batches.


Functions


NppStatus nppiYCbCr420ToBGRBatch_8u_P3C3R_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned packed BGR batch color conversion for a single ROI.
Provided oSizeROI will be used for all pairs of input planes making input images and output packed images passed in pSrcBatchList and pSrcBatchList arguments. API user must ensure that provided ROI (oSizeROI) does not go beyond the borders of any of provided images.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of Cb planes. The third element of array (pSrcBatchList[2]) represents a batch of Cr planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – A number of NppiImageDescriptor structures processed in this call (must be > 1).
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr420ToBGRBatchAdvanced


Planar YCbCr420 to packed BGR batch color conversion where each pair of input/output images from provided batches has own [Region-Of-Interest (ROI)](introduction.html#nppi_conventions_lb_1roi_specification).


Functions


NppStatus nppiYCbCr420ToBGRBatch_8u_P3C3R_Advanced_Ctx(const NppiImageDescriptor *const pSrcBatchList[3], NppiImageDescriptor *pDstBatchList, int nBatchSize, NppiSize oMaxSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned packed BGR batch color conversion where each pair of input/output images has own ROI.
Provided oMaxSizeROI must contain the maximum width and the maximum height of all ROIs defined in pDstBatchList. API user must ensure that ROI from pDstBatchList for each pair of input and output images does not go beyond the borders of images in each pair.

Parameters

pSrcBatchList – An array where each element is a batch of images representing one of planes in planar images, Source-Batch-Images Pointer. The first element of array (pSrcBatchList[0]) represents a batch of Y planes. The second element of array (pSrcBatchList[1]) represents a batch of Cb planes. The third element of array (pSrcBatchList[2]) represents a batch of Cr planes.
pDstBatchList – Destination-Batch-Images Pointer.
nBatchSize – Number of NppiImageDescriptor structures processed in this call (must be > 1).
oMaxSizeROI – Region-Of-Interest (ROI), must contain the maximum width and the maximum height from all destination ROIs used for processing data.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr420ToBGR 709CSC


YCbCr420_709CSC to BGR color conversion.


Functions


NppStatus nppiYCbCr420ToBGR_709CSC_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned packed BGR_709CSC color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr420ToBGR 709HDTV


YCbCr420_709HDTV to BGR color conversion.


Functions


NppStatus nppiYCbCr420ToBGR_709HDTV_8u_P3C4R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nAval, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 4 channel 8-bit unsigned packed BGR_709HDTV color conversion with constant alpha.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAval – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToYCrCb420


BGR to YCrCb420 color conversion.


Functions


NppStatus nppiBGRToYCrCb420_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned planar YCrCb420 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCrCb420_8u_AC4P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 3 channel 8-bit unsigned planar YCrCb420 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToYCbCr411


BGR to YCbCr411 color conversion.


Functions


NppStatus nppiBGRToYCbCr411_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned planar YCbCr411 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr411_8u_AC4P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int rDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 3 channel 8-bit unsigned planar YCbCr411 color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
rDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToYCbCr


BGR to YCbCr color conversion.


Functions


NppStatus nppiBGRToYCbCr_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned planar YCbCr color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr_8u_AC4P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 3 channel 8-bit unsigned planar YCbCr color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr_8u_AC4P4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[4], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 4 channel 8-bit unsigned planar YCbCr color conversion.
images.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Planar-Image Line Step Array.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr411ToBGR


YCbCr411 to BGR color conversion.


Functions


NppStatus nppiYCbCr411ToBGR_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411ToBGR_8u_P3C4R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nAval, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 4 channel 8-bit unsigned packed BGR color conversion with constant alpha.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAval – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCbCr411ToRGB


YCbCr411 to RGB color conversion.


Functions


NppStatus nppiYCbCr411ToRGB_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411ToRGB_8u_P3C4R_Ctx(const Npp8u *const pSrc[3], int rSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, Npp8u nAval, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 4 channel 8-bit unsigned packed RGB color conversion with constant alpha.

Parameters

pSrc – Source-Planar-Image Pointer Array.
rSrcStep – Source-Planar-Image Line Step Array.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nAval – 8-bit unsigned alpha constant.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RGBToXYZ


RGB to XYZ color conversion.


Here is how NPP converts gamma corrected RGB or BGR to XYZ.




```
Npp32f nNormalizedR = (Npp32f)R * 0.003921569F; // / 255.0F
Npp32f nNormalizedG = (Npp32f)G * 0.003921569F;
Npp32f nNormalizedB = (Npp32f)B * 0.003921569F;
Npp32f nX = 0.412453F * nNormalizedR + 0.35758F  * nNormalizedG + 0.180423F * nNormalizedB;
if (nX > 1.0F)
    nX = 1.0F;
Npp32f nY = 0.212671F * nNormalizedR + 0.71516F  * nNormalizedG + 0.072169F * nNormalizedB;
if (nY > 1.0F)
    nY = 1.0F;
Npp32f nZ = 0.019334F * nNormalizedR + 0.119193F * nNormalizedG + 0.950227F * nNormalizedB;
if (nZ > 1.0F)
    nZ = 1.0F;
X = (Npp8u)(nX * 255.0F);
Y = (Npp8u)(nY * 255.0F);
Z = (Npp8u)(nZ * 255.0F);
```


Functions


NppStatus nppiRGBToXYZ_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned packed XYZ color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToXYZ_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGB with alpha to 4 channel 8-bit unsigned packed XYZ with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### XYZToRGB


XYZ to RGB color conversion.


Here is how NPP converts XYZ to gamma corrected RGB or BGR. The code assumes that X,Y, and Z values are in the range [0..1].




```
Npp32f nNormalizedX = (Npp32f)X * 0.003921569F; // / 255.0F
Npp32f nNormalizedY = (Npp32f)Y * 0.003921569F;
Npp32f nNormalizedZ = (Npp32f)Z * 0.003921569F;
Npp32f nR = 3.240479F * nNormalizedX - 1.53715F  * nNormalizedY - 0.498535F * nNormalizedZ;
if (nR > 1.0F)
    nR = 1.0F;
Npp32f nG = -0.969256F * nNormalizedX + 1.875991F  * nNormalizedY + 0.041556F * nNormalizedZ;
if (nG > 1.0F)
    nG = 1.0F;
Npp32f nB = 0.055648F * nNormalizedX - 0.204043F * nNormalizedY + 1.057311F * nNormalizedZ;
if (nB > 1.0F)
    nB = 1.0F;
R = (Npp8u)(nR * 255.0F);
G = (Npp8u)(nG * 255.0F);
B = (Npp8u)(nB * 255.0F);
```


Functions


NppStatus nppiXYZToRGB_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed XYZ to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiXYZToRGB_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed XYZ with alpha to 4 channel 8-bit unsigned packed RGB with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RGBToLUV


RGB to LUV color conversion.


Here is how NPP converts gamma corrected RGB or BGR to CIE LUV using the CIE XYZ D65 white point with a Y luminance of 1.0. The computed values of the L component are in the range [0..100], U component in the range [-134..220], and V component in the range [-140..122]. The code uses cbrtf() the 32 bit floating point cube root math function.




```
// use CIE D65 chromaticity coordinates
#define nCIE_XYZ_D65_xn 0.312713F
#define nCIE_XYZ_D65_yn 0.329016F
#define nn_DIVISOR (-2.0F * nCIE_XYZ_D65_xn + 12.0F * nCIE_XYZ_D65_yn + 3.0F)
#define nun (4.0F * nCIE_XYZ_D65_xn / nn_DIVISOR)
#define nvn (9.0F * nCIE_XYZ_D65_yn / nn_DIVISOR)

// First convert to XYZ
Npp32f nNormalizedR = (Npp32f)R * 0.003921569F; // / 255.0F
Npp32f nNormalizedG = (Npp32f)G * 0.003921569F;
Npp32f nNormalizedB = (Npp32f)B * 0.003921569F;
Npp32f nX = 0.412453F * nNormalizedR + 0.35758F  * nNormalizedG + 0.180423F * nNormalizedB;
Npp32f nY = 0.212671F * nNormalizedR + 0.71516F  * nNormalizedG + 0.072169F * nNormalizedB;
Npp32f nZ = 0.019334F * nNormalizedR + 0.119193F * nNormalizedG + 0.950227F * nNormalizedB;
// Now calculate LUV from the XYZ value
Npp32f nTemp = nX + 15.0F * nY + 3.0F * nZ;
Npp32f nu = 4.0F * nX / nTemp;
Npp32f nv = 9.0F * nY / nTemp;
Npp32f nL = 116.0F * cbrtf(nY) - 16.0F;
if (nL < 0.0F)
    nL = 0.0F;
if (nL > 100.0F)
    nL = 100.0F;
nTemp = 13.0F * nL;
Npp32f nU = nTemp * (nu - nun);
if (nU < -134.0F)
    nU = -134.0F;
if (nU > 220.0F)
    nU = 220.0F;
Npp32f nV = nTemp * (nv - nvn);
if (nV < -140.0F)
    nV = -140.0F;
if (nV > 122.0F)
    nV = 122.0F;
L = (Npp8u)(nL * 255.0F * 0.01F); // / 100.0F
U = (Npp8u)((nU + 134.0F) * 255.0F * 0.0028249F); // / 354.0F
V = (Npp8u)((nV + 140.0F) * 255.0F * 0.0038168F); // / 262.0F
```


Functions


NppStatus nppiRGBToLUV_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned packed LUV color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToLUV_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGB with alpha to 4 channel 8-bit unsigned packed LUV with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### LUVToRGB


LUV to RGB color conversion.


Here is how NPP converts CIE LUV to gamma corrected RGB or BGR using the CIE XYZ D65 white point with a Y luminance of 1.0. The code uses powf() the 32 bit floating point power math function.




```
// use CIE D65 chromaticity coordinates
#define nCIE_XYZ_D65_xn 0.312713F
#define nCIE_XYZ_D65_yn 0.329016F
#define nn_DIVISOR (-2.0F * nCIE_XYZ_D65_xn + 12.0F * nCIE_XYZ_D65_yn + 3.0F)
#define nun (4.0F * nCIE_XYZ_D65_xn / nn_DIVISOR)
#define nvn (9.0F * nCIE_XYZ_D65_yn / nn_DIVISOR)

// First convert normalized LUV back to original CIE LUV range
Npp32f nL = (Npp32f)L * 100.0F * 0.003921569F;  // / 255.0F
Npp32f nU = ((Npp32f)U * 354.0F * 0.003921569F) - 134.0F;
Npp32f nV = ((Npp32f)V * 262.0F * 0.003921569F) - 140.0F;
// Now convert LUV to CIE XYZ
Npp32f nTemp = 13.0F * nL;
Npp32f nu = nU / nTemp + nun;
Npp32f nv = nV / nTemp + nvn;
Npp32f nNormalizedY;
if (nL > 7.9996248F)
{
    nNormalizedY = (nL + 16.0F) * 0.008621F; // / 116.0F
    nNormalizedY = powf(nNormalizedY, 3.0F);
}
else
{
    nNormalizedY = nL * 0.001107F; // / 903.3F
}
Npp32f nNormalizedX = (-9.0F * nNormalizedY * nu) / ((nu - 4.0F) * nv - nu * nv);
Npp32f nNormalizedZ = (9.0F * nNormalizedY - 15.0F * nv * nNormalizedY - nv * nNormalizedX) / (3.0F * nv);
Npp32f nR = 3.240479F * nNormalizedX - 1.53715F  * nNormalizedY - 0.498535F * nNormalizedZ;
if (nR > 1.0F)
    nR = 1.0F;
if (nR < 0.0F)
    nR = 0.0F;
Npp32f nG = -0.969256F * nNormalizedX + 1.875991F  * nNormalizedY + 0.041556F * nNormalizedZ;
if (nG > 1.0F)
    nG = 1.0F;
if (nG < 0.0F)
    nG = 0.0F;
Npp32f nB = 0.055648F * nNormalizedX - 0.204043F * nNormalizedY + 1.057311F * nNormalizedZ;
if (nB > 1.0F)
    nB = 1.0F;
if (nB < 0.0F)
    nB = 0.0F;
R = (Npp8u)(nR * 255.0F);
G = (Npp8u)(nG * 255.0F);
B = (Npp8u)(nB * 255.0F);
```


Functions


NppStatus nppiLUVToRGB_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed LUV to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiLUVToRGB_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed LUV with alpha to 4 channel 8-bit unsigned packed RGB with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToLab


BGR to Lab color conversion.


This is how NPP converts gamma corrected BGR or RGB to Lab using the CIE Lab D65 white point with a Y luminance of 1.0. The computed values of the L component are in the range [0..100], a and b component values are in the range [-128..127]. The code uses cbrtf() the 32 bit floating point cube root math function.




```
// use CIE Lab chromaticity coordinates
#define nCIE_LAB_D65_xn 0.950455F
#define nCIE_LAB_D65_yn 1.0F
#define nCIE_LAB_D65_zn 1.088753F
// First convert to XYZ
Npp32f nNormalizedR = (Npp32f)R * 0.003921569F; // / 255.0F
Npp32f nNormalizedG = (Npp32f)G * 0.003921569F;
Npp32f nNormalizedB = (Npp32f)B * 0.003921569F;
Npp32f nX = 0.412453F * nNormalizedR + 0.35758F  * nNormalizedG + 0.180423F * nNormalizedB;
Npp32f nY = 0.212671F * nNormalizedR + 0.71516F  * nNormalizedG + 0.072169F * nNormalizedB;
Npp32f nZ = 0.019334F * nNormalizedR + 0.119193F * nNormalizedG + 0.950227F * nNormalizedB;
Npp32f nL = cbrtf(nY);
Npp32f nA; Npp32f nB; Npp32f nfX = nX * 1.052128F; // / nCIE_LAB_D65_xn; Npp32f nfY = nY; Npp32f nfZ = nZ * 0.918482F; // /
nCIE_LAB_D65_zn; nfY = nL - 16.0F; nL = 116.0F * nL - 16.0F; nA = cbrtf(nfX) - 16.0F; nA = 500.0F
* (nA - nfY); nB = cbrtf(nfZ) - 16.0F; nB = 200.0F * (nfY - nB); // Now scale Lab range nL = nL * 255.0F
* 0.01F; // / 100.0F nA = nA + 128.0F; nB = nB + 128.0F; L = (Npp8u)nL; a = (Npp8u)nA; b = (Npp8u)nB;
```


Functions


NppStatus nppiBGRToLab_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned packed Lab color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### LabToBGR


Lab to BGR color conversion.


This is how NPP converts Lab to gamma corrected BGR or RGB using the CIE Lab D65 white point with a Y luminance of 1.0. The code uses powf() the 32 bit floating point power math function.




```
// use CIE Lab chromaticity coordinates
#define nCIE_LAB_D65_xn 0.950455F
#define nCIE_LAB_D65_yn 1.0F
#define nCIE_LAB_D65_zn 1.088753F
// First convert Lab back to original range then to CIE XYZ
Npp32f nL = (Npp32f)L * 100.0F * 0.003921569F;  // / 255.0F
Npp32f nA = (Npp32f)a - 128.0F;
Npp32f nB = (Npp32f)b - 128.0F;
Npp32f nP = (nL + 16.0F) * 0.008621F; // / 116.0F
Npp32f nNormalizedY = nP * nP * nP; // powf(nP, 3.0F);
Npp32f nNormalizedX = nCIE_LAB_D65_xn * powf((nP + nA * 0.002F), 3.0F); // / 500.0F
Npp32f nNormalizedZ = nCIE_LAB_D65_zn * powf((nP - nB * 0.005F), 3.0F); // / 200.0F
Npp32f nR = 3.240479F * nNormalizedX - 1.53715F  * nNormalizedY - 0.498535F * nNormalizedZ;
if (nR > 1.0F)
    nR = 1.0F;
Npp32f nG = -0.969256F * nNormalizedX + 1.875991F  * nNormalizedY + 0.041556F * nNormalizedZ;
if (nG > 1.0F)
    nG = 1.0F;
nB = 0.055648F * nNormalizedX - 0.204043F * nNormalizedY + 1.057311F * nNormalizedZ;
if (nB > 1.0F)
    nB = 1.0F;
R = (Npp8u)(nR * 255.0F);
G = (Npp8u)(nG * 255.0F);
B = (Npp8u)(nB * 255.0F);
```


Functions


NppStatus nppiLabToBGR_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed Lab to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RGBToYCC


RGB to PhotoYCC color conversion.


This is how NPP converts gamma corrected BGR or RGB to PhotoYCC. The computed Y, C1, C2 values are then quantized and converted to fit in the range [0..1] before expanding to 8 bits.




```
Npp32f nNormalizedR = (Npp32f)R * 0.003921569F; // / 255.0F
Npp32f nNormalizedG = (Npp32f)G * 0.003921569F;
Npp32f nNormalizedB = (Npp32f)B * 0.003921569F;
Npp32f nY = 0.299F * nNormalizedR + 0.587F  * nNormalizedG + 0.114F * nNormalizedB;
Npp32f nC1 = nNormalizedB - nY;
nC1 = 111.4F * 0.003921569F * nC1 + 156.0F * 0.003921569F;
Npp32f nC2 = nNormalizedR - nY;
nC2 = 135.64F * 0.003921569F * nC2 + 137.0F * 0.003921569F;
nY = 1.0F * 0.713267F * nY; // / 1.402F
Y = (Npp8u)(nY  * 255.0F);
C1 = (Npp8u)(nC1 * 255.0F);
C2 = (Npp8u)(nC2 * 255.0F);
```


Functions


NppStatus nppiRGBToYCC_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned packed YCC color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCC_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGB with alpha to 4 channel 8-bit unsigned packed YCC with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCCToRGB


PhotoYCC to RGB color conversion.


This is how NPP converts PhotoYCC to gamma corrected RGB or BGR.




```
Npp32f nNormalizedY  = ((Npp32f)Y * 0.003921569F) * 1.3584F;  // / 255.0F
Npp32f nNormalizedC1 = (((Npp32f)C1 * 0.003921569F) - 156.0F * 0.003921569F) * 2.2179F;
Npp32f nNormalizedC2 = (((Npp32f)C2 * 0.003921569F) - 137.0F * 0.003921569F) * 1.8215F;
Npp32f nR = nNormalizedY + nNormalizedC2;
if (nR > 1.0F)
    nR = 1.0F;
Npp32f nG = nNormalizedY - 0.194F  * nNormalizedC1 - 0.509F * nNormalizedC2;
if (nG > 1.0F)
    nG = 1.0F;
Npp32f nB = nNormalizedY + nNormalizedC1;
if (nB > 1.0F)
    nB = 1.0F;
R = (Npp8u)(nR * 255.0F);
G = (Npp8u)(nG * 255.0F);
B = (Npp8u)(nB * 255.0F);
```


Functions


NppStatus nppiYCCToRGB_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YCC to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCCToRGB_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed YCC with alpha to 4 channel 8-bit unsigned packed RGB with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCCKToCMYK_JPEG


This function partially converts JPEG YCCK to CMYK.


This is how NPP converts JPEG YCCK to CMYK. NPP only performs and initial YCC to RGB conversion using the 601 conversion coefficients and the RGB to CMY inversion leaving K unmodified. To complete this conversion to useful RGB values an additional RGB conversion needs to follow this function using the color profile contained in the YCCK JPEG file metadata section. NPP does not directly support this conversion but potentially nppiColorTwist can be used to perform it once the conversion coefficients are known.




```
Npp32f nY  = static_cast<Npp32f>(Y);
Npp32f nC1 = static_cast<Npp32f>(Cb);
Npp32f nC2 = static_cast<Npp32f>(Cr);
Npp32f nR = nY + 1.402F * nC2 - 179.456F;
Npp32f nG = nY - 0.34414F * nC1 - 0.71414F * nC2 + 135.45984F;
Npp32f nB = nY + 1.772F * nC1 - 226.816F;

Npp8u nC = static_cast<Npp8u>(255.0F - nR);
Npp8u nM = static_cast<Npp8u>(255.0F - nG);
Npp8u nM = static_cast<Npp8u>(255.0F - nB);
Npp8u nK = K;
```


Functions


NppStatus nppiYCCKToCMYK_JPEG_601_8u_P4R_Ctx(const Npp8u *pSrc[4], int nSrcStep, Npp8u *pDst[4], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned planar JPEG YCCK color format to 4 channel 8-bit unsigned planar CMYK color conversion using 601 RGB color coefficients and CMY inversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### CMYKOrYCCKJPEGToRGB


These functions convert JPEG CMYK or YCCK color format images to either planar or packed RGB images for images which need no color profile conversion.


Functions


NppStatus nppiCMYKOrYCCKToRGB_JPEG_8u_P4P3R_Ctx(const Npp8u *pSrc[4], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned planar JPEG CMYK or YCCK color model image to 3 channel 8-bit unsigned planar RGB color model image without color profile conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiCMYKOrYCCKToRGB_JPEG_8u_P4C3R_Ctx(const Npp8u *pSrc[4], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned planar JPEG CMYK or YCCK color model image to 3 channel 8-bit unsigned packed RGB color model image without color profile conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### YCCKJPEGOrCMYKToBGR


These functions convert JPEG CMYK or YCCK color format images to either planar or packed BGR images for images which need no color profile conversion.


Functions


NppStatus nppiCMYKOrYCCKToBGR_JPEG_8u_P4P3R_Ctx(const Npp8u *pSrc[4], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned planar JPEG CMYK or YCCK color model image to 3 channel 8-bit unsigned planar BGR color model image without color profile conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiCMYKOrYCCKToBGR_JPEG_8u_P4C3R_Ctx(const Npp8u *pSrc[4], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned planar JPEG CMYK or YCCK color model image to 3 channel 8-bit unsigned packed BGR color model image without color profile conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RGBToHLS


RGB to HLS color conversion.


This is how NPP converts gamma corrected RGB or BGR to HLS. This code uses the fmaxf() and fminf() 32 bit floating point math functions.




```
Npp32f nNormalizedR = (Npp32f)R * 0.003921569F;  // / 255.0F
Npp32f nNormalizedG = (Npp32f)G * 0.003921569F;
Npp32f nNormalizedB = (Npp32f)B * 0.003921569F;
Npp32f nS;
Npp32f nH;
// Lightness
Npp32f nMax = fmaxf(nNormalizedR, nNormalizedG);
       nMax = fmaxf(nMax, nNormalizedB);
Npp32f nMin = fminf(nNormalizedR, nNormalizedG);
       nMin = fminf(nMin, nNormalizedB);
Npp32f nL = (nMax + nMin) * 0.5F;
Npp32f nDivisor = nMax - nMin;
// Saturation
if (nDivisor == 0.0F) // achromatics case
{
    nS = 0.0F;
    nH = 0.0F;
}
else // chromatics case
{
    if (nL > 0.5F)
        nS = nDivisor / (1.0F - (nMax + nMin - 1.0F));
    else
        nS = nDivisor / (nMax + nMin);
}
// Hue
Npp32f nCr = (nMax - nNormalizedR) / nDivisor;
Npp32f nCg = (nMax - nNormalizedG) / nDivisor;
Npp32f nCb = (nMax - nNormalizedB) / nDivisor;
if (nNormalizedR == nMax)
    nH = nCb - nCg;
else if (nNormalizedG == nMax)
    nH = 2.0F + nCr - nCb;
else if (nNormalizedB == nMax)
    nH = 4.0F + nCg - nCr;
nH = nH * 0.166667F; // / 6.0F
if (nH < 0.0F)
    nH = nH + 1.0F;
H = (Npp8u)(nH * 255.0F);
L = (Npp8u)(nL * 255.0F);
S = (Npp8u)(nS * 255.0F);
```


Functions


NppStatus nppiRGBToHLS_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned packed HLS color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToHLS_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGB with alpha to 4 channel 8-bit unsigned packed HLS with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### HLSToRGB


HLS to RGB color conversion.


This is how NPP converts HLS to gamma corrected RGB or BGR.




```
Npp32f nNormalizedH = (Npp32f)H * 0.003921569F;  // / 255.0F
Npp32f nNormalizedL = (Npp32f)L * 0.003921569F;
Npp32f nNormalizedS = (Npp32f)S * 0.003921569F;
Npp32f nM1;
Npp32f nM2;
Npp32f nR;
Npp32f nG;
Npp32f nB;
Npp32f nh = 0.0F;
if (nNormalizedL <= 0.5F)
    nM2 = nNormalizedL * (1.0F + nNormalizedS);
else
    nM2 = nNormalizedL + nNormalizedS - nNormalizedL * nNormalizedS;
nM1 = 2.0F * nNormalizedL - nM2;
if (nNormalizedS == 0.0F)
    nR = nG = nB = nNormalizedL;
else
{
    nh = nNormalizedH + 0.3333F;
    if (nh > 1.0F)
        nh -= 1.0F;
}
Npp32f nMDiff = nM2 - nM1;
if (0.6667F < nh)
    nR = nM1;
else
{
    if (nh < 0.1667F)
        nR = (nM1 + nMDiff * nh * 6.0F); // / 0.1667F
    else if (nh < 0.5F)
        nR = nM2;
    else
        nR = nM1 + nMDiff * ( 0.6667F - nh ) * 6.0F; // / 0.1667F
}
if (nR > 1.0F)
    nR = 1.0F;
nh = nNormalizedH;
if (0.6667F < nh)
    nG = nM1;
else
{
    if (nh < 0.1667F)
        nG = (nM1 + nMDiff * nh * 6.0F); // / 0.1667F
    else if (nh < 0.5F)
        nG = nM2;
    else
        nG = nM1 + nMDiff * (0.6667F - nh ) * 6.0F; // / 0.1667F
}
if (nG > 1.0F)
    nG = 1.0F;
nh = nNormalizedH - 0.3333F;
if (nh < 0.0F)
    nh += 1.0F;
if (0.6667F < nh)
    nB = nM1;
else
{
    if (nh < 0.1667F)
        nB = (nM1 + nMDiff * nh * 6.0F); // / 0.1667F
    else if (nh < 0.5F)
        nB = nM2;
    else
        nB = nM1 + nMDiff * (0.6667F - nh ) * 6.0F; // / 0.1667F
}
if (nB > 1.0F)
    nB = 1.0F;
R = (Npp8u)(nR * 255.0F);
G = (Npp8u)(nG * 255.0F);
B = (Npp8u)(nB * 255.0F);
```


Functions


NppStatus nppiHLSToRGB_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed HLS to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiHLSToRGB_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed HLS with alpha to 4 channel 8-bit unsigned packed RGB with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### BGRToHLS


BGR to HLS color conversion.


Functions


NppStatus nppiBGRToHLS_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 4 channel 8-bit unsigned packed HLS with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToHLS_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned planar HLS color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToHLS_8u_AC4P4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[4], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed BGR with alpha to 4 channel 8-bit unsigned planar HLS with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToHLS_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar BGR to 3 channel 8-bit unsigned packed HLS color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToHLS_8u_AP4C4R_Ctx(const Npp8u *const pSrc[4], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned planar BGR with alpha to 4 channel 8-bit unsigned packed HLS with alpha color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToHLS_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar BGR to 3 channel 8-bit unsigned planar HLS color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToHLS_8u_AP4R_Ctx(const Npp8u *const pSrc[4], int nSrcStep, Npp8u *pDst[4], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned planar BGR with alpha to 4 channel 8-bit unsigned planar HLS with alpha color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### HLSToBGR


HLS to BGR color conversion.


Functions


NppStatus nppiHLSToBGR_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed HLS to 3 channel 8-bit unsigned planar BGR color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiHLSToBGR_8u_AC4P4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[4], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed HLS with alpha to 4 channel 8-bit unsigned planar BGR with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiHLSToBGR_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar HLS to 3 channel 8-bit unsigned planar BGR color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiHLSToBGR_8u_AP4R_Ctx(const Npp8u *const pSrc[4], int nSrcStep, Npp8u *pDst[4], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned planar HLS with alpha to 4 channel 8-bit unsigned planar BGR with alpha color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Planar-Image Pointer Array.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiHLSToBGR_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar HLS to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiHLSToBGR_8u_AP4C4R_Ctx(const Npp8u *const pSrc[4], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned planar HLS with alpha to 4 channel 8-bit unsigned packed BGR with alpha color conversion.

Parameters

pSrc – Source-Planar-Image Pointer Array.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### RBGToHSV


RGB to HSV color conversion.


This is how NPP converts gamma corrected RGB or BGR to HSV. This code uses the fmaxf() and fminf() 32 bit floating point math functions.




```
Npp32f nNormalizedR = (Npp32f)R * 0.003921569F; // / 255.0F
Npp32f nNormalizedG = (Npp32f)G * 0.003921569F;
Npp32f nNormalizedB = (Npp32f)B * 0.003921569F;
Npp32f nS;
Npp32f nH;
// Value
Npp32f nV = fmaxf(nNormalizedR, nNormalizedG);
       nV = fmaxf(nV, nNormalizedB);
// Saturation
Npp32f nTemp = fminf(nNormalizedR, nNormalizedG);
       nTemp = fminf(nTemp, nNormalizedB);
Npp32f nDivisor = nV - nTemp;
if (nV == 0.0F) // achromatics case
{
    nS = 0.0F;
    nH = 0.0F;
}
else // chromatics case
    nS = nDivisor / nV;
// Hue:
Npp32f nCr = (nV - nNormalizedR) / nDivisor;
Npp32f nCg = (nV - nNormalizedG) / nDivisor;
Npp32f nCb = (nV - nNormalizedB) / nDivisor;
if (nNormalizedR == nV)
    nH = nCb - nCg;
else if (nNormalizedG == nV)
    nH = 2.0F + nCr - nCb;
else if (nNormalizedB == nV)
    nH = 4.0F + nCg - nCr;
nH = nH * 0.166667F; // / 6.0F
if (nH < 0.0F)
    nH = nH + 1.0F;
H = (Npp8u)(nH * 255.0F);
S = (Npp8u)(nS * 255.0F);
V = (Npp8u)(nV * 255.0F);
```


Functions


NppStatus nppiRGBToHSV_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned packed HSV color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToHSV_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed RGB with alpha to 4 channel 8-bit unsigned packed HSV with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### HSVToRGB


HSV to RGB color conversion.


This is how NPP converts HSV to gamma corrected RGB or BGR. This code uses the floorf() 32 bit floating point math function.




```
Npp32f nNormalizedH = (Npp32f)H * 0.003921569F; // / 255.0F
Npp32f nNormalizedS = (Npp32f)S * 0.003921569F;
Npp32f nNormalizedV = (Npp32f)V * 0.003921569F;
Npp32f nR;
Npp32f nG;
Npp32f nB;
if (nNormalizedS == 0.0F)
{
    nR = nG = nB = nNormalizedV;
}
else
{
    if (nNormalizedH == 1.0F)
        nNormalizedH = 0.0F;
    else
        nNormalizedH = nNormalizedH * 6.0F; // / 0.1667F
}
Npp32f nI = floorf(nNormalizedH);
Npp32f nF = nNormalizedH - nI;
Npp32f nM = nNormalizedV * (1.0F - nNormalizedS);
Npp32f nN = nNormalizedV * (1.0F - nNormalizedS * nF);
Npp32f nK = nNormalizedV * (1.0F - nNormalizedS * (1.0F - nF));
if (nI == 0.0F)
    { nR = nNormalizedV; nG = nK; nB = nM; }
else if (nI == 1.0F)
    { nR = nN; nG = nNormalizedV; nB = nM; }
else if (nI == 2.0F)
    { nR = nM; nG = nNormalizedV; nB = nK; }
else if (nI == 3.0F)
    { nR = nM; nG = nN; nB = nNormalizedV; }
else if (nI == 4.0F)
    { nR = nK; nG = nM; nB = nNormalizedV; }
else if (nI == 5.0F)
    { nR = nNormalizedV; nG = nM; nB = nN; }
R = (Npp8u)(nR * 255.0F);
G = (Npp8u)(nG * 255.0F);
B = (Npp8u)(nB * 255.0F);
```


Functions


NppStatus nppiHSVToRGB_8u_C3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed HSV to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiHSVToRGB_8u_AC4R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
4 channel 8-bit unsigned packed HSV with alpha to 4 channel 8-bit unsigned packed RGB with alpha color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


### JPEG Color Conversion


The set of JPEG color conversion functions available in the library.


RGBToYCbCr_JPEG Planar to planar.


JPEG RGB to YCbCr color conversion.


NppStatus nppiRGBToYCbCr420_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar RGB to 3 channel 8-bit unsigned planar YCbCr420 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCbCr422_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar RGB to 3 channel 8-bit unsigned planar YCbCr422 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCbCr411_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar RGB to 3 channel 8-bit unsigned planar YCbCr411 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCbCr444_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar RGB to 3 channel 8-bit unsigned planar YCbCr444 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr420_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar BGR to 3 channel 8-bit unsigned planar YCbCr420 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr422_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar BGR to 3 channel 8-bit unsigned planar YCbCr422 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr411_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar BGR to 3 channel 8-bit unsigned planar YCbCr411 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr444_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar BGR to 3 channel 8-bit unsigned planar YCbCr444 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr420ToRGB_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned planar RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToRGB_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 3 channel 8-bit unsigned planar RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411ToRGB_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 3 channel 8-bit unsigned planar RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr444ToRGB_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr444 to 3 channel 8-bit unsigned planar RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr420ToBGR_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned planar BGR color conversion.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToBGR_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 3 channel 8-bit unsigned planar BGR color conversion.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411ToBGR_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 3 channel 8-bit unsigned planar BGR color conversion.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr444ToBGR_JPEG_8u_P3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr444 to 3 channel 8-bit unsigned planar BGR color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


RGBToYCbCr_JPEG Planar to packed.


JPEG RGB to YCbCr color conversion.


NppStatus nppiRGBToYCbCr420_JPEG_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned planar YCbCr420 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCbCr422_JPEG_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned planar YCbCr422 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCbCr411_JPEG_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned planar YCbCr411 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiRGBToYCbCr444_JPEG_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed RGB to 3 channel 8-bit unsigned planar YCbCr444 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr420_JPEG_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned planar YCbCr420 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr422_JPEG_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned planar YCbCr422 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr411_JPEG_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int aDstStep[3], NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned planar YCbCr411 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
aDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiBGRToYCbCr444_JPEG_8u_C3P3R_Ctx(const Npp8u *pSrc, int nSrcStep, Npp8u *pDst[3], int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed BGR to 3 channel 8-bit unsigned planar YCbCr444 color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr420ToRGB_JPEG_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YCbCr420 to 3 channel 8-bit unsigned planar RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToRGB_JPEG_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YCbCr422 to 3 channel 8-bit unsigned planar RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411ToRGB_JPEG_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned packed YCbCr411 to 3 channel 8-bit unsigned planar RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr444ToRGB_JPEG_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr444 to 3 channel 8-bit unsigned packed RGB color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr420ToBGR_JPEG_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr420 to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr422ToBGR_JPEG_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr422 to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr411ToBGR_JPEG_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int aSrcStep[3], Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr411 to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Image Pointer.
aSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiYCbCr444ToBGR_JPEG_8u_P3C3R_Ctx(const Npp8u *const pSrc[3], int nSrcStep, Npp8u *pDst, int nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
3 channel 8-bit unsigned planar YCbCr444 to 3 channel 8-bit unsigned packed BGR color conversion.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes