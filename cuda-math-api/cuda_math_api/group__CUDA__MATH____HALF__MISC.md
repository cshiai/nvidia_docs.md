# 4.5. Half Precision Conversion and Data Movement


To use these functions, include the header file `cuda_fp16.h` in your program.


Functions


__host__ __device__ __half __double2half(const double a)
Converts double number to half precision in round-to-nearest-even mode and returns half with converted value.

__host__ __device__ __half2 __float22half2_rn(const float2 a)
Converts both components of float2 number to half precision in round-to-nearest-even mode and returns half2 with converted values.

__host__ __device__ __half __float2half(const float a)
Converts float number to half precision in round-to-nearest-even mode and returns half with converted value.

__host__ __device__ __half2 __float2half2_rn(const float a)
Converts input to half precision in round-to-nearest-even mode and populates both halves of half2 with converted value.

__host__ __device__ __half __float2half_rd(const float a)
Converts float number to half precision in round-down mode and returns half with converted value.

__host__ __device__ __half __float2half_rn(const float a)
Converts float number to half precision in round-to-nearest-even mode and returns half with converted value.

__host__ __device__ __half __float2half_ru(const float a)
Converts float number to half precision in round-up mode and returns half with converted value.

__host__ __device__ __half __float2half_rz(const float a)
Converts float number to half precision in round-towards-zero mode and returns half with converted value.

__host__ __device__ __half2 __floats2half2_rn(const float a, const float b)
Converts both input floats to half precision in round-to-nearest-even mode and returns half2 with converted values.

__host__ __device__ float2 __half22float2(const __half2 a)
Converts both halves of half2 to float2 and returns the result.

__host__ __device__ __half2::__half2(const __half2_raw &h2r)
Constructor from __half2_raw .

__host__ __device__ constexpr __half2::__half2(const __half &a, const __half &b)
Constructor from two __half variables.

__host__ __device__ __half2::__half2(const __half2 &&src)
Move constructor, available for C++11 and later dialects.

__host__ __device__ __half2::__half2(const __half2 &src)
Copy constructor.

__half2::__half2()=default
Constructor by default.

__host__ __device__ __half2::operator __half2_raw() const
Conversion operator to __half2_raw .

__host__ __device__ __half2 & __half2::operator=(const __half2_raw &h2r)
Assignment operator from __half2_raw .

__host__ __device__ __half2 & __half2::operator=(const __half2 &&src)
Move assignment operator, available for C++11 and later dialects.

__host__ __device__ __half2 & __half2::operator=(const __half2 &src)
Copy assignment operator.

__host__ __device__ signed char __half2char_rz(const __half h)
Convert a half to a signed char in round-towards-zero mode.

__host__ __device__ float __half2float(const __half a)
Converts half number to float.

__host__ __device__ __half2 __half2half2(const __half a)
Returns half2 with both halves equal to the input value.

__device__ int __half2int_rd(const __half h)
Convert a half to a signed integer in round-down mode.

__device__ int __half2int_rn(const __half h)
Convert a half to a signed integer in round-to-nearest-even mode.

__device__ int __half2int_ru(const __half h)
Convert a half to a signed integer in round-up mode.

__host__ __device__ int __half2int_rz(const __half h)
Convert a half to a signed integer in round-towards-zero mode.

__device__ long long int __half2ll_rd(const __half h)
Convert a half to a signed 64-bit integer in round-down mode.

__device__ long long int __half2ll_rn(const __half h)
Convert a half to a signed 64-bit integer in round-to-nearest-even mode.

__device__ long long int __half2ll_ru(const __half h)
Convert a half to a signed 64-bit integer in round-up mode.

__host__ __device__ long long int __half2ll_rz(const __half h)
Convert a half to a signed 64-bit integer in round-towards-zero mode.

__device__ short int __half2short_rd(const __half h)
Convert a half to a signed short integer in round-down mode.

__device__ short int __half2short_rn(const __half h)
Convert a half to a signed short integer in round-to-nearest-even mode.

__device__ short int __half2short_ru(const __half h)
Convert a half to a signed short integer in round-up mode.

__host__ __device__ short int __half2short_rz(const __half h)
Convert a half to a signed short integer in round-towards-zero mode.

__host__ __device__ unsigned char __half2uchar_rz(const __half h)
Convert a half to an unsigned char in round-towards-zero mode.

__device__ unsigned int __half2uint_rd(const __half h)
Convert a half to an unsigned integer in round-down mode.

__device__ unsigned int __half2uint_rn(const __half h)
Convert a half to an unsigned integer in round-to-nearest-even mode.

__device__ unsigned int __half2uint_ru(const __half h)
Convert a half to an unsigned integer in round-up mode.

__host__ __device__ unsigned int __half2uint_rz(const __half h)
Convert a half to an unsigned integer in round-towards-zero mode.

__device__ unsigned long long int __half2ull_rd(const __half h)
Convert a half to an unsigned 64-bit integer in round-down mode.

__device__ unsigned long long int __half2ull_rn(const __half h)
Convert a half to an unsigned 64-bit integer in round-to-nearest-even mode.

__device__ unsigned long long int __half2ull_ru(const __half h)
Convert a half to an unsigned 64-bit integer in round-up mode.

__host__ __device__ unsigned long long int __half2ull_rz(const __half h)
Convert a half to an unsigned 64-bit integer in round-towards-zero mode.

__device__ unsigned short int __half2ushort_rd(const __half h)
Convert a half to an unsigned short integer in round-down mode.

__device__ unsigned short int __half2ushort_rn(const __half h)
Convert a half to an unsigned short integer in round-to-nearest-even mode.

__device__ unsigned short int __half2ushort_ru(const __half h)
Convert a half to an unsigned short integer in round-up mode.

__host__ __device__ unsigned short int __half2ushort_rz(const __half h)
Convert a half to an unsigned short integer in round-towards-zero mode.

__host__ __device__ constexpr __half::__half(const __half_raw &hr)
Constructor from __half_raw .

__host__ __device__ __half::__half(const unsigned short val)
Construct __half from unsigned short integer input using default round-to-nearest-even rounding mode.

__host__ __device__ __half::__half(const unsigned int val)
Construct __half from unsigned int input using default round-to-nearest-even rounding mode.

__host__ __device__ __half::__half(const short val)
Construct __half from short integer input using default round-to-nearest-even rounding mode.

__host__ __device__ __half::__half(const double f)
Construct __half from double input using default round-to-nearest-even rounding mode.

__host__ __device__ __half::__half(const unsigned long val)
Construct __half from unsigned long input using default round-to-nearest-even rounding mode.

__host__ __device__ __half::__half(const float f)
Construct __half from float input using default round-to-nearest-even rounding mode.

__host__ __device__ __half::__half(const int val)
Construct __half from int input using default round-to-nearest-even rounding mode.

__host__ __device__ __half::__half(const long val)
Construct __half from long input using default round-to-nearest-even rounding mode.

__host__ __device__ __half::__half(const long long val)
Construct __half from long long input using default round-to-nearest-even rounding mode.

__half::__half()=default
Constructor by default.

__host__ __device__ __half::__half(const __nv_bfloat16 f)
Construct __half from __nv_bfloat16 input using default round-to-nearest-even rounding mode.

__host__ __device__ __half::__half(const unsigned long long val)
Construct __half from unsigned long long input using default round-to-nearest-even rounding mode.

__host__ __device__ __half::operator __half_raw() const volatile
Type cast to __half_raw operator with volatile input.

__host__ __device__ __half::operator __half_raw() const
Type cast to __half_raw operator.

__host__ __device__ constexpr __half::operator bool() const
Conversion operator to bool data type.

