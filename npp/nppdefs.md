# Data Types, Structs, Enums, and Constants


struct Npp16f
Workarounds for cuda_fp16.h C incompatibility Npp16f.

Public Members

short fp16

Original Cuda fp16 data size and format.


struct Npp16f_2
Npp16f_2.

Public Members

short fp16_0

Original Cuda fp16 data size and format.

short fp16_1

Original Cuda fp16 data size and format.


enum NppiInterpolationMode
Filtering methods.
Values:

enumerator NPPI_INTER_UNDEFINED

Undefined filtering interpolation mode.

enumerator NPPI_INTER_NN

Nearest neighbor filtering.

enumerator NPPI_INTER_LINEAR

Linear interpolation.

enumerator NPPI_INTER_CUBIC

Cubic interpolation.

enumerator NPPI_INTER_CUBIC2P_BSPLINE

Two-parameter cubic filter (B=1, C=0)

enumerator NPPI_INTER_CUBIC2P_CATMULLROM

Two-parameter cubic filter (B=0, C=1/2)

enumerator NPPI_INTER_CUBIC2P_B05C03

Two-parameter cubic filter (B=1/2, C=3/10)

enumerator NPPI_INTER_SUPER

Super sampling.

enumerator NPPI_INTER_LANCZOS

Lanczos filtering.

enumerator NPPI_INTER_LANCZOS3_ADVANCED

Generic Lanczos filtering with order 3.

enumerator NPPI_SMOOTH_EDGE

Smooth edge filtering.


enum NppiBayerGridPosition
Bayer Grid Position Registration.
Values:

enumerator NPPI_BAYER_BGGR

Default registration position BGGR.

enumerator NPPI_BAYER_RGGB

Registration position RGGB.

enumerator NPPI_BAYER_GBRG

Registration position GBRG.

enumerator NPPI_BAYER_GRBG

Registration position GRBG.


enum NppiMaskSize
Fixed filter-kernel sizes.
Values:

enumerator NPP_MASK_SIZE_1_X_3

1 X 3 filter mask size.

enumerator NPP_MASK_SIZE_1_X_5

1 X 5 filter mask size.

enumerator NPP_MASK_SIZE_3_X_1

3 X 1 filter mask size, leaving space for more 1 X N type enum values.

enumerator NPP_MASK_SIZE_5_X_1

5 X 1 filter mask size.

enumerator NPP_MASK_SIZE_3_X_3

3 X 3 filter mask size, leaving space for more N X 1 type enum values.

enumerator NPP_MASK_SIZE_5_X_5

5 X 5 filter mask size.

enumerator NPP_MASK_SIZE_7_X_7

7 X 7 filter mask size.

enumerator NPP_MASK_SIZE_9_X_9

9 X 9 filter mask size.

enumerator NPP_MASK_SIZE_11_X_11

11 X 11 filter mask size.

enumerator NPP_MASK_SIZE_13_X_13

13 X 13 filter mask size.

enumerator NPP_MASK_SIZE_15_X_15

15 X 15 filter mask size.


enum NppiDifferentialKernel
Differential Filter types.
Values:

enumerator NPP_FILTER_SOBEL

Differential kernel filter type sobel.

enumerator NPP_FILTER_SCHARR

Differential kernel filter type scharr.


enum NppStatus
Error Status Codes.
Almost all NPP function return error-status information using these return codes. Negative return codes indicate errors, positive return codes indicate warnings, a return code of 0 indicates success.
Values:

enumerator NPP_NOT_SUPPORTED_MODE_ERROR

Not supported mode error.

enumerator NPP_INVALID_HOST_POINTER_ERROR

Invalid host memory pointer error.

enumerator NPP_INVALID_DEVICE_POINTER_ERROR

Invalid device memory pointer error.

enumerator NPP_LUT_PALETTE_BITSIZE_ERROR

Color look up table bitsize error.

enumerator NPP_ZC_MODE_NOT_SUPPORTED_ERROR

ZeroCrossing mode not supported error.

enumerator NPP_NOT_SUFFICIENT_COMPUTE_CAPABILITY

