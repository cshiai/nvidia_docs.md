# 2.7. FP6 Conversion and Data Movement


To use these functions, include the header file `cuda_fp6.h` in your program.


Enumerations


__nv_fp6_interpretation_t
Enumerates the possible interpretations of the 8-bit values when referring to them as fp6 types.


Functions


__host__ __device__ __nv_fp6x2_storage_t __nv_cvt_bfloat16raw2_to_fp6x2(const __nv_bfloat162_raw x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input vector of two nv_bfloat16 precision numbers packed in __nv_bfloat162_raw x into a vector of two values of fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.

__host__ __device__ __nv_fp6_storage_t __nv_cvt_bfloat16raw_to_fp6(const __nv_bfloat16_raw x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input nv_bfloat16 precision x to fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.

__host__ __device__ __nv_fp6x2_storage_t __nv_cvt_double2_to_fp6x2(const double2 x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input vector of two double precision numbers packed in double2 x into a vector of two values of fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.

__host__ __device__ __nv_fp6_storage_t __nv_cvt_double_to_fp6(const double x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input double precision x to fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.

__host__ __device__ __nv_fp6x2_storage_t __nv_cvt_float2_to_fp6x2(const float2 x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input vector of two single precision numbers packed in float2 x into a vector of two values of fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.

__host__ __device__ __nv_fp6_storage_t __nv_cvt_float_to_fp6(const float x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input single precision x to fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.

__host__ __device__ __half_raw __nv_cvt_fp6_to_halfraw(const __nv_fp6_storage_t x, const __nv_fp6_interpretation_t fp6_interpretation)
Converts input fp6 x of the specified kind to half precision.

__host__ __device__ __half2_raw __nv_cvt_fp6x2_to_halfraw2(const __nv_fp6x2_storage_t x, const __nv_fp6_interpretation_t fp6_interpretation)
Converts input vector of two fp6 values of the specified kind to a vector of two half precision values packed in __half2_raw structure.

__host__ __device__ __nv_fp6x2_storage_t __nv_cvt_halfraw2_to_fp6x2(const __half2_raw x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input vector of two half precision numbers packed in __half2_raw x into a vector of two values of fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.

__host__ __device__ __nv_fp6_storage_t __nv_cvt_halfraw_to_fp6(const __half_raw x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input half precision x to fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3()
Constructor by default.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3(const float f)
Constructor from float data type, relies on __NV_SATFINITE behavior for out-of-range values and cudaRoundNearest rounding mode.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3(const long long int val)
Constructor from long long int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3(const long int val)
Constructor from long int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3(const unsigned short int val)
Constructor from unsigned short int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3(const double f)
Constructor from double data type, relies on __NV_SATFINITE behavior for out-of-range values and cudaRoundNearest rounding mode.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3(const unsigned long long int val)
Constructor from unsigned long long int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3(const short int val)
Constructor from short int data type.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3(const __nv_bfloat16 f)
Constructor from __nv_bfloat16 data type, relies on __NV_SATFINITE behavior for out-of-range values and cudaRoundNearest rounding mode.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3(const int val)
Constructor from int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3(const __half f)
Constructor from __half data type, relies on __NV_SATFINITE behavior for out-of-range values and cudaRoundNearest rounding mode.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3(const unsigned int val)
Constructor from unsigned int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e2m3::__nv_fp6_e2m3(const unsigned long int val)
Constructor from unsigned long int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2(const long long int val)
Constructor from long long int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2(const __half f)
Constructor from __half data type, relies on __NV_SATFINITE behavior for out-of-range values and cudaRoundNearest rounding mode.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2(const int val)
Constructor from int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2(const float f)
Constructor from float data type, relies on __NV_SATFINITE behavior for out-of-range values and cudaRoundNearest rounding mode.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2(const short int val)
Constructor from short int data type.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2(const long int val)
Constructor from long int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2(const unsigned long long int val)
Constructor from unsigned long long int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2(const unsigned short int val)
Constructor from unsigned short int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2(const __nv_bfloat16 f)
Constructor from __nv_bfloat16 data type, relies on __NV_SATFINITE behavior for out-of-range values and cudaRoundNearest rounding mode.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2(const double f)
Constructor from double data type, relies on __NV_SATFINITE behavior for out-of-range values and cudaRoundNearest rounding mode.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2(const unsigned int val)
Constructor from unsigned int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2()
Constructor by default.

__host__ __device__ __nv_fp6_e3m2::__nv_fp6_e3m2(const unsigned long int val)
Constructor from unsigned long int data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x2_e2m3::__nv_fp6x2_e2m3(const __nv_bfloat162 f)
Constructor from __nv_bfloat162 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x2_e2m3::__nv_fp6x2_e2m3(const float2 f)
Constructor from float2 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x2_e2m3::__nv_fp6x2_e2m3(const double2 f)
Constructor from double2 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x2_e2m3::__nv_fp6x2_e2m3(const __half2 f)
Constructor from __half2 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x2_e2m3::__nv_fp6x2_e2m3()
Constructor by default.

__host__ __device__ __nv_fp6x2_e3m2::__nv_fp6x2_e3m2(const __half2 f)
Constructor from __half2 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x2_e3m2::__nv_fp6x2_e3m2(const float2 f)
Constructor from float2 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x2_e3m2::__nv_fp6x2_e3m2(const __nv_bfloat162 f)
Constructor from __nv_bfloat162 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x2_e3m2::__nv_fp6x2_e3m2(const double2 f)
Constructor from double2 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x2_e3m2::__nv_fp6x2_e3m2()
Constructor by default.

__host__ __device__ __nv_fp6x4_e2m3::__nv_fp6x4_e2m3(const double4_32a f)
Constructor from double4_32a vector data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x4_e2m3::__nv_fp6x4_e2m3(const __half2 flo, const __half2 fhi)
Constructor from a pair of __half2 data type values, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x4_e2m3::__nv_fp6x4_e2m3(const float4 f)
Constructor from float4 vector data type, relies on __NV_SATFINITE behavior for out-of-range values.

__NV_SILENCE_DEPRECATION_END __host__ __device__ __nv_fp6x4_e2m3::__nv_fp6x4_e2m3(const double4_16a f)
Constructor from double4_16a vector data type, relies on __NV_SATFINITE behavior for out-of-range values.

__NV_SILENCE_DEPRECATION_BEGIN __host__ __device__ __nv_fp6x4_e2m3::__nv_fp6x4_e2m3(const double4 f)
Constructor from double4 vector data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x4_e2m3::__nv_fp6x4_e2m3(const __nv_bfloat162 flo, const __nv_bfloat162 fhi)
Constructor from a pair of __nv_bfloat162 data type values, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x4_e2m3::__nv_fp6x4_e2m3()
Constructor by default.

__NV_SILENCE_DEPRECATION_END __host__ __device__ __nv_fp6x4_e3m2::__nv_fp6x4_e3m2(const double4_16a f)
Constructor from double4_16a vector data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x4_e3m2::__nv_fp6x4_e3m2()
Constructor by default.

__host__ __device__ __nv_fp6x4_e3m2::__nv_fp6x4_e3m2(const double4_32a f)
Constructor from double4_32a vector data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x4_e3m2::__nv_fp6x4_e3m2(const __half2 flo, const __half2 fhi)
Constructor from a pair of __half2 data type values, relies on __NV_SATFINITE behavior for out-of-range values.

__NV_SILENCE_DEPRECATION_BEGIN __host__ __device__ __nv_fp6x4_e3m2::__nv_fp6x4_e3m2(const double4 f)
Constructor from double4 vector data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x4_e3m2::__nv_fp6x4_e3m2(const float4 f)
Constructor from float4 vector data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ __nv_fp6x4_e3m2::__nv_fp6x4_e3m2(const __nv_bfloat162 flo, const __nv_bfloat162 fhi)
Constructor from a pair of __nv_bfloat162 data type values, relies on __NV_SATFINITE behavior for out-of-range values.


Typedefs


__nv_fp6_storage_t
8-bit unsigned integer type abstraction used for fp6 floating-point numbers storage.

__nv_fp6x2_storage_t
16-bit unsigned integer type abstraction used for storage of pairs of fp6 floating-point numbers.

__nv_fp6x4_storage_t
32-bit unsigned integer type abstraction used for storage of tetrads of fp6 floating-point numbers.


## 2.7.1. Enumerations


enum __nv_fp6_interpretation_t
Enumerates the possible interpretations of the 8-bit values when referring to them as fp6 types.
Values:

enumerator __NV_E2M3

Stands for fp6 numbers of e2m3 kind.

enumerator __NV_E3M2

Stands for fp6 numbers of e3m2 kind.


## 2.7.2. Functions


__host__ __device__ __nv_fp6x2_storage_t __nv_cvt_bfloat16raw2_to_fp6x2(const __nv_bfloat162_raw x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input vector of two nv_bfloat16 precision numbers packed in __nv_bfloat162_raw x into a vector of two values of fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.
Converts input vector x to a vector of two fp6 values of the kind specified by fp6_interpretation parameter, using rounding mode specified by rounding parameter. Large out-of-range values saturate to MAXNORM of the same sign. NaN input values result in positive MAXNORM.

Returns

The __nv_fp6x2_storage_t value holds the result of conversion.


__host__ __device__ __nv_fp6_storage_t __nv_cvt_bfloat16raw_to_fp6(const __nv_bfloat16_raw x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input nv_bfloat16 precision x to fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.
Converts input x to fp6 type of the kind specified by fp6_interpretation parameter, using rounding mode specified by rounding parameter. Large out-of-range values saturate to MAXNORM of the same sign. NaN input values result in positive MAXNORM.

Returns

The __nv_fp6_storage_t value holds the result of conversion.


__host__ __device__ __nv_fp6x2_storage_t __nv_cvt_double2_to_fp6x2(const double2 x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input vector of two double precision numbers packed in double2 x into a vector of two values of fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.
Converts input vector x to a vector of two fp6 values of the kind specified by fp6_interpretation parameter, using rounding mode specified by rounding parameter. Large out-of-range values saturate to MAXNORM of the same sign. NaN input values result in positive MAXNORM.

Returns

The __nv_fp6x2_storage_t value holds the result of conversion.


__host__ __device__ __nv_fp6_storage_t __nv_cvt_double_to_fp6(const double x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input double precision x to fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.
Converts input x to fp6 type of the kind specified by fp6_interpretation parameter, using rounding mode specified by rounding parameter. Large out-of-range values saturate to MAXNORM of the same sign. NaN input values result in positive MAXNORM.

Returns

The __nv_fp6_storage_t value holds the result of conversion.


__host__ __device__ __nv_fp6x2_storage_t __nv_cvt_float2_to_fp6x2(const float2 x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input vector of two single precision numbers packed in float2 x into a vector of two values of fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.
Converts input vector x to a vector of two fp6 values of the kind specified by fp6_interpretation parameter, using rounding mode specified by rounding parameter. Large out-of-range values saturate to MAXNORM of the same sign. NaN input values result in positive MAXNORM.

Returns

The __nv_fp6x2_storage_t value holds the result of conversion.


__host__ __device__ __nv_fp6_storage_t __nv_cvt_float_to_fp6(const float x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input single precision x to fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.
Converts input x to fp6 type of the kind specified by fp6_interpretation parameter, using rounding mode specified by rounding parameter. Large out-of-range values saturate to MAXNORM of the same sign. NaN input values result in positive MAXNORM.

Returns

The __nv_fp6_storage_t value holds the result of conversion.


__host__ __device__ __half_raw __nv_cvt_fp6_to_halfraw(const __nv_fp6_storage_t x, const __nv_fp6_interpretation_t fp6_interpretation)
Converts input fp6 x of the specified kind to half precision.
Converts input x of fp6 type of the kind specified by fp6_interpretation parameter to half precision.

Returns

The __half_raw value holds the result of conversion.


__host__ __device__ __half2_raw __nv_cvt_fp6x2_to_halfraw2(const __nv_fp6x2_storage_t x, const __nv_fp6_interpretation_t fp6_interpretation)
Converts input vector of two fp6 values of the specified kind to a vector of two half precision values packed in __half2_raw structure.
Converts input vector x of fp6 type of the kind specified by fp6_interpretation parameter to a vector of two half precision values and returns as __half2_raw structure.

Returns

The __half2_raw value holds the result of conversion.


__host__ __device__ __nv_fp6x2_storage_t __nv_cvt_halfraw2_to_fp6x2(const __half2_raw x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input vector of two half precision numbers packed in __half2_raw x into a vector of two values of fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.
Converts input vector x to a vector of two fp6 values of the kind specified by fp6_interpretation parameter, using rounding mode specified by rounding parameter. Large out-of-range values saturate to MAXNORM of the same sign. NaN input values result in positive MAXNORM.

Returns

The __nv_fp6x2_storage_t value holds the result of conversion.


__host__ __device__ __nv_fp6_storage_t __nv_cvt_halfraw_to_fp6(const __half_raw x, const __nv_fp6_interpretation_t fp6_interpretation, const enum cudaRoundMode rounding)
Converts input half precision x to fp6 type of the requested kind using specified rounding mode and saturating the out-of-range values.
Converts input x to fp6 type of the kind specified by fp6_interpretation parameter, using rounding mode specified by rounding parameter. Large out-of-range values saturate to MAXNORM of the same sign. NaN input values result in positive MAXNORM.

Returns

The __nv_fp6_storage_t value holds the result of conversion.


## 2.7.3. Typedefs


typedef __nv_fp8_storage_t __nv_fp6_storage_t
8-bit unsigned integer type abstraction used for fp6 floating-point numbers storage.


typedef __nv_fp8x2_storage_t __nv_fp6x2_storage_t
16-bit unsigned integer type abstraction used for storage of pairs of fp6 floating-point numbers.


typedef __nv_fp8x4_storage_t __nv_fp6x4_storage_t
32-bit unsigned integer type abstraction used for storage of tetrads of fp6 floating-point numbers.