__host__ __device__ __half::operator char() const
Conversion operator to an implementation defined char data type.

__host__ __device__ __half::operator float() const
Type cast to float operator.

__host__ __device__ __half::operator int() const
Conversion operator to int data type.

__host__ __device__ __half::operator long() const
Conversion operator to long data type.

__host__ __device__ __half::operator long long() const
Conversion operator to long long data type.

__host__ __device__ __half::operator short() const
Conversion operator to short data type.

__host__ __device__ __half::operator signed char() const
Conversion operator to signed char data type.

__host__ __device__ __half::operator unsigned char() const
Conversion operator to unsigned char data type.

__host__ __device__ __half::operator unsigned int() const
Conversion operator to unsigned int data type.

__host__ __device__ __half::operator unsigned long() const
Conversion operator to unsigned long data type.

__host__ __device__ __half::operator unsigned long long() const
Conversion operator to unsigned long long data type.

__host__ __device__ __half::operator unsigned short() const
Conversion operator to unsigned short data type.

__host__ __device__ __half & __half::operator=(const float f)
Type cast to __half assignment operator from float input using default round-to-nearest-even rounding mode.

__host__ __device__ volatile __half & __half::operator=(const volatile __half_raw &hr) volatile
Assignment operator from volatile __half_raw to volatile __half .

__host__ __device__ __half & __half::operator=(const long long val)
Type cast from long long assignment operator, using default round-to-nearest-even rounding mode.

__host__ __device__ volatile __half & __half::operator=(const __half_raw &hr) volatile
Assignment operator from __half_raw to volatile __half .

__host__ __device__ __half & __half::operator=(const unsigned int val)
Type cast from unsigned int assignment operator, using default round-to-nearest-even rounding mode.

__host__ __device__ __half & __half::operator=(const unsigned short val)
Type cast from unsigned short assignment operator, using default round-to-nearest-even rounding mode.

__host__ __device__ __half & __half::operator=(const short val)
Type cast from short assignment operator, using default round-to-nearest-even rounding mode.

__host__ __device__ __half & __half::operator=(const double f)
Type cast to __half assignment operator from double input using default round-to-nearest-even rounding mode.

__host__ __device__ __half & __half::operator=(const __half_raw &hr)
Assignment operator from __half_raw .

__host__ __device__ __half & __half::operator=(const unsigned long long val)
Type cast from unsigned long long assignment operator, using default round-to-nearest-even rounding mode.

__host__ __device__ __half & __half::operator=(const int val)
Type cast from int assignment operator, using default round-to-nearest-even rounding mode.

__host__ __device__ short int __half_as_short(const __half h)
Reinterprets bits in a half as a signed short integer.

__host__ __device__ unsigned short int __half_as_ushort(const __half h)
Reinterprets bits in a half as an unsigned short integer.

__host__ __device__ __half2 __halves2half2(const __half a, const __half b)
Combines two half numbers into one half2 number.

__host__ __device__ float __high2float(const __half2 a)
Converts high 16 bits of half2 to float and returns the result.

__host__ __device__ __half __high2half(const __half2 a)
Returns high 16 bits of half2 input.

__host__ __device__ __half2 __high2half2(const __half2 a)
Extracts high 16 bits from half2 input.

__host__ __device__ __half2 __highs2half2(const __half2 a, const __half2 b)
Extracts high 16 bits from each of the two half2 inputs and combines into one half2 number.

__host__ __device__ __half __int2half_rd(const int i)
Convert a signed integer to a half in round-down mode.

__host__ __device__ __half __int2half_rn(const int i)
Convert a signed integer to a half in round-to-nearest-even mode.

__host__ __device__ __half __int2half_ru(const int i)
Convert a signed integer to a half in round-up mode.

__host__ __device__ __half __int2half_rz(const int i)
Convert a signed integer to a half in round-towards-zero mode.

__device__ __half2 __ldca(const __half2 *const ptr)
Generates a ld.global.ca load instruction.

__device__ __half __ldca(const __half *const ptr)
Generates a ld.global.ca load instruction.

__device__ __half __ldcg(const __half *const ptr)
Generates a ld.global.cg load instruction.

__device__ __half2 __ldcg(const __half2 *const ptr)
Generates a ld.global.cg load instruction.

__device__ __half __ldcs(const __half *const ptr)
Generates a ld.global.cs load instruction.

__device__ __half2 __ldcs(const __half2 *const ptr)
Generates a ld.global.cs load instruction.

__device__ __half2 __ldcv(const __half2 *const ptr)
Generates a ld.global.cv load instruction.

__device__ __half __ldcv(const __half *const ptr)
Generates a ld.global.cv load instruction.

__device__ __half2 __ldg(const __half2 *const ptr)
Generates a ld.global.nc load instruction.

__device__ __half __ldg(const __half *const ptr)
Generates a ld.global.nc load instruction.

__device__ __half __ldlu(const __half *const ptr)
Generates a ld.global.lu load instruction.

__device__ __half2 __ldlu(const __half2 *const ptr)
Generates a ld.global.lu load instruction.

__host__ __device__ __half __ll2half_rd(const long long int i)
Convert a signed 64-bit integer to a half in round-down mode.

__host__ __device__ __half __ll2half_rn(const long long int i)
Convert a signed 64-bit integer to a half in round-to-nearest-even mode.

__host__ __device__ __half __ll2half_ru(const long long int i)
Convert a signed 64-bit integer to a half in round-up mode.

__host__ __device__ __half __ll2half_rz(const long long int i)
Convert a signed 64-bit integer to a half in round-towards-zero mode.

__host__ __device__ float __low2float(const __half2 a)
Converts low 16 bits of half2 to float and returns the result.

__host__ __device__ __half __low2half(const __half2 a)
Returns low 16 bits of half2 input.

__host__ __device__ __half2 __low2half2(const __half2 a)
Extracts low 16 bits from half2 input.

__host__ __device__ __half2 __lowhigh2highlow(const __half2 a)
Swaps both halves of the half2 input.

__host__ __device__ __half2 __lows2half2(const __half2 a, const __half2 b)
Extracts low 16 bits from each of the two half2 inputs and combines into one half2 number.