Not sufficient Cuda compute capability error.

enumerator NPP_TEXTURE_BIND_ERROR

Texture bind error.

enumerator NPP_WRONG_INTERSECTION_ROI_ERROR

Wrong intersection region of interest error.

enumerator NPP_HAAR_CLASSIFIER_PIXEL_MATCH_ERROR

Haar classifier pixel match error.

enumerator NPP_MEMFREE_ERROR

Memory free request error.

enumerator NPP_MEMSET_ERROR

Memory set request error.

enumerator NPP_MEMCPY_ERROR

Memory copy request error.

enumerator NPP_ALIGNMENT_ERROR

Memory alignment error.

enumerator NPP_CUDA_KERNEL_EXECUTION_ERROR

Cuda kernel execution error, most commonly Cuda kernel launch error.

enumerator NPP_STREAM_CTX_ERROR

Non CTX function support has been deprecated.

enumerator NPP_ROUND_MODE_NOT_SUPPORTED_ERROR

Unsupported round mode.

enumerator NPP_QUALITY_INDEX_ERROR

Image pixels are constant for quality index.

enumerator NPP_RESIZE_NO_OPERATION_ERROR

One of the output image dimensions is less than 1 pixel.

enumerator NPP_OVERFLOW_ERROR

Number overflows the upper or lower limit of the data type.

enumerator NPP_NOT_EVEN_STEP_ERROR

Step value is not pixel multiple.

enumerator NPP_HISTOGRAM_NUMBER_OF_LEVELS_ERROR

Number of levels for histogram is less than 2.

enumerator NPP_LUT_NUMBER_OF_LEVELS_ERROR

Number of levels for LUT is less than 2.

enumerator NPP_CORRUPTED_DATA_ERROR

Processed data is corrupted,.

enumerator NPP_CHANNEL_ORDER_ERROR

Wrong order of the destination channels,.

enumerator NPP_ZERO_MASK_VALUE_ERROR

All values of the mask are zero,.

enumerator NPP_QUADRANGLE_ERROR

The quadrangle is nonconvex or degenerates into triangle, line or point.

enumerator NPP_RECTANGLE_ERROR

Size of the rectangle region is less than or equal to 1.

enumerator NPP_COEFFICIENT_ERROR

Unallowable values of the transformation coefficients.

enumerator NPP_NUMBER_OF_CHANNELS_ERROR

Bad or unsupported number of channels.

enumerator NPP_COI_ERROR

Channel of interest is not 1, 2, or 3.

enumerator NPP_DIVISOR_ERROR

Divisor is equal to zero.

enumerator NPP_CHANNEL_ERROR

Illegal channel index.

enumerator NPP_STRIDE_ERROR

Stride is less than the row length.

enumerator NPP_ANCHOR_ERROR

Anchor point is outside mask.

enumerator NPP_MASK_SIZE_ERROR

Lower bound is larger than upper bound.

enumerator NPP_RESIZE_FACTOR_ERROR

enumerator NPP_INTERPOLATION_ERROR

enumerator NPP_MIRROR_FLIP_ERROR

enumerator NPP_MOMENT_00_ZERO_ERROR

enumerator NPP_THRESHOLD_NEGATIVE_LEVEL_ERROR

enumerator NPP_THRESHOLD_ERROR

enumerator NPP_CONTEXT_MATCH_ERROR

enumerator NPP_FFT_FLAG_ERROR

enumerator NPP_FFT_ORDER_ERROR

enumerator NPP_STEP_ERROR

Step is less or equal zero.

enumerator NPP_SCALE_RANGE_ERROR

enumerator NPP_DATA_TYPE_ERROR

enumerator NPP_OUT_OFF_RANGE_ERROR

enumerator NPP_DIVIDE_BY_ZERO_ERROR

enumerator NPP_MEMORY_ALLOCATION_ERR

enumerator NPP_NULL_POINTER_ERROR

enumerator NPP_RANGE_ERROR

enumerator NPP_SIZE_ERROR

enumerator NPP_BAD_ARGUMENT_ERROR

