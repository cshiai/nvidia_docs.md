# Private Image Filtering Functions


Private filtering functions.


It is the user’s responsibility to avoid [Sampling Beyond Image Boundaries](introduction.html#nppi_conventions_lb_1sampling_beyond_image_boundaries).


These functions can be found in the nppif library. Linking to only the sub-libraries that you use can significantly save link time, application load time, and CUDA runtime startup time when using dynamic libraries.


## Image CuLitho Filters


### cuLithoFilters


The set of cuLitho private image functions available in the library.


FilterLocalCurvatureBorder


Computes the local pixel neighborhood curvature via Arridge formula


NppStatus nppiFilterLocalCurvatureBorder_32f_C1R_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppStreamContext nppStreamCtx)
Single channel 32-bit floating point local curvature calculation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


AccumulateWeightedSquare


Computes the squared sum of pixel


NppStatus nppiAccumulateWeightedSquare_32f_C1IR_Ctx(const Npp32f *pSrc, Npp32s nSrcStep, Npp32f *pAccBuffer, Npp32s nAccStep, NppiSize oSizeROI, Npp32f nSrcWeight, NppStreamContext nppStreamCtx)
Single channel 32-bit floating point in-place accumulate weighted square.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
pAccBuffer – accumulation_image_pointer.
nAccStep – accumulation_image_line_step.
oSizeROI – Region-Of-Interest (ROI).
nSrcWeight – source_image_weight.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


SampleImagePoints


Given a list of coordinates, this will sample the provided image (with bilinear interpolation) and produce a list of values for those points inside the ROI


NppStatus nppiSampleImagePoints_32f_C1R_Ctx(Npp32f *pSrc, Npp32s nSrcStep, NppiSize oSizeROI, NppiPoint64f *pXYCoordinateArray, Npp32s nCoordinateCount, Npp32f *pDstDataArray, NppStreamContext nppStreamCtx)
Single channel 32-bit pixel sampling function, uses bilinear interpolation.

Parameters

pSrc – Source-Image Pointer.
nSrcStep – Source-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pXYCoordinateArray – list of NppiPoint64fs to sample in the image.
nCoordinateCount – number of points in the pXYCoordinateArray.
pDstDataArray – output array for sampled pixel values.
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


SetImagePoints


Given a list of coordinates, this will set pixels in the provided image with values provided for those points inside the ROI


NppStatus nppiSetImagePoints_32f_C1R_Ctx(Npp32f *pDst, Npp32s nDstStep, NppiSize oSizeROI, NppiPoint64f *pXYCoordinateArray, Npp32s nCoordinateCount, Npp32f *pSrcDataArray, NppStreamContext nppStreamCtx)
Single channel 32-bit pixel set function.

Parameters

pDst – Destination-Image Pointer.
nDstStep – Destination-Image Line Step.
oSizeROI – Region-Of-Interest (ROI).
pXYCoordinateArray – list of NppiPoint64fs to set in the image.
nCoordinateCount – number of points in the pXYCoordinateArray.
pSrcDataArray – source array for pixel values to be written
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


ComputeCurvature


Given an array of NppiContourBlockSegmenst, for each contour specified this computes the inverse square radius of curvature for each point along that contour for those points inside the ROI


NppStatus nppiComputeCurvature_64f_Ctx(NppiPoint64f *pContoursPointList, Npp32u nTotalContourPointCount, NppiContourBlockSegment *pContourBlockSegmentList, Npp32u nFirstContourGeometryListID, Npp32u nLastContourGeometryListID, NppiSize oSizeROI, Npp32u nAdjacentPixels, Npp32f *pComputedContourPointCurvatureDev, NppStreamContext nppStreamCtx)
Measure inverse radius squared curvature along contours.

Parameters

pContoursPointList – pointer to device memory array of NppiPoint64f
nTotalContourPointCount – count of number of points in pContoursPointList
pContourBlockSegmentList – pointer to array of NppiContourBlockSegment objects
nFirstContourGeometryListID – the ID of the first contour geometry list to output.
nLastContourGeometryListID – the ID of the last contour geometry list to output
oSizeROI – Region-Of-Interest (ROI).
nAdjacentPixels – how far away in a contour to find adjacent points to use to compute radius
pComputedContourPointCurvatureDev – output array for computed values
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiComputeCurvature_32f_Ctx(NppiPoint32f *pContoursPointList, Npp32u nTotalContourPointCount, NppiContourBlockSegment *pContourBlockSegmentList, Npp32u nFirstContourGeometryListID, Npp32u nLastContourGeometryListID, NppiSize oSizeROI, Npp32u nAdjacentPixels, Npp32f *pComputedContourPointCurvatureDev, NppStreamContext nppStreamCtx)
Measure inverse radius squared curvature along contours.

Parameters

pContoursPointList – pointer to device memory array of NppiPoint32f
nTotalContourPointCount – count of number of points in pContoursPointList
pContourBlockSegmentList – pointer to array of NppiContourBlockSegment objects
nFirstContourGeometryListID – the ID of the first contour geometry list to output.
nLastContourGeometryListID – the ID of the last contour geometry list to output
oSizeROI – Region-Of-Interest (ROI).
nAdjacentPixels – how far away in a contour to find adjacent points to use to compute radius
pComputedContourPointCurvatureDev – output array for computed values
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes


NppStatus nppiComputeCurvature_32s_Ctx(NppiPoint *pContoursPointList, Npp32u nTotalContourPointCount, NppiContourBlockSegment *pContourBlockSegmentList, Npp32u nFirstContourGeometryListID, Npp32u nLastContourGeometryListID, NppiSize oSizeROI, Npp32u nAdjacentPixels, Npp32f *pComputedContourPointCurvatureDev, NppStreamContext nppStreamCtx)
Measure inverse radius squared curvature along contours.

Parameters

pContoursPointList – pointer to device memory array of NppiPoint
nTotalContourPointCount – count of number of points in pContoursPointList
pContourBlockSegmentList – pointer to array of NppiContourBlockSegment objects
nFirstContourGeometryListID – the ID of the first contour geometry list to output.
nLastContourGeometryListID – the ID of the last contour geometry list to output
oSizeROI – Region-Of-Interest (ROI).
nAdjacentPixels – how far away in a contour to find adjacent points to use to compute radius
pComputedContourPointCurvatureDev – output array for computed values
nppStreamCtx – Application Managed Stream Context.

Returns

Image Data Related Error Codes, ROI Related Error Codes