__device__ __half __shfl_down_sync(const unsigned int mask, const __half var, const unsigned int delta, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __half2 __shfl_down_sync(const unsigned int mask, const __half2 var, const unsigned int delta, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __half2 __shfl_sync(const unsigned int mask, const __half2 var, const int srcLane, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __half __shfl_sync(const unsigned int mask, const __half var, const int srcLane, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __half2 __shfl_up_sync(const unsigned int mask, const __half2 var, const unsigned int delta, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __half __shfl_up_sync(const unsigned int mask, const __half var, const unsigned int delta, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __half2 __shfl_xor_sync(const unsigned int mask, const __half2 var, const int laneMask, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __half __shfl_xor_sync(const unsigned int mask, const __half var, const int laneMask, const int width=warpSize)
Exchange a variable between threads within a warp.

__host__ __device__ __half __short2half_rd(const short int i)
Convert a signed short integer to a half in round-down mode.

__host__ __device__ __half __short2half_rn(const short int i)
Convert a signed short integer to a half in round-to-nearest-even mode.

__host__ __device__ __half __short2half_ru(const short int i)
Convert a signed short integer to a half in round-up mode.

__host__ __device__ __half __short2half_rz(const short int i)
Convert a signed short integer to a half in round-towards-zero mode.

__host__ __device__ __half __short_as_half(const short int i)
Reinterprets bits in a signed short integer as a half .

__device__ void __stcg(__half2 *const ptr, const __half2 value)
Generates a st.global.cg store instruction.

__device__ void __stcg(__half *const ptr, const __half value)
Generates a st.global.cg store instruction.

__device__ void __stcs(__half2 *const ptr, const __half2 value)
Generates a st.global.cs store instruction.

__device__ void __stcs(__half *const ptr, const __half value)
Generates a st.global.cs store instruction.

__device__ void __stwb(__half2 *const ptr, const __half2 value)
Generates a st.global.wb store instruction.

__device__ void __stwb(__half *const ptr, const __half value)
Generates a st.global.wb store instruction.

__device__ void __stwt(__half *const ptr, const __half value)
Generates a st.global.wt store instruction.

__device__ void __stwt(__half2 *const ptr, const __half2 value)
Generates a st.global.wt store instruction.

__host__ __device__ __half __uint2half_rd(const unsigned int i)
Convert an unsigned integer to a half in round-down mode.

__host__ __device__ __half __uint2half_rn(const unsigned int i)
Convert an unsigned integer to a half in round-to-nearest-even mode.

__host__ __device__ __half __uint2half_ru(const unsigned int i)
Convert an unsigned integer to a half in round-up mode.

__host__ __device__ __half __uint2half_rz(const unsigned int i)
Convert an unsigned integer to a half in round-towards-zero mode.

__host__ __device__ __half __ull2half_rd(const unsigned long long int i)
Convert an unsigned 64-bit integer to a half in round-down mode.

__host__ __device__ __half __ull2half_rn(const unsigned long long int i)
Convert an unsigned 64-bit integer to a half in round-to-nearest-even mode.

__host__ __device__ __half __ull2half_ru(const unsigned long long int i)
Convert an unsigned 64-bit integer to a half in round-up mode.

__host__ __device__ __half __ull2half_rz(const unsigned long long int i)
Convert an unsigned 64-bit integer to a half in round-towards-zero mode.

__host__ __device__ __half __ushort2half_rd(const unsigned short int i)
Convert an unsigned short integer to a half in round-down mode.

__host__ __device__ __half __ushort2half_rn(const unsigned short int i)
Convert an unsigned short integer to a half in round-to-nearest-even mode.

__host__ __device__ __half __ushort2half_ru(const unsigned short int i)
Convert an unsigned short integer to a half in round-up mode.

__host__ __device__ __half __ushort2half_rz(const unsigned short int i)
Convert an unsigned short integer to a half in round-towards-zero mode.

__host__ __device__ __half __ushort_as_half(const unsigned short int i)
Reinterprets bits in an unsigned short integer as a half .

__host__ __device__ __half2 make_half2(const __half x, const __half y)
Vector function, combines two __half numbers into one __half2 number.


## 4.5.1. Functions


__host__ __device__ __half __double2half(const double a)
Converts double number to half precision in round-to-nearest-even mode and returns half with converted value.
Converts double number a to half precision in round-to-nearest-even mode.

Parameters

a – [in] - double. Is only being read.

Returns

half

a converted to half precision using round-to-nearest-even mode.
__double2half \( (\pm 0)\) returns \( \pm 0 \).
__double2half \( (\pm \infty)\) returns \( \pm \infty \).
__double2half(NaN) returns NaN.


__host__ __device__ __half2 __float22half2_rn(const float2 a)
Converts both components of float2 number to half precision in round-to-nearest-even mode and returns half2 with converted values.
Converts both components of float2 to half precision in round-to-nearest-even mode and combines the results into one half2 number. Low 16 bits of the return value correspond to a.x and high 16 bits of the return value correspond to a.y.

See also
__float2half_rn(float) for further details.

Parameters

a – [in] - float2. Is only being read.

Returns

half2

The half2 which has corresponding halves equal to the converted float2 components.


__host__ __device__ __half __float2half(const float a)
Converts float number to half precision in round-to-nearest-even mode and returns half with converted value.
Converts float number a to half precision in round-to-nearest-even mode.

See also
__float2half_rn(float) for further details.

Parameters

a – [in] - float. Is only being read.

Returns

half

a converted to half precision using round-to-nearest-even mode.


__host__ __device__ __half2 __float2half2_rn(const float a)
Converts input to half precision in round-to-nearest-even mode and populates both halves of half2 with converted value.
Converts input a to half precision in round-to-nearest-even mode and populates both halves of half2 with converted value.

See also
__float2half_rn(float) for further details.

Parameters

a – [in] - float. Is only being read.

Returns

half2

The half2 value with both halves equal to the converted half precision number.


__host__ __device__ __half __float2half_rd(const float a)
Converts float number to half precision in round-down mode and returns half with converted value.
Converts float number a to half precision in round-down mode.

Parameters

a – [in] - float. Is only being read.

Returns

half

a converted to half precision using round-down mode.
__float2half_rd \( (\pm 0)\) returns \( \pm 0 \).
__float2half_rd \( (\pm \infty)\) returns \( \pm \infty \).
__float2half_rd(NaN) returns NaN.


__host__ __device__ __half __float2half_rn(const float a)
Converts float number to half precision in round-to-nearest-even mode and returns half with converted value.
Converts float number a to half precision in round-to-nearest-even mode.

Parameters

a – [in] - float. Is only being read.

Returns

half

a converted to half precision using round-to-nearest-even mode.
__float2half_rn \( (\pm 0)\) returns \( \pm 0 \).
__float2half_rn \( (\pm \infty)\) returns \( \pm \infty \).
__float2half_rn(NaN) returns NaN.


__host__ __device__ __half __float2half_ru(const float a)
Converts float number to half precision in round-up mode and returns half with converted value.
Converts float number a to half precision in round-up mode.

Parameters

a – [in] - float. Is only being read.

Returns

half

a converted to half precision using round-up mode.
__float2half_ru \( (\pm 0)\) returns \( \pm 0 \).
__float2half_ru \( (\pm \infty)\) returns \( \pm \infty \).
__float2half_ru(NaN) returns NaN.


__host__ __device__ __half __float2half_rz(const float a)
Converts float number to half precision in round-towards-zero mode and returns half with converted value.
Converts float number a to half precision in round-towards-zero mode.

Parameters

a – [in] - float. Is only being read.

Returns

half

a converted to half precision using round-towards-zero mode.
__float2half_rz \( (\pm 0)\) returns \( \pm 0 \).
__float2half_rz \( (\pm \infty)\) returns \( \pm \infty \).
__float2half_rz(NaN) returns NaN.


__host__ __device__ __half2 __floats2half2_rn(const float a, const float b)
Converts both input floats to half precision in round-to-nearest-even mode and returns half2 with converted values.
Converts both input floats to half precision in round-to-nearest-even mode and combines the results into one half2 number. Low 16 bits of the return value correspond to the input a, high 16 bits correspond to the input b.

See also
__float2half_rn(float) for further details.

Parameters

a – [in] - float. Is only being read.
b – [in] - float. Is only being read.

Returns

half2

The half2 value with corresponding halves equal to the converted input floats.


__host__ __device__ float2 __half22float2(const __half2 a)
Converts both halves of half2 to float2 and returns the result.
Converts both halves of half2 input a to float2 and returns the result.

See also
__half2float(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

float2

a converted to float2.


__host__ __device__ signed char __half2char_rz(const __half h)
Convert a half to a signed char in round-towards-zero mode.
Convert the half-precision floating-point value h to a signed char integer in round-towards-zero mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

signed char

h converted to a signed char using round-towards-zero mode.
__half2char_rz \( (\pm 0)\) returns 0.
__half2char_rz \( (x), x > 127\) returns SCHAR_MAX = 0x7F.
__half2char_rz \( (x), x < -128\) returns SCHAR_MIN = 0x80.
__half2char_rz(NaN) returns 0.


__host__ __device__ float __half2float(const __half a)
Converts half number to float.
Converts half number a to float.

Parameters

a – [in] - float. Is only being read.

Returns

float

a converted to float.
__half2float \( (\pm 0)\) returns \( \pm 0 \).
__half2float \( (\pm \infty)\) returns \( \pm \infty \).
__half2float(NaN) returns NaN.


__host__ __device__ __half2 __half2half2(const __half a)
Returns half2 with both halves equal to the input value.
Returns half2 number with both halves equal to the input a half number.

Parameters

a – [in] - half. Is only being read.

Returns

half2

The vector which has both its halves equal to the input a.


__device__ int __half2int_rd(const __half h)
Convert a half to a signed integer in round-down mode.
Convert the half-precision floating-point value h to a signed integer in round-down mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

int

h converted to a signed integer using round-down mode.
__half2int_rd \( (\pm 0)\) returns 0.
__half2int_rd \( (+\infty)\) returns INT_MAX = 0x7FFFFFFF.
__half2int_rd \( (-\infty)\) returns INT_MIN = 0x80000000.
__half2int_rd(NaN) returns 0.


__device__ int __half2int_rn(const __half h)
Convert a half to a signed integer in round-to-nearest-even mode.
Convert the half-precision floating-point value h to a signed integer in round-to-nearest-even mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

int

h converted to a signed integer using round-to-nearest-even mode.
__half2int_rn \( (\pm 0)\) returns 0.
__half2int_rn \( (+\infty)\) returns INT_MAX = 0x7FFFFFFF.
__half2int_rn \( (-\infty)\) returns INT_MIN = 0x80000000.
__half2int_rn(NaN) returns 0.


__device__ int __half2int_ru(const __half h)
Convert a half to a signed integer in round-up mode.
Convert the half-precision floating-point value h to a signed integer in round-up mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

int

h converted to a signed integer using round-up mode.
__half2int_ru \( (\pm 0)\) returns 0.
__half2int_ru \( (+\infty)\) returns INT_MAX = 0x7FFFFFFF.
__half2int_ru \( (-\infty)\) returns INT_MIN = 0x80000000.
__half2int_ru(NaN) returns 0.


__host__ __device__ int __half2int_rz(const __half h)
Convert a half to a signed integer in round-towards-zero mode.
Convert the half-precision floating-point value h to a signed integer in round-towards-zero mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

int

h converted to a signed integer using round-towards-zero mode.
__half2int_rz \( (\pm 0)\) returns 0.
__half2int_rz \( (+\infty)\) returns INT_MAX = 0x7FFFFFFF.
__half2int_rz \( (-\infty)\) returns INT_MIN = 0x80000000.
__half2int_rz(NaN) returns 0.


__device__ long long int __half2ll_rd(const __half h)
Convert a half to a signed 64-bit integer in round-down mode.
Convert the half-precision floating-point value h to a signed 64-bit integer in round-down mode. NaN inputs return a long long int with hex value of 0x8000000000000000.

Parameters

h – [in] - half. Is only being read.

Returns

long long int

h converted to a signed 64-bit integer using round-down mode.
__half2ll_rd \( (\pm 0)\) returns 0.
__half2ll_rd \( (+\infty)\) returns LLONG_MAX = 0x7FFFFFFFFFFFFFFF.
__half2ll_rd \( (-\infty)\) returns LLONG_MIN = 0x8000000000000000.
__half2ll_rd(NaN) returns 0x8000000000000000.


__device__ long long int __half2ll_rn(const __half h)
Convert a half to a signed 64-bit integer in round-to-nearest-even mode.
Convert the half-precision floating-point value h to a signed 64-bit integer in round-to-nearest-even mode. NaN inputs return a long long int with hex value of 0x8000000000000000.

Parameters

h – [in] - half. Is only being read.

Returns

long long int

h converted to a signed 64-bit integer using round-to-nearest-even mode.
__half2ll_rn \( (\pm 0)\) returns 0.
__half2ll_rn \( (+\infty)\) returns LLONG_MAX = 0x7FFFFFFFFFFFFFFF.
__half2ll_rn \( (-\infty)\) returns LLONG_MIN = 0x8000000000000000.
__half2ll_rn(NaN) returns 0x8000000000000000.


__device__ long long int __half2ll_ru(const __half h)
Convert a half to a signed 64-bit integer in round-up mode.
Convert the half-precision floating-point value h to a signed 64-bit integer in round-up mode. NaN inputs return a long long int with hex value of 0x8000000000000000.

Parameters

h – [in] - half. Is only being read.

Returns

long long int

h converted to a signed 64-bit integer using round-up mode.
__half2ll_ru \( (\pm 0)\) returns 0.
__half2ll_ru \( (+\infty)\) returns LLONG_MAX = 0x7FFFFFFFFFFFFFFF.
__half2ll_ru \( (-\infty)\) returns LLONG_MIN = 0x8000000000000000.
__half2ll_ru(NaN) returns 0x8000000000000000.


__host__ __device__ long long int __half2ll_rz(const __half h)
Convert a half to a signed 64-bit integer in round-towards-zero mode.
Convert the half-precision floating-point value h to a signed 64-bit integer in round-towards-zero mode. NaN inputs return a long long int with hex value of 0x8000000000000000.

Parameters

h – [in] - half. Is only being read.

Returns

long long int

h converted to a signed 64-bit integer using round-towards-zero mode.
__half2ll_rz \( (\pm 0)\) returns 0.
__half2ll_rz \( (+\infty)\) returns LLONG_MAX = 0x7FFFFFFFFFFFFFFF.
__half2ll_rz \( (-\infty)\) returns LLONG_MIN = 0x8000000000000000.
__half2ll_rz(NaN) returns 0x8000000000000000.


__device__ short int __half2short_rd(const __half h)
Convert a half to a signed short integer in round-down mode.
Convert the half-precision floating-point value h to a signed short integer in round-down mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

short int

h converted to a signed short integer using round-down mode.
__half2short_rd \( (\pm 0)\) returns 0.
__half2short_rd \( (x), x > 32767\) returns SHRT_MAX = 0x7FFF.
__half2short_rd \( (x), x < -32768\) returns SHRT_MIN = 0x8000.
__half2short_rd(NaN) returns 0.


__device__ short int __half2short_rn(const __half h)
Convert a half to a signed short integer in round-to-nearest-even mode.
Convert the half-precision floating-point value h to a signed short integer in round-to-nearest-even mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

short int

h converted to a signed short integer using round-to-nearest-even mode.
__half2short_rn \( (\pm 0)\) returns 0.
__half2short_rn \( (x), x > 32767\) returns SHRT_MAX = 0x7FFF.
__half2short_rn \( (x), x < -32768\) returns SHRT_MIN = 0x8000.
__half2short_rn(NaN) returns 0.


__device__ short int __half2short_ru(const __half h)
Convert a half to a signed short integer in round-up mode.
Convert the half-precision floating-point value h to a signed short integer in round-up mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

short int

h converted to a signed short integer using round-up mode.
__half2short_ru \( (\pm 0)\) returns 0.
__half2short_ru \( (x), x > 32767\) returns SHRT_MAX = 0x7FFF.
__half2short_ru \( (x), x < -32768\) returns SHRT_MIN = 0x8000.
__half2short_ru(NaN) returns 0.


__host__ __device__ short int __half2short_rz(const __half h)
Convert a half to a signed short integer in round-towards-zero mode.
Convert the half-precision floating-point value h to a signed short integer in round-towards-zero mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

short int

h converted to a signed short integer using round-towards-zero mode.
__half2short_rz \( (\pm 0)\) returns 0.
__half2short_rz \( (x), x > 32767\) returns SHRT_MAX = 0x7FFF.
__half2short_rz \( (x), x < -32768\) returns SHRT_MIN = 0x8000.
__half2short_rz(NaN) returns 0.


__host__ __device__ unsigned char __half2uchar_rz(const __half h)
Convert a half to an unsigned char in round-towards-zero mode.
Convert the half-precision floating-point value h to an unsigned char in round-towards-zero mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned char

h converted to an unsigned char using round-towards-zero mode.
__half2uchar_rz \( (\pm 0)\) returns 0.
__half2uchar_rz \( (x), x > 255\) returns UCHAR_MAX = 0xFF.
__half2uchar_rz \( (x), x < 0.0\) returns 0.
__half2uchar_rz(NaN) returns 0.


__device__ unsigned int __half2uint_rd(const __half h)
Convert a half to an unsigned integer in round-down mode.
Convert the half-precision floating-point value h to an unsigned integer in round-down mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned int

h converted to an unsigned integer using round-down mode.
__half2uint_rd \( (\pm 0)\) returns 0.
__half2uint_rd \( (+\infty)\) returns UINT_MAX = 0xFFFFFFFF.
__half2uint_rd \( (x), x < 0.0\) returns 0.
__half2uint_rd(NaN) returns 0.


__device__ unsigned int __half2uint_rn(const __half h)
Convert a half to an unsigned integer in round-to-nearest-even mode.
Convert the half-precision floating-point value h to an unsigned integer in round-to-nearest-even mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned int

h converted to an unsigned integer using round-to-nearest-even mode.
__half2uint_rn \( (\pm 0)\) returns 0.
__half2uint_rn \( (+\infty)\) returns UINT_MAX = 0xFFFFFFFF.
__half2uint_rn \( (x), x < 0.0\) returns 0.
__half2uint_rn(NaN) returns 0.


__device__ unsigned int __half2uint_ru(const __half h)
Convert a half to an unsigned integer in round-up mode.
Convert the half-precision floating-point value h to an unsigned integer in round-up mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned int

h converted to an unsigned integer using round-up mode.
__half2uint_ru \( (\pm 0)\) returns 0.
__half2uint_ru \( (+\infty)\) returns UINT_MAX = 0xFFFFFFFF.
__half2uint_ru \( (x), x < 0.0\) returns 0.
__half2uint_ru(NaN) returns 0.


__host__ __device__ unsigned int __half2uint_rz(const __half h)
Convert a half to an unsigned integer in round-towards-zero mode.
Convert the half-precision floating-point value h to an unsigned integer in round-towards-zero mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned int

h converted to an unsigned integer using round-towards-zero mode.
__half2uint_rz \( (\pm 0)\) returns 0.
__half2uint_rz \( (+\infty)\) returns UINT_MAX = 0xFFFFFFFF.
__half2uint_rz \( (x), x < 0.0\) returns 0.
__half2uint_rz(NaN) returns 0.


__device__ unsigned long long int __half2ull_rd(const __half h)
Convert a half to an unsigned 64-bit integer in round-down mode.
Convert the half-precision floating-point value h to an unsigned 64-bit integer in round-down mode. NaN inputs return 0x8000000000000000.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned long long int

h converted to an unsigned 64-bit integer using round-down mode.
__half2ull_rd \( (\pm 0)\) returns 0.
__half2ull_rd \( (+\infty)\) returns ULLONG_MAX = 0xFFFFFFFFFFFFFFFF.
__half2ull_rd \( (x), x < 0.0\) returns 0.
__half2ull_rd(NaN) returns 0x8000000000000000.


__device__ unsigned long long int __half2ull_rn(const __half h)
Convert a half to an unsigned 64-bit integer in round-to-nearest-even mode.
Convert the half-precision floating-point value h to an unsigned 64-bit integer in round-to-nearest-even mode. NaN inputs return 0x8000000000000000.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned long long int

h converted to an unsigned 64-bit integer using round-to-nearest-even mode.
__half2ull_rn \( (\pm 0)\) returns 0.
__half2ull_rn \( (+\infty)\) returns ULLONG_MAX = 0xFFFFFFFFFFFFFFFF.
__half2ull_rn \( (x), x < 0.0\) returns 0.
__half2ull_rn(NaN) returns 0x8000000000000000.


__device__ unsigned long long int __half2ull_ru(const __half h)
Convert a half to an unsigned 64-bit integer in round-up mode.
Convert the half-precision floating-point value h to an unsigned 64-bit integer in round-up mode. NaN inputs return 0x8000000000000000.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned long long int

h converted to an unsigned 64-bit integer using round-up mode.
__half2ull_ru \( (\pm 0)\) returns 0.
__half2ull_ru \( (+\infty)\) returns ULLONG_MAX = 0xFFFFFFFFFFFFFFFF.
__half2ull_ru \( (x), x < 0.0\) returns 0.
__half2ull_ru(NaN) returns 0x8000000000000000.


__host__ __device__ unsigned long long int __half2ull_rz(const __half h)
Convert a half to an unsigned 64-bit integer in round-towards-zero mode.
Convert the half-precision floating-point value h to an unsigned 64-bit integer in round-towards-zero mode. NaN inputs return 0x8000000000000000.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned long long int

h converted to an unsigned 64-bit integer using round-towards-zero mode.
__half2ull_rz \( (\pm 0)\) returns 0.
__half2ull_rz \( (+\infty)\) returns ULLONG_MAX = 0xFFFFFFFFFFFFFFFF.
__half2ull_rz \( (x), x < 0.0\) returns 0.
__half2ull_rz(NaN) returns 0x8000000000000000.


__device__ unsigned short int __half2ushort_rd(const __half h)
Convert a half to an unsigned short integer in round-down mode.
Convert the half-precision floating-point value h to an unsigned short integer in round-down mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned short int

h converted to an unsigned short integer using round-down mode.
__half2ushort_rd \( (\pm 0)\) returns 0.
__half2ushort_rd \( (+\infty)\) returns USHRT_MAX = 0xFFFF.
__half2ushort_rd \( (x), x < 0.0\) returns 0.
__half2ushort_rd(NaN) returns 0.


__device__ unsigned short int __half2ushort_rn(const __half h)
Convert a half to an unsigned short integer in round-to-nearest-even mode.
Convert the half-precision floating-point value h to an unsigned short integer in round-to-nearest-even mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned short int

h converted to an unsigned short integer using round-to-nearest-even mode.
__half2ushort_rn \( (\pm 0)\) returns 0.
__half2ushort_rn \( (+\infty)\) returns USHRT_MAX = 0xFFFF.
__half2ushort_rn \( (x), x < 0.0\) returns 0.
__half2ushort_rn(NaN) returns 0.


__device__ unsigned short int __half2ushort_ru(const __half h)
Convert a half to an unsigned short integer in round-up mode.
Convert the half-precision floating-point value h to an unsigned short integer in round-up mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned short int

h converted to an unsigned short integer using round-up mode.
__half2ushort_ru \( (\pm 0)\) returns 0.
__half2ushort_ru \( (+\infty)\) returns USHRT_MAX = 0xFFFF.
__half2ushort_ru \( (x), x < 0.0\) returns 0.
__half2ushort_ru(NaN) returns 0.


__host__ __device__ unsigned short int __half2ushort_rz(const __half h)
Convert a half to an unsigned short integer in round-towards-zero mode.
Convert the half-precision floating-point value h to an unsigned short integer in round-towards-zero mode. NaN inputs are converted to 0.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned short int

h converted to an unsigned short integer using round-towards-zero mode.
__half2ushort_rz \( (\pm 0)\) returns 0.
__half2ushort_rz \( (+\infty)\) returns USHRT_MAX = 0xFFFF.
__half2ushort_rz \( (x), x < 0.0\) returns 0.
__half2ushort_rz(NaN) returns 0.


__host__ __device__ short int __half_as_short(const __half h)
Reinterprets bits in a half as a signed short integer.
Reinterprets the bits in the half-precision floating-point number h as a signed short integer.

Parameters

h – [in] - half. Is only being read.

Returns

short int

The reinterpreted value.


__host__ __device__ unsigned short int __half_as_ushort(const __half h)
Reinterprets bits in a half as an unsigned short integer.
Reinterprets the bits in the half-precision floating-point h as an unsigned short number.

Parameters

h – [in] - half. Is only being read.

Returns

unsigned short int

The reinterpreted value.


__host__ __device__ __half2 __halves2half2(const __half a, const __half b)
Combines two half numbers into one half2 number.
Combines two input half number a and b into one half2 number. Input a is stored in low 16 bits of the return value, input b is stored in high 16 bits of the return value.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half2

The half2 with one half equal to a and the other to b.


__host__ __device__ float __high2float(const __half2 a)
Converts high 16 bits of half2 to float and returns the result.
Converts high 16 bits of half2 input a to 32-bit floating-point number and returns the result.

See also
__half2float(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

float

The high 16 bits of a converted to float.


__host__ __device__ __half __high2half(const __half2 a)
Returns high 16 bits of half2 input.
Returns high 16 bits of half2 input a.

Parameters

a – [in] - half2. Is only being read.

Returns

half

The high 16 bits of the input.


__host__ __device__ __half2 __high2half2(const __half2 a)
Extracts high 16 bits from half2 input.
Extracts high 16 bits from half2 input a and returns a new half2 number which has both halves equal to the extracted bits.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The half2 with both halves equal to the high 16 bits of the input.


__host__ __device__ __half2 __highs2half2(const __half2 a, const __half2 b)
Extracts high 16 bits from each of the two half2 inputs and combines into one half2 number.
Extracts high 16 bits from each of the two half2 inputs and combines into one half2 number. High 16 bits from input a is stored in low 16 bits of the return value, high 16 bits from input b is stored in high 16 bits of the return value.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The high 16 bits of a and of b.


__host__ __device__ __half __int2half_rd(const int i)
Convert a signed integer to a half in round-down mode.
Convert the signed integer value i to a half-precision floating-point value in round-down mode.

Parameters

i – [in] - int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __int2half_rn(const int i)
Convert a signed integer to a half in round-to-nearest-even mode.
Convert the signed integer value i to a half-precision floating-point value in round-to-nearest-even mode.

Parameters

i – [in] - int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __int2half_ru(const int i)
Convert a signed integer to a half in round-up mode.
Convert the signed integer value i to a half-precision floating-point value in round-up mode.

Parameters

i – [in] - int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __int2half_rz(const int i)
Convert a signed integer to a half in round-towards-zero mode.
Convert the signed integer value i to a half-precision floating-point value in round-towards-zero mode.

Parameters

i – [in] - int. Is only being read.

Returns

half

i converted to half.


__device__ __half2 __ldca(const __half2 *const ptr)
Generates a ld.global.ca load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __half __ldca(const __half *const ptr)
Generates a ld.global.ca load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __half __ldcg(const __half *const ptr)
Generates a ld.global.cg load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __half2 __ldcg(const __half2 *const ptr)
Generates a ld.global.cg load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __half __ldcs(const __half *const ptr)
Generates a ld.global.cs load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __half2 __ldcs(const __half2 *const ptr)
Generates a ld.global.cs load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __half2 __ldcv(const __half2 *const ptr)
Generates a ld.global.cv load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __half __ldcv(const __half *const ptr)
Generates a ld.global.cv load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __half2 __ldg(const __half2 *const ptr)
Generates a ld.global.nc load instruction.
defined(CUDA_ARCH) || (CUDA_ARCH >= 300)

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __half __ldg(const __half *const ptr)
Generates a ld.global.nc load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __half __ldlu(const __half *const ptr)
Generates a ld.global.lu load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __half2 __ldlu(const __half2 *const ptr)
Generates a ld.global.lu load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__host__ __device__ __half __ll2half_rd(const long long int i)
Convert a signed 64-bit integer to a half in round-down mode.
Convert the signed 64-bit integer value i to a half-precision floating-point value in round-down mode.

Parameters

i – [in] - long long int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __ll2half_rn(const long long int i)
Convert a signed 64-bit integer to a half in round-to-nearest-even mode.
Convert the signed 64-bit integer value i to a half-precision floating-point value in round-to-nearest-even mode.

Parameters

i – [in] - long long int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __ll2half_ru(const long long int i)
Convert a signed 64-bit integer to a half in round-up mode.
Convert the signed 64-bit integer value i to a half-precision floating-point value in round-up mode.

Parameters

i – [in] - long long int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __ll2half_rz(const long long int i)
Convert a signed 64-bit integer to a half in round-towards-zero mode.
Convert the signed 64-bit integer value i to a half-precision floating-point value in round-towards-zero mode.

Parameters

i – [in] - long long int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ float __low2float(const __half2 a)
Converts low 16 bits of half2 to float and returns the result.
Converts low 16 bits of half2 input a to 32-bit floating-point number and returns the result.

See also
__half2float(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

float

The low 16 bits of a converted to float.


__host__ __device__ __half __low2half(const __half2 a)
Returns low 16 bits of half2 input.
Returns low 16 bits of half2 input a.

Parameters

a – [in] - half2. Is only being read.

Returns

half

Returns half which contains low 16 bits of the input a.


__host__ __device__ __half2 __low2half2(const __half2 a)
Extracts low 16 bits from half2 input.
Extracts low 16 bits from half2 input a and returns a new half2 number which has both halves equal to the extracted bits.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The half2 with both halves equal to the low 16 bits of the input.


__host__ __device__ __half2 __lowhigh2highlow(const __half2 a)
Swaps both halves of the half2 input.
Swaps both halves of the half2 input and returns a new half2 number with swapped halves.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

a with its halves being swapped.


__host__ __device__ __half2 __lows2half2(const __half2 a, const __half2 b)
Extracts low 16 bits from each of the two half2 inputs and combines into one half2 number.
Extracts low 16 bits from each of the two half2 inputs and combines into one half2 number. Low 16 bits from input a is stored in low 16 bits of the return value, low 16 bits from input b is stored in high 16 bits of the return value.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The low 16 bits of a and of b.


__device__ __half __shfl_down_sync(const unsigned int mask, const __half var, const unsigned int delta, const int width = warpSize)
Exchange a variable between threads within a warp.
Copy from a thread with higher ID relative to the caller.
Calculates a source thread ID by adding delta to the caller’s thread ID. The value of var held by the resulting thread ID is returned: this has the effect of shifting var down the warp by delta threads. If the width is less than warpSize, then each subsection of the warp behaves as a separate entity with a starting logical thread ID of 0. Similarly to the __shfl_up_sync(), the ID number of the source thread will not wrap around the value of width and the upper delta threads will remain unchanged. Threads may only read data from another thread which is actively participating in the __shfl_*sync() command. If the target thread is inactive, the retrieved value is undefined.

Note
For more details about this function, see the Warp Shuffle Functions section in the CUDA C++ Programming Guide.

Parameters

mask – [in] - unsigned int. Is only being read.

Indicates the threads participating in the call.
A bit, representing the thread’s lane ID, must be set for each participating thread to ensure they are properly converged before the intrinsic is executed by the hardware.
Each calling thread must have its own bit set in the mask and all non-exited threads named in mask must execute the same intrinsic with the same mask, or the result is undefined.

var – [in] - half. Is only being read.
delta – [in] - unsigned int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 2-byte word referenced by var from the source thread ID as half.


__device__ __half2 __shfl_down_sync(const unsigned int mask, const __half2 var, const unsigned int delta, const int width = warpSize)
Exchange a variable between threads within a warp.
Copy from a thread with higher ID relative to the caller.
Calculates a source thread ID by adding delta to the caller’s thread ID. The value of var held by the resulting thread ID is returned: this has the effect of shifting var down the warp by delta threads. If the width is less than warpSize, then each subsection of the warp behaves as a separate entity with a starting logical thread ID of 0. Similarly to the __shfl_up_sync(), the ID number of the source thread will not wrap around the value of width and the upper delta threads will remain unchanged. Threads may only read data from another thread which is actively participating in the __shfl_*sync() command. If the target thread is inactive, the retrieved value is undefined.

Note
For more details about this function, see the Warp Shuffle Functions section in the CUDA C++ Programming Guide.

Parameters

mask – [in] - unsigned int. Is only being read.

Indicates the threads participating in the call.
A bit, representing the thread’s lane ID, must be set for each participating thread to ensure they are properly converged before the intrinsic is executed by the hardware.
Each calling thread must have its own bit set in the mask and all non-exited threads named in mask must execute the same intrinsic with the same mask, or the result is undefined.

var – [in] - half2. Is only being read.
delta – [in] - unsigned int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 4-byte word referenced by var from the source thread ID as half2.


__device__ __half2 __shfl_sync(const unsigned int mask, const __half2 var, const int srcLane, const int width = warpSize)
Exchange a variable between threads within a warp.
Direct copy from indexed thread.
Returns the value of var held by the thread whose ID is given by srcLane. If the width is less than warpSize, then each subsection of the warp behaves as a separate entity with a starting logical thread ID of 0. If srcLane is outside the range [0:width-1], the value returned corresponds to the value of var held by the srcLane modulo width (i.e. within the same subsection). width must have a value which is a power of 2; results are undefined if width is not a power of 2, or is a number greater than warpSize. Threads may only read data from another thread which is actively participating in the __shfl_*sync() command. If the target thread is inactive, the retrieved value is undefined.

Note
For more details about this function, see the Warp Shuffle Functions section in the CUDA C++ Programming Guide.

Parameters

mask – [in] - unsigned int. Is only being read.

Indicates the threads participating in the call.
A bit, representing the thread’s lane ID, must be set for each participating thread to ensure they are properly converged before the intrinsic is executed by the hardware.
Each calling thread must have its own bit set in the mask and all non-exited threads named in mask must execute the same intrinsic with the same mask, or the result is undefined.

var – [in] - half2. Is only being read.
srcLane – [in] - int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 4-byte word referenced by var from the source thread ID as half2.


__device__ __half __shfl_sync(const unsigned int mask, const __half var, const int srcLane, const int width = warpSize)
Exchange a variable between threads within a warp.
Direct copy from indexed thread.
Returns the value of var held by the thread whose ID is given by srcLane. If the width is less than warpSize, then each subsection of the warp behaves as a separate entity with a starting logical thread ID of 0. If srcLane is outside the range [0:width-1], the value returned corresponds to the value of var held by the srcLane modulo width (i.e. within the same subsection). width must have a value which is a power of 2; results are undefined if width is not a power of 2, or is a number greater than warpSize. Threads may only read data from another thread which is actively participating in the __shfl_*sync() command. If the target thread is inactive, the retrieved value is undefined.

Note
For more details about this function, see the Warp Shuffle Functions section in the CUDA C++ Programming Guide.

Parameters

mask – [in] - unsigned int. Is only being read.

Indicates the threads participating in the call.
A bit, representing the thread’s lane ID, must be set for each participating thread to ensure they are properly converged before the intrinsic is executed by the hardware.
Each calling thread must have its own bit set in the mask and all non-exited threads named in mask must execute the same intrinsic with the same mask, or the result is undefined.

var – [in] - half. Is only being read.
srcLane – [in] - int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 2-byte word referenced by var from the source thread ID as half.


__device__ __half2 __shfl_up_sync(const unsigned int mask, const __half2 var, const unsigned int delta, const int width = warpSize)
Exchange a variable between threads within a warp.
Copy from a thread with lower ID relative to the caller.
Calculates a source thread ID by subtracting delta from the caller’s lane ID. The value of var held by the resulting lane ID is returned: in effect, var is shifted up the warp by delta threads. If the width is less than warpSize, then each subsection of the warp behaves as a separate entity with a starting logical thread ID of 0. The source thread index will not wrap around the value of width, so effectively the lower delta threads will be unchanged. width must have a value which is a power of 2; results are undefined if width is not a power of 2, or is a number greater than warpSize. Threads may only read data from another thread which is actively participating in the __shfl_*sync() command. If the target thread is inactive, the retrieved value is undefined.

Note
For more details about this function, see the Warp Shuffle Functions section in the CUDA C++ Programming Guide.

Parameters

mask – [in] - unsigned int. Is only being read.

Indicates the threads participating in the call.
A bit, representing the thread’s lane ID, must be set for each participating thread to ensure they are properly converged before the intrinsic is executed by the hardware.
Each calling thread must have its own bit set in the mask and all non-exited threads named in mask must execute the same intrinsic with the same mask, or the result is undefined.

var – [in] - half2. Is only being read.
delta – [in] - unsigned int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 4-byte word referenced by var from the source thread ID as half2.


__device__ __half __shfl_up_sync(const unsigned int mask, const __half var, const unsigned int delta, const int width = warpSize)
Exchange a variable between threads within a warp.
Copy from a thread with lower ID relative to the caller.
Calculates a source thread ID by subtracting delta from the caller’s lane ID. The value of var held by the resulting lane ID is returned: in effect, var is shifted up the warp by delta threads. If the width is less than warpSize, then each subsection of the warp behaves as a separate entity with a starting logical thread ID of 0. The source thread index will not wrap around the value of width, so effectively the lower delta threads will be unchanged. width must have a value which is a power of 2; results are undefined if width is not a power of 2, or is a number greater than warpSize. Threads may only read data from another thread which is actively participating in the __shfl_*sync() command. If the target thread is inactive, the retrieved value is undefined.

Note
For more details about this function, see the Warp Shuffle Functions section in the CUDA C++ Programming Guide.

Parameters

mask – [in] - unsigned int. Is only being read.

Indicates the threads participating in the call.
A bit, representing the thread’s lane ID, must be set for each participating thread to ensure they are properly converged before the intrinsic is executed by the hardware.
Each calling thread must have its own bit set in the mask and all non-exited threads named in mask must execute the same intrinsic with the same mask, or the result is undefined.

var – [in] - half. Is only being read.
delta – [in] - unsigned int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 2-byte word referenced by var from the source thread ID as half.


__device__ __half2 __shfl_xor_sync(const unsigned int mask, const __half2 var, const int laneMask, const int width = warpSize)
Exchange a variable between threads within a warp.
Copy from a thread based on bitwise XOR of own thread ID.
Calculates a source thread ID by performing a bitwise XOR of the caller’s thread ID with laneMask: the value of var held by the resulting thread ID is returned. If the width is less than warpSize, then each group of width consecutive threads are able to access elements from earlier groups of threads, however if they attempt to access elements from later groups of threads their own value of var will be returned. This mode implements a butterfly addressing pattern such as is used in tree reduction and broadcast. Threads may only read data from another thread which is actively participating in the __shfl_*sync() command. If the target thread is inactive, the retrieved value is undefined.

Note
For more details about this function, see the Warp Shuffle Functions section in the CUDA C++ Programming Guide.

Parameters

mask – [in] - unsigned int. Is only being read.

Indicates the threads participating in the call.
A bit, representing the thread’s lane ID, must be set for each participating thread to ensure they are properly converged before the intrinsic is executed by the hardware.
Each calling thread must have its own bit set in the mask and all non-exited threads named in mask must execute the same intrinsic with the same mask, or the result is undefined.

var – [in] - half2. Is only being read.
laneMask – [in] - int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 4-byte word referenced by var from the source thread ID as half2.


__device__ __half __shfl_xor_sync(const unsigned int mask, const __half var, const int laneMask, const int width = warpSize)
Exchange a variable between threads within a warp.
Copy from a thread based on bitwise XOR of own thread ID.
Calculates a source thread ID by performing a bitwise XOR of the caller’s thread ID with laneMask: the value of var held by the resulting thread ID is returned. If the width is less than warpSize, then each group of width consecutive threads are able to access elements from earlier groups of threads, however if they attempt to access elements from later groups of threads their own value of var will be returned. This mode implements a butterfly addressing pattern such as is used in tree reduction and broadcast. Threads may only read data from another thread which is actively participating in the __shfl_*sync() command. If the target thread is inactive, the retrieved value is undefined.

Note
For more details about this function, see the Warp Shuffle Functions section in the CUDA C++ Programming Guide.

Parameters

mask – [in] - unsigned int. Is only being read.

Indicates the threads participating in the call.
A bit, representing the thread’s lane ID, must be set for each participating thread to ensure they are properly converged before the intrinsic is executed by the hardware.
Each calling thread must have its own bit set in the mask and all non-exited threads named in mask must execute the same intrinsic with the same mask, or the result is undefined.

var – [in] - half. Is only being read.
laneMask – [in] - int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 2-byte word referenced by var from the source thread ID as half.


__host__ __device__ __half __short2half_rd(const short int i)
Convert a signed short integer to a half in round-down mode.
Convert the signed short integer value i to a half-precision floating-point value in round-down mode.

Parameters

i – [in] - short int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __short2half_rn(const short int i)
Convert a signed short integer to a half in round-to-nearest-even mode.
Convert the signed short integer value i to a half-precision floating-point value in round-to-nearest-even mode.

Parameters

i – [in] - short int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __short2half_ru(const short int i)
Convert a signed short integer to a half in round-up mode.
Convert the signed short integer value i to a half-precision floating-point value in round-up mode.

Parameters

i – [in] - short int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __short2half_rz(const short int i)
Convert a signed short integer to a half in round-towards-zero mode.
Convert the signed short integer value i to a half-precision floating-point value in round-towards-zero mode.

Parameters

i – [in] - short int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __short_as_half(const short int i)
Reinterprets bits in a signed short integer as a half.
Reinterprets the bits in the signed short integer i as a half-precision floating-point number.

Parameters

i – [in] - short int. Is only being read.

Returns

half

The reinterpreted value.


__device__ void __stcg(__half2 *const ptr, const __half2 value)
Generates a st.global.cg store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stcg(__half *const ptr, const __half value)
Generates a st.global.cg store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stcs(__half2 *const ptr, const __half2 value)
Generates a st.global.cs store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stcs(__half *const ptr, const __half value)
Generates a st.global.cs store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stwb(__half2 *const ptr, const __half2 value)
Generates a st.global.wb store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stwb(__half *const ptr, const __half value)
Generates a st.global.wb store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stwt(__half *const ptr, const __half value)
Generates a st.global.wt store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stwt(__half2 *const ptr, const __half2 value)
Generates a st.global.wt store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__host__ __device__ __half __uint2half_rd(const unsigned int i)
Convert an unsigned integer to a half in round-down mode.
Convert the unsigned integer value i to a half-precision floating-point value in round-down mode.

Parameters

i – [in] - unsigned int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __uint2half_rn(const unsigned int i)
Convert an unsigned integer to a half in round-to-nearest-even mode.
Convert the unsigned integer value i to a half-precision floating-point value in round-to-nearest-even mode.

Parameters

i – [in] - unsigned int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __uint2half_ru(const unsigned int i)
Convert an unsigned integer to a half in round-up mode.
Convert the unsigned integer value i to a half-precision floating-point value in round-up mode.

Parameters

i – [in] - unsigned int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __uint2half_rz(const unsigned int i)
Convert an unsigned integer to a half in round-towards-zero mode.
Convert the unsigned integer value i to a half-precision floating-point value in round-towards-zero mode.

Parameters

i – [in] - unsigned int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __ull2half_rd(const unsigned long long int i)
Convert an unsigned 64-bit integer to a half in round-down mode.
Convert the unsigned 64-bit integer value i to a half-precision floating-point value in round-down mode.

Parameters

i – [in] - unsigned long long int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __ull2half_rn(const unsigned long long int i)
Convert an unsigned 64-bit integer to a half in round-to-nearest-even mode.
Convert the unsigned 64-bit integer value i to a half-precision floating-point value in round-to-nearest-even mode.

Parameters

i – [in] - unsigned long long int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __ull2half_ru(const unsigned long long int i)
Convert an unsigned 64-bit integer to a half in round-up mode.
Convert the unsigned 64-bit integer value i to a half-precision floating-point value in round-up mode.

Parameters

i – [in] - unsigned long long int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __ull2half_rz(const unsigned long long int i)
Convert an unsigned 64-bit integer to a half in round-towards-zero mode.
Convert the unsigned 64-bit integer value i to a half-precision floating-point value in round-towards-zero mode.

Parameters

i – [in] - unsigned long long int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __ushort2half_rd(const unsigned short int i)
Convert an unsigned short integer to a half in round-down mode.
Convert the unsigned short integer value i to a half-precision floating-point value in round-down mode.

Parameters

i – [in] - unsigned short int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __ushort2half_rn(const unsigned short int i)
Convert an unsigned short integer to a half in round-to-nearest-even mode.
Convert the unsigned short integer value i to a half-precision floating-point value in round-to-nearest-even mode.

Parameters

i – [in] - unsigned short int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __ushort2half_ru(const unsigned short int i)
Convert an unsigned short integer to a half in round-up mode.
Convert the unsigned short integer value i to a half-precision floating-point value in round-up mode.

Parameters

i – [in] - unsigned short int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __ushort2half_rz(const unsigned short int i)
Convert an unsigned short integer to a half in round-towards-zero mode.
Convert the unsigned short integer value i to a half-precision floating-point value in round-towards-zero mode.

Parameters

i – [in] - unsigned short int. Is only being read.

Returns

half

i converted to half.


__host__ __device__ __half __ushort_as_half(const unsigned short int i)
Reinterprets bits in an unsigned short integer as a half.
Reinterprets the bits in the unsigned short integer i as a half-precision floating-point number.

Parameters

i – [in] - unsigned short int. Is only being read.

Returns

half

The reinterpreted value.


__host__ __device__ __half2 make_half2(const __half x, const __half y)
Vector function, combines two __half numbers into one __half2 number.
Combines two input __half number x and y into one __half2 number. Input x is stored in low 16 bits of the return value, input y is stored in high 16 bits of the return value.

Parameters

x – [in] - half. Is only being read.
y – [in] - half. Is only being read.

Returns

__half2

The __half2 vector with one half equal to x and the other to y.