enumerator NPP_NO_MEMORY_ERROR

enumerator NPP_NOT_IMPLEMENTED_ERROR

enumerator NPP_ERROR

enumerator NPP_ERROR_RESERVED

enumerator NPP_NO_ERROR

Error free operation.

enumerator NPP_SUCCESS

Successful operation (same as NPP_NO_ERROR)

enumerator NPP_NO_OPERATION_WARNING

Indicates that no operation was performed.

enumerator NPP_DIVIDE_BY_ZERO_WARNING

Divisor is zero however does not terminate the execution.

enumerator NPP_AFFINE_QUAD_INCORRECT_WARNING

Indicates that the quadrangle passed to one of affine warping functions doesn’t have necessary properties.
First 3 vertices are used, the fourth vertex discarded.

enumerator NPP_WRONG_INTERSECTION_ROI_WARNING

The given ROI has no interestion with either the source or destination ROI.
Thus no operation was performed.

enumerator NPP_WRONG_INTERSECTION_QUAD_WARNING

The given quadrangle has no intersection with either the source or destination ROI.
Thus no operation was performed.

enumerator NPP_DOUBLE_SIZE_WARNING

Image size isn’t multiple of two.
Indicates that in case of 422/411/420 sampling the ROI width/height was modified for proper processing.

enumerator NPP_MISALIGNED_DST_ROI_WARNING

Speed reduction due to uncoalesced memory accesses warning.


struct NppLibraryVersion
NPPLibraryVersion This struct contains the NPP Library Version information.

Public Members

int major

Major version number.

int minor

Minor version number.

int build

Build number.
This reflects the nightly build this release was made from.


typedef unsigned char Npp8u
8-bit unsigned chars


typedef signed char Npp8s
8-bit signed chars


typedef unsigned short Npp16u
16-bit unsigned integers


typedef short Npp16s
16-bit signed integers


typedef unsigned int Npp32u
32-bit unsigned integers


typedef int Npp32s
32-bit signed integers


typedef unsigned long long Npp64u
64-bit unsigned integers


typedef long long Npp64s
64-bit signed integers


typedef float Npp32f
32-bit (IEEE) floating-point numbers


typedef double Npp64f
64-bit floating-point numbers


struct Npp8uc
Complex Number This struct represents an unsigned char complex number.

Public Members

Npp8u re

Real part.

Npp8u im

Imaginary part.


struct Npp16uc
Complex Number This struct represents an unsigned short complex number.

Public Members

Npp16u re

Real part.

Npp16u im

Imaginary part.


struct Npp16sc
Complex Number This struct represents a short complex number.

Public Members

Npp16s re

Real part.

Npp16s im

Imaginary part.


struct Npp32uc
Complex Number This struct represents an unsigned int complex number.

Public Members

Npp32u re

Real part.

Npp32u im

Imaginary part.


struct Npp32sc
Complex Number This struct represents a signed int complex number.

Public Members

Npp32s re

Real part.

Npp32s im

Imaginary part.


struct Npp32fc
Complex Number This struct represents a single floating-point complex number.

Public Members

Npp32f re

Real part.

Npp32f im

Imaginary part.


struct Npp64sc
Complex Number This struct represents a long long complex number.

Public Members

Npp64s re

Real part.

Npp64s im

Imaginary part.


struct Npp64fc
Complex Number This struct represents a double floating-point complex number.

Public Members

Npp64f re

Real part.

Npp64f im

Imaginary part.


enum NppDataType
Data types for nppiPlus functions.
Values:

enumerator NPP_8U

8-bit unsigned integer data type

enumerator NPP_8S

8-bit signed integer data type

enumerator NPP_16U

16-bit unsigned integer data type

enumerator NPP_16S

16-bit signed integer data type

enumerator NPP_32U

32-bit unsigned integer data type

enumerator NPP_32S

32-bit signed integer data type

enumerator NPP_64U

64-bit unsigned integer data type

enumerator NPP_64S

64-bit signed integer data type

enumerator NPP_16F

16-bit original Cuda floating point data type

enumerator NPP_32F

32-bit floating point data type

enumerator NPP_64F

64-bit double precision floating point data type


enum NppiChannels
Image channel counts for nppiPlus functions.
Values:

enumerator NPP_CH_1

Single channel per pixel data.

enumerator NPP_CH_2

Two channel per pixel data.

enumerator NPP_CH_3

Three channel per pixel data.

enumerator NPP_CH_4

Four channel per pixel data.

enumerator NPP_CH_A4

Four channel per pixel data with alpha.

enumerator NPP_CH_P2

Two channel single channel per plane pixel data.

enumerator NPP_CH_P3

Three channel single channel per plane pixel data.

enumerator NPP_CH_P4

Four channel single channel per plane pixel data.


NPP_MIN_8U
Minimum 8-bit unsigned integer.


NPP_MAX_8U
Maximum 8-bit unsigned integer.


NPP_MIN_16U
Minimum 16-bit unsigned integer.


NPP_MAX_16U
Maximum 16-bit unsigned integer.


NPP_MIN_32U
Minimum 32-bit unsigned integer.


NPP_MAX_32U
Maximum 32-bit unsigned integer.


NPP_MIN_64U
Minimum 64-bit unsigned integer.


NPP_MAX_64U
Maximum 64-bit unsigned integer.


NPP_MIN_8S
Minimum 8-bit signed integer.


NPP_MAX_8S
Maximum 8-bit signed integer.


NPP_MIN_16S
Minimum 16-bit signed integer.


NPP_MAX_16S
Maximum 16-bit signed integer.


NPP_MIN_32S
Minimum 32-bit signed integer.


NPP_MAX_32S
Maximum 32-bit signed integer.


NPP_MIN_64S
Minimum 64-bit signed integer.


NPP_MAX_64S
Minimum 64-bit signed integer.


NPP_MINABS_32F
Smallest positive 32-bit floating point value.


NPP_MAXABS_32F
Largest positive 32-bit floating point value.


NPP_MINABS_64F
Smallest positive 64-bit floating point value.


NPP_MAXABS_64F
Largest positive 64-bit floating point value.


struct NppiPoint
2D Point

Public Members

int x

x-coordinate.

int y

y-coordinate.


struct NppiPoint32f
2D Npp32f Point

Public Members

Npp32f x

x-coordinate.

Npp32f y

y-coordinate.


struct NppiPoint64f
2D Npp64f Point

Public Members

Npp64f x

x-coordinate.

Npp64f y

y-coordinate.


struct NppPointPolar
2D Polar Point

Public Members

Npp32f rho

Polar rho value.

Npp32f theta

Polar theta value.


struct NppiSize
2D Size This struct typically represents the size of a a rectangular region in two space.

Public Members

int width

Rectangle width.

int height

Rectangle height.


struct NppiRect
2D Rectangle This struct contains position and size information of a rectangle in two space.
The rectangle’s position is usually signified by the coordinate of its upper-left corner.

Public Members

int x

x-coordinate of upper left corner (lowest memory address).

int y

y-coordinate of upper left corner (lowest memory address).

int width

Rectangle width.

int height

Rectangle height.


enum NppiAxis
nppiMirror direction controls
Values:

enumerator NPP_HORIZONTAL_AXIS

Flip around horizontal axis in mirror function.

enumerator NPP_VERTICAL_AXIS

Flip around vertical axis in mirror function.

enumerator NPP_BOTH_AXIS

Flip around both axes in mirror function.


enum NppCmpOp
Pixel comparison control values.
Values:

enumerator NPP_CMP_LESS

Threshold test for less than.

enumerator NPP_CMP_LESS_EQ

Threshold test for less than or equal.

enumerator NPP_CMP_EQ

Threshold test for equal.

enumerator NPP_CMP_GREATER_EQ

Threshold test for greater than or equal.

enumerator NPP_CMP_GREATER

Threshold test for greater than.


enum NppRoundMode
Rounding Modes.
The enumerated rounding modes are used by a large number of NPP primitives to allow the user to specify the method by which fractional values are converted to integer values. Also see Rounding Modes.
For NPP release 5.5 new names for the three rounding modes are introduced that are based on the naming conventions for rounding modes set forth in the IEEE-754 floating-point standard. Developers are encouraged to use the new, longer names to be future proof as the legacy names will be deprecated in subsequent NPP releases.
Values:

enumerator NPP_RND_NEAR

Round to the nearest even integer.
All fractional numbers are rounded to their nearest integer. The ambiguous cases (i.e. <integer>.5) are rounded to the closest even integer. E.g.

roundNear(0.5) = 0
roundNear(0.6) = 1
roundNear(1.5) = 2
roundNear(-1.5) = -2

enumerator NPP_ROUND_NEAREST_TIES_TO_EVEN

Alias name for NPP_RND_NEAR.

enumerator NPP_RND_FINANCIAL

Round according to financial rule.
All fractional numbers are rounded to their nearest integer. The ambiguous cases (i.e. <integer>.5) are rounded away from zero. E.g.

roundFinancial(0.4) = 0
roundFinancial(0.5) = 1
roundFinancial(-1.5) = -2

enumerator NPP_ROUND_NEAREST_TIES_AWAY_FROM_ZERO

Alias name for NPP_RND_FINANCIAL.

enumerator NPP_RND_ZERO

Round towards zero (truncation).
All fractional numbers of the form <integer>.<decimals> are truncated to <integer>.

roundZero(1.5) = 1
roundZero(1.9) = 1
roundZero(-2.5) = -2

enumerator NPP_ROUND_TOWARD_ZERO

Alias name for NPP_RND_ZERO.


enum NppiBorderType
Supported image border modes.
Values:

enumerator NPP_BORDER_UNDEFINED

Image border type undefined.

enumerator NPP_BORDER_NONE

Image border type none.

enumerator NPP_BORDER_CONSTANT

Image border type constant value.

enumerator NPP_BORDER_REPLICATE

Image border type replicate border pixels.

enumerator NPP_BORDER_WRAP

Image border type wrap border pixels.

enumerator NPP_BORDER_MIRROR

Image border type mirror border pixels.


enum NppHintAlgorithm
Hints.
Values:

enumerator NPP_ALG_HINT_NONE

Hint none, currently these are all ignored.

enumerator NPP_ALG_HINT_FAST

Hint fast, currently these are all ignored.

enumerator NPP_ALG_HINT_ACCURATE

Hint accurate, currently these are all ignored.


enum NppiAlphaOp
Alpha composition mode controls.
Values:

enumerator NPPI_OP_ALPHA_OVER

Alpha composition over operation.

enumerator NPPI_OP_ALPHA_IN

Alpha composition in operation.

enumerator NPPI_OP_ALPHA_OUT

Alpha composition out operation.

enumerator NPPI_OP_ALPHA_ATOP

Alpha composition atop operation.

enumerator NPPI_OP_ALPHA_XOR

Alpha composition xor operation.

enumerator NPPI_OP_ALPHA_PLUS

Alpha composition plus operation.

enumerator NPPI_OP_ALPHA_OVER_PREMUL

Alpha composition over premultiply operation.

enumerator NPPI_OP_ALPHA_IN_PREMUL

Alpha composition in premultiply operation.

enumerator NPPI_OP_ALPHA_OUT_PREMUL

Alpha composition out premultiply operation.

enumerator NPPI_OP_ALPHA_ATOP_PREMUL

Alpha composition atop premultiply operation.

enumerator NPPI_OP_ALPHA_XOR_PREMUL

Alpha composition xor premultiply operation.

enumerator NPPI_OP_ALPHA_PLUS_PREMUL

Alpha composition plus premultiply operation.

enumerator NPPI_OP_ALPHA_PREMUL

Alpha composition premultiply operation.


struct NppiHOGConfig
The NppiHOGConfig structure defines the configuration parameters for the HOG descriptor:

Public Members

int cellSize

square cell size (pixels).

int histogramBlockSize

square histogram block size (pixels).

int nHistogramBins

required number of histogram bins.

NppiSize detectionWindowSize

detection window size (pixels).


NPP_HOG_MAX_CELL_SIZE
HOG Cell controls.
max horizontal/vertical pixel size of cell.


NPP_HOG_MAX_BLOCK_SIZE
max horizontal/vertical pixel size of block.


NPP_HOG_MAX_BINS_PER_CELL
max number of histogram bins.


NPP_HOG_MAX_CELLS_PER_DESCRIPTOR
max number of cells in a descriptor window.


NPP_HOG_MAX_OVERLAPPING_BLOCKS_PER_DESCRIPTOR
max number of overlapping blocks in a descriptor window.


NPP_HOG_MAX_DESCRIPTOR_LOCATIONS_PER_CALL
max number of descriptor window locations per function call.


struct NppiHaarClassifier_32f
Data structure for HaarClassifier_32f.

Public Members

int numClassifiers

number of classifiers.

Npp32s *classifiers

packed classifier data 40 bytes each.

size_t classifierStep

packed classifier byte step.

NppiSize classifierSize

packed classifier size.

Npp32s *counterDevice

counter device.


struct NppiHaarBuffer
Data structure for Haar buffer.

Public Members

int haarBufferSize

size of the buffer

Npp32s *haarBuffer

buffer


enum NppsZCType
Signal sign operations.
Values:

enumerator nppZCR

sign change

enumerator nppZCXor

sign change XOR

enumerator nppZCC

sign change count_0


enum NppiHuffmanTableType
HuffMan Table controls.
Values:

enumerator nppiDCTable

DC Table.

enumerator nppiACTable

AC Table.


enum NppiNorm
Norm controls.
Values:

enumerator nppiNormInf

maximum

enumerator nppiNormL1

sum

enumerator nppiNormL2

square root of sum of squares


struct NppiConnectedRegion
Data structure of connected pixel region information.

Public Members

NppiRect oBoundingBox

x, y, width, height == left, top, right, and bottom pixel coordinates

Npp32u nConnectedPixelCount

total number of pixels in connected region

Npp32u aSeedPixelValue[3]

original pixel value of seed pixel, 1 or 3 channel


struct NppiImageDescriptor
General image descriptor.
Defines the basic parameters of an image, including data pointer, step, and image size. This can be used by both source and destination images.

Public Members

void *pData

device memory pointer to the image

int nStep

step size

NppiSize oSize

width and height of the image


struct NppiBufferDescriptor
struct NppiBufferDescriptor

Public Members

void *pData

per image device memory pointer to the corresponding buffer

int nBufferSize

allocated buffer size


struct NppiCompressedMarkerLabelsInfo
Provides details of uniquely labeled pixel regions of interest returned by CompressedLabelMarkersUF function.

Public Members

Npp32u nMarkerLabelPixelCount

total number of pixels in this connected pixel region

Npp32u nContourPixelCount

total number of pixels in this connected pixel region contour

Npp32u nContourPixelsFound

total number of pixels in this connected pixel region contour found during geometry search

NppiPoint oContourFirstPixelLocation

image geometric x and y location of the first pixel in the contour

NppiRect oMarkerLabelBoundingBox

bounding box of this connected pixel region expressed as leftmostX, topmostY, rightmostX, and bottommostY


struct NppiContourBlockSegment
Provides details of contour pixel grid map location and association.

Public Members

Npp32u nMarkerLabelID

this connected pixel region contour ID

Npp32u nContourPixelCount

total number of pixels in this connected pixel region contour

Npp32u nContourStartingPixelOffset

base offset of starting pixel in the overall contour pixel list

Npp32u nSegmentNum

relative block segment number within this particular contour ID


struct NppiContourPixelGeometryInfo
Provides contour (boundary) geometry info of uniquely labeled pixel regions returned by nppiCompressedMarkerLabelsUFInfo function in host memory in counterclockwise order relative to contour interiors.

Public Members

NppiPoint oContourOrderedGeometryLocation

image geometry X and Y location in requested output order

NppiPoint oContourPrevPixelLocation

image geometry X and Y location of previous contour pixel

NppiPoint oContourCenterPixelLocation

image geometry X and Y location of center contour pixel

NppiPoint oContourNextPixelLocation

image geometry X and Y location of next contour pixel

Npp32s nOrderIndex

contour pixel counterclockwise order index in geometry list

Npp32s nReverseOrderIndex

contour pixel clockwise order index in geometry list

Npp32u nFirstIndex

index of first ordered contour pixel in this subgroup

Npp32u nLastIndex

index of last ordered contour pixel in this subgroup

Npp32u nNextContourPixelIndex

index of next ordered contour pixel in NppiContourPixelGeometryInfo list

Npp32u nPrevContourPixelIndex

index of previous ordered contour pixel in NppiContourPixelGeometryInfo list

Npp8u nPixelAlreadyUsed

this test pixel is has already been used

Npp8u nAlreadyLinked

this test pixel is already linked to center pixel

Npp8u nAlreadyOutput

this pixel has already been output in geometry list

Npp8u nContourInteriorDirection

direction of contour region interior


NPP_CONTOUR_DIRECTION_SOUTH_EAST
Provides contour (boundary) direction info of uniquely labeled pixel regions returned by CompressedLabelMarkersUF function.
Contour direction south east


NPP_CONTOUR_DIRECTION_SOUTH
Contour direction south.


NPP_CONTOUR_DIRECTION_SOUTH_WEST
Contour direction south west.


NPP_CONTOUR_DIRECTION_WEST
Contour direction west.


NPP_CONTOUR_DIRECTION_EAST
Contour direction east.


NPP_CONTOUR_DIRECTION_NORTH_EAST
Contour direction north east.


NPP_CONTOUR_DIRECTION_NORTH
Contour direction north.


NPP_CONTOUR_DIRECTION_NORTH_WEST
Contour direction north west.


NPP_CONTOUR_DIRECTION_ANY_NORTH
Provides contour (boundary) diagonal direction info of uniquely labeled pixel regions returned by CompressedLabelMarkersUF function.
Contour direction any north


NPP_CONTOUR_DIRECTION_ANY_WEST
Contour direction any west.


NPP_CONTOUR_DIRECTION_ANY_SOUTH
Contour direction any south.


NPP_CONTOUR_DIRECTION_ANY_EAST
Contour direction any east.


struct NppiContourPixelDirectionInfo
Data structure for contour pixel direction information.

Public Members

Npp32u nMarkerLabelID

MarkerLabelID of contour interior connected region.

Npp8u nContourDirectionCenterPixel

provides current center contour pixel input and output direction info

Npp8u nContourInteriorDirectionCenterPixel

provides current center contour pixel region interior direction info

Npp8u nConnected

direction to directly connected contour pixels, 0 if not connected

Npp8u nGeometryInfoIsValid

direction to directly connected contour pixels, 0 if not connected

NppiContourPixelGeometryInfo oContourPixelGeometryInfo

Pixel geometry info structure.

NppiPoint nEast1

Pixel coordinate values in each direction.

NppiPoint nNorthEast1

Pixel coordinate values in each direction.

NppiPoint nNorth1

Pixel coordinate values in each direction.

NppiPoint nNorthWest1

Pixel coordinate values in each direction.

NppiPoint nWest1

Pixel coordinate values in each direction.

NppiPoint nSouthWest1

Pixel coordinate values in each direction.

NppiPoint nSouth1

Pixel coordinate values in each direction.

NppiPoint nSouthEast1

Pixel coordinate values in each direction.

Npp8u nTest1EastConnected

East connected flag.

Npp8u nTest1NorthEastConnected

North east connected flag.

Npp8u nTest1NorthConnected

North connected flag.

Npp8u nTest1NorthWestConnected

North west connected flag.

Npp8u nTest1WestConnected

West connected flag.

Npp8u nTest1SouthWestConnected

South west connected flag.

Npp8u nTest1SouthConnected

South connected flag.

Npp8u nTest1SouthEastConnected

South east connected flag.


struct NppiContourTotalsInfo
Data structure for contour total counts.

Public Members

Npp32u nTotalImagePixelContourCount

total number of contour pixels in image

Npp32u nLongestImageContourPixelCount

longest per contour pixel count in image


enum NppiWatershedSegmentBoundaryType
Provides control of the type of segment boundaries, if any, added to the image generated by the watershed segmentation function.
Values:

enumerator NPP_WATERSHED_SEGMENT_BOUNDARIES_NONE

Image watershed segment boundary type none.

enumerator NPP_WATERSHED_SEGMENT_BOUNDARIES_BLACK

Image watershed segment boundary type black.

enumerator NPP_WATERSHED_SEGMENT_BOUNDARIES_WHITE

Image watershed segment boundary type white.

enumerator NPP_WATERSHED_SEGMENT_BOUNDARIES_CONTRAST

Image watershed segment boundary type contrasting intensiity.

enumerator NPP_WATERSHED_SEGMENT_BOUNDARIES_ONLY

Image watershed segment boundary type render boundaries only.


struct NppStreamContext
Application Managed Stream Context

NPP stream context structure must be filled in by application. Application should not initialize or alter reserved fields.

Public Members

cudaStream_t hStream

From current Cuda stream ID.

int nCudaDeviceId

From cudaGetDevice().

int nMultiProcessorCount

From cudaGetDeviceProperties().

int nMaxThreadsPerMultiProcessor

From cudaGetDeviceProperties().

int nMaxThreadsPerBlock

From cudaGetDeviceProperties().

size_t nSharedMemPerBlock

From cudaGetDeviceProperties().

int nCudaDevAttrComputeCapabilityMajor

From cudaGetDeviceAttribute().

int nCudaDevAttrComputeCapabilityMinor

From cudaGetDeviceAttribute().

unsigned int nStreamFlags

From cudaStreamGetFlags().

int nReserved0

reserved, do not alter.


struct NppiResizeBatchCXR
NPP Batch Geometry Structure Definitions.

Public Members

const void *pSrc

source image device memory pointer.

int nSrcStep

source image byte count per row.

void *pDst

destination image device memory pointer.

int nDstStep

device image byte count per row.


struct NppiResizeBatchROI_Advanced
Data structure for variable ROI image batch resizing.

Public Members

NppiRect oSrcRectROI

per source image rectangle parameters.

NppiRect oDstRectROI

per destination image rectangle parameters.


struct NppiMirrorBatchCXR
Data structure for batched nppiMirrorBatch.

Public Members

const void *pSrc

source image device memory pointer, ignored for in-place versions.

int nSrcStep

source image byte count per row.

void *pDst

destination image device memory pointer.

int nDstStep

device image byte count per row.


struct NppiWarpAffineBatchCXR
Data structure for batched nppiWarpAffineBatch.

Public Members

const void *pSrc

source image device memory pointer.

int nSrcStep

source image byte count per row.

void *pDst

destination image device memory pointer.

int nDstStep

device image byte count per row.

Npp64f *pCoeffs

device memory pointer to the tranformation matrix with double precision floating-point coefficient values to be used for this image.

Npp64f aTransformedCoeffs[2][3]

FOR INTERNAL USE, DO NOT INITIALIZE.


struct NppiWarpPerspectiveBatchCXR
Data structure for batched nppiWarpPerspectiveBatch.

Public Members

const void *pSrc

source image device memory pointer.

int nSrcStep

source image byte count per row.

void *pDst

destination image device memory pointer.

int nDstStep

device image byte count per row.

Npp64f *pCoeffs

device memory pointer to the tranformation matrix with double precision floating-point coefficient values to be used for this image.

Npp64f aTransformedCoeffs[3][3]

FOR INTERNAL USE, DO NOT INITIALIZE.


struct NppiColorTwistBatchCXR
Data structure for batched nppiColorTwistBatch.

Public Members

const void *pSrc

source image device memory pointer.

int nSrcStep

source image byte count per row.

void *pDst

destination image device memory pointer.

int nDstStep

device image byte count per row.

Npp32f *pTwist

device memory pointer to the color twist matrix with floating-point coefficient values to be used for this image.