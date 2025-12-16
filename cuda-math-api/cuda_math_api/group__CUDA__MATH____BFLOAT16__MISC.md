# 5.5. Bfloat16 Precision Conversion and Data Movement


To use these functions, include the header file `cuda_bf16.h` in your program.


Functions


__host__ __device__ float2 __bfloat1622float2(const __nv_bfloat162 a)
Converts both halves of nv_bfloat162 to float2 and returns the result.

__host__ __device__ __nv_bfloat162 __bfloat162bfloat162(const __nv_bfloat16 a)
Returns nv_bfloat162 with both halves equal to the input value.

__host__ __device__ signed char __bfloat162char_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed char in round-towards-zero mode.

__host__ __device__ float __bfloat162float(const __nv_bfloat16 a)
Converts nv_bfloat16 number to float.

__device__ int __bfloat162int_rd(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed integer in round-down mode.

__device__ int __bfloat162int_rn(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed integer in round-to-nearest-even mode.

__device__ int __bfloat162int_ru(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed integer in round-up mode.

__host__ __device__ int __bfloat162int_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed integer in round-towards-zero mode.

__device__ long long int __bfloat162ll_rd(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed 64-bit integer in round-down mode.

__device__ long long int __bfloat162ll_rn(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed 64-bit integer in round-to-nearest-even mode.

__device__ long long int __bfloat162ll_ru(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed 64-bit integer in round-up mode.

__host__ __device__ long long int __bfloat162ll_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed 64-bit integer in round-towards-zero mode.

__device__ short int __bfloat162short_rd(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed short integer in round-down mode.

__device__ short int __bfloat162short_rn(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed short integer in round-to-nearest-even mode.

__device__ short int __bfloat162short_ru(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed short integer in round-up mode.

__host__ __device__ short int __bfloat162short_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed short integer in round-towards-zero mode.

__host__ __device__ unsigned char __bfloat162uchar_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned char in round-towards-zero mode.

__device__ unsigned int __bfloat162uint_rd(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned integer in round-down mode.

__device__ unsigned int __bfloat162uint_rn(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned integer in round-to-nearest-even mode.

__device__ unsigned int __bfloat162uint_ru(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned integer in round-up mode.

__host__ __device__ unsigned int __bfloat162uint_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned integer in round-towards-zero mode.

__device__ unsigned long long int __bfloat162ull_rd(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned 64-bit integer in round-down mode.

__device__ unsigned long long int __bfloat162ull_rn(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned 64-bit integer in round-to-nearest-even mode.

__device__ unsigned long long int __bfloat162ull_ru(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned 64-bit integer in round-up mode.

__host__ __device__ unsigned long long int __bfloat162ull_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned 64-bit integer in round-towards-zero mode.

__device__ unsigned short int __bfloat162ushort_rd(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned short integer in round-down mode.

__device__ unsigned short int __bfloat162ushort_rn(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned short integer in round-to-nearest-even mode.

__device__ unsigned short int __bfloat162ushort_ru(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned short integer in round-up mode.

__host__ __device__ unsigned short int __bfloat162ushort_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned short integer in round-towards-zero mode.

__host__ __device__ short int __bfloat16_as_short(const __nv_bfloat16 h)
Reinterprets bits in a nv_bfloat16 as a signed short integer.

__host__ __device__ unsigned short int __bfloat16_as_ushort(const __nv_bfloat16 h)
Reinterprets bits in a nv_bfloat16 as an unsigned short integer.

__host__ __device__ __nv_bfloat16 __double2bfloat16(const double a)
Converts double number to nv_bfloat16 precision in round-to-nearest-even mode and returns nv_bfloat16 with converted value.

__host__ __device__ __nv_bfloat162 __float22bfloat162_rn(const float2 a)
Converts both components of float2 number to nv_bfloat16 precision in round-to-nearest-even mode and returns nv_bfloat162 with converted values.

__host__ __device__ __nv_bfloat16 __float2bfloat16(const float a)
Converts float number to nv_bfloat16 precision in round-to-nearest-even mode and returns nv_bfloat16 with converted value.

__host__ __device__ __nv_bfloat162 __float2bfloat162_rn(const float a)
Converts input to nv_bfloat16 precision in round-to-nearest-even mode and populates both halves of nv_bfloat162 with converted value.

__host__ __device__ __nv_bfloat16 __float2bfloat16_rd(const float a)
Converts float number to nv_bfloat16 precision in round-down mode and returns nv_bfloat16 with converted value.

__host__ __device__ __nv_bfloat16 __float2bfloat16_rn(const float a)
Converts float number to nv_bfloat16 precision in round-to-nearest-even mode and returns nv_bfloat16 with converted value.

__host__ __device__ __nv_bfloat16 __float2bfloat16_ru(const float a)
Converts float number to nv_bfloat16 precision in round-up mode and returns nv_bfloat16 with converted value.

__host__ __device__ __nv_bfloat16 __float2bfloat16_rz(const float a)
Converts float number to nv_bfloat16 precision in round-towards-zero mode and returns nv_bfloat16 with converted value.

__host__ __device__ __nv_bfloat162 __floats2bfloat162_rn(const float a, const float b)
Converts both input floats to nv_bfloat16 precision in round-to-nearest-even mode and returns nv_bfloat162 with converted values.

__host__ __device__ __nv_bfloat162 __halves2bfloat162(const __nv_bfloat16 a, const __nv_bfloat16 b)
Combines two nv_bfloat16 numbers into one nv_bfloat162 number.

__host__ __device__ __nv_bfloat16 __high2bfloat16(const __nv_bfloat162 a)
Returns high 16 bits of nv_bfloat162 input.

__host__ __device__ __nv_bfloat162 __high2bfloat162(const __nv_bfloat162 a)
Extracts high 16 bits from nv_bfloat162 input.

__host__ __device__ float __high2float(const __nv_bfloat162 a)
Converts high 16 bits of nv_bfloat162 to float and returns the result.

__host__ __device__ __nv_bfloat162 __highs2bfloat162(const __nv_bfloat162 a, const __nv_bfloat162 b)
Extracts high 16 bits from each of the two nv_bfloat162 inputs and combines into one nv_bfloat162 number.

__device__ __nv_bfloat16 __int2bfloat16_rd(const int i)
Convert a signed integer to a nv_bfloat16 in round-down mode.

__host__ __device__ __nv_bfloat16 __int2bfloat16_rn(const int i)
Convert a signed integer to a nv_bfloat16 in round-to-nearest-even mode.

__device__ __nv_bfloat16 __int2bfloat16_ru(const int i)
Convert a signed integer to a nv_bfloat16 in round-up mode.

__device__ __nv_bfloat16 __int2bfloat16_rz(const int i)
Convert a signed integer to a nv_bfloat16 in round-towards-zero mode.

__device__ __nv_bfloat162 __ldca(const __nv_bfloat162 *const ptr)
Generates a ld.global.ca load instruction.

__device__ __nv_bfloat16 __ldca(const __nv_bfloat16 *const ptr)
Generates a ld.global.ca load instruction.

__device__ __nv_bfloat16 __ldcg(const __nv_bfloat16 *const ptr)
Generates a ld.global.cg load instruction.

__device__ __nv_bfloat162 __ldcg(const __nv_bfloat162 *const ptr)
Generates a ld.global.cg load instruction.

__device__ __nv_bfloat162 __ldcs(const __nv_bfloat162 *const ptr)
Generates a ld.global.cs load instruction.

__device__ __nv_bfloat16 __ldcs(const __nv_bfloat16 *const ptr)
Generates a ld.global.cs load instruction.

__device__ __nv_bfloat16 __ldcv(const __nv_bfloat16 *const ptr)
Generates a ld.global.cv load instruction.

__device__ __nv_bfloat162 __ldcv(const __nv_bfloat162 *const ptr)
Generates a ld.global.cv load instruction.

__device__ __nv_bfloat162 __ldg(const __nv_bfloat162 *const ptr)
Generates a ld.global.nc load instruction.

__device__ __nv_bfloat16 __ldg(const __nv_bfloat16 *const ptr)
Generates a ld.global.nc load instruction.

__device__ __nv_bfloat162 __ldlu(const __nv_bfloat162 *const ptr)
Generates a ld.global.lu load instruction.

__device__ __nv_bfloat16 __ldlu(const __nv_bfloat16 *const ptr)
Generates a ld.global.lu load instruction.

__device__ __nv_bfloat16 __ll2bfloat16_rd(const long long int i)
Convert a signed 64-bit integer to a nv_bfloat16 in round-down mode.

__host__ __device__ __nv_bfloat16 __ll2bfloat16_rn(const long long int i)
Convert a signed 64-bit integer to a nv_bfloat16 in round-to-nearest-even mode.

__device__ __nv_bfloat16 __ll2bfloat16_ru(const long long int i)
Convert a signed 64-bit integer to a nv_bfloat16 in round-up mode.

__device__ __nv_bfloat16 __ll2bfloat16_rz(const long long int i)
Convert a signed 64-bit integer to a nv_bfloat16 in round-towards-zero mode.

__host__ __device__ __nv_bfloat16 __low2bfloat16(const __nv_bfloat162 a)
Returns low 16 bits of nv_bfloat162 input.

__host__ __device__ __nv_bfloat162 __low2bfloat162(const __nv_bfloat162 a)
Extracts low 16 bits from nv_bfloat162 input.

__host__ __device__ float __low2float(const __nv_bfloat162 a)
Converts low 16 bits of nv_bfloat162 to float and returns the result.

__host__ __device__ __nv_bfloat162 __lowhigh2highlow(const __nv_bfloat162 a)
Swaps both halves of the nv_bfloat162 input.

__host__ __device__ __nv_bfloat162 __lows2bfloat162(const __nv_bfloat162 a, const __nv_bfloat162 b)
Extracts low 16 bits from each of the two nv_bfloat162 inputs and combines into one nv_bfloat162 number.

__nv_bfloat162::__nv_bfloat162()=default
Constructor by default.

__host__ __device__ constexpr __nv_bfloat162::__nv_bfloat162(const __nv_bfloat16 &a, const __nv_bfloat16 &b)
Constructor from two __nv_bfloat16 variables.

__host__ __device__ __nv_bfloat162::__nv_bfloat162(__nv_bfloat162 &&src)
Move constructor, available for C++11 and later dialects.

__host__ __device__ __nv_bfloat162::__nv_bfloat162(const __nv_bfloat162_raw &h2r)
Constructor from __nv_bfloat162_raw .

__host__ __device__ __nv_bfloat162::__nv_bfloat162(const __nv_bfloat162 &src)
Copy constructor.

__host__ __device__ __nv_bfloat162::operator __nv_bfloat162_raw() const
Conversion operator to __nv_bfloat162_raw .

__host__ __device__ __nv_bfloat162 & __nv_bfloat162::operator=(const __nv_bfloat162 &src)
Copy assignment operator.

__host__ __device__ __nv_bfloat162 & __nv_bfloat162::operator=(const __nv_bfloat162_raw &h2r)
Assignment operator from __nv_bfloat162_raw .

__host__ __device__ __nv_bfloat162 & __nv_bfloat162::operator=(__nv_bfloat162 &&src)
Move assignment operator, available for C++11 and later dialects.

__host__ __device__ __nv_bfloat16::__nv_bfloat16(const double f)
Construct __nv_bfloat16 from double input using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16::__nv_bfloat16(const float f)
Construct __nv_bfloat16 from float input using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16::__nv_bfloat16(long long val)
Construct __nv_bfloat16 from long long input using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16::__nv_bfloat16(unsigned short val)
Construct __nv_bfloat16 from unsigned short integer input using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16::__nv_bfloat16(unsigned int val)
Construct __nv_bfloat16 from unsigned int input using default round-to-nearest-even rounding mode.

__nv_bfloat16::__nv_bfloat16()=default
Constructor by default.

__host__ __device__ __nv_bfloat16::__nv_bfloat16(const __half f)
Construct __nv_bfloat16 from __half input using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16::__nv_bfloat16(short val)
Construct __nv_bfloat16 from short integer input using default round-to-nearest-even rounding mode.

__host__ __device__ constexpr __nv_bfloat16::__nv_bfloat16(const __nv_bfloat16_raw &hr)
Constructor from __nv_bfloat16_raw .

__host__ __device__ __nv_bfloat16::__nv_bfloat16(unsigned long long val)
Construct __nv_bfloat16 from unsigned long long input using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16::__nv_bfloat16(int val)
Construct __nv_bfloat16 from int input using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16::__nv_bfloat16(const unsigned long val)
Construct __nv_bfloat16 from unsigned long input using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16::__nv_bfloat16(const long val)
Construct __nv_bfloat16 from long input using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16::operator __nv_bfloat16_raw() const
Type cast to __nv_bfloat16_raw operator.

__host__ __device__ __nv_bfloat16::operator __nv_bfloat16_raw() const volatile
Type cast to __nv_bfloat16_raw operator with volatile input.

__host__ __device__ constexpr __nv_bfloat16::operator bool() const
Conversion operator to bool data type.

__host__ __device__ __nv_bfloat16::operator char() const
Conversion operator to an implementation defined char data type.

__host__ __device__ __nv_bfloat16::operator float() const
Type cast to float operator.

__host__ __device__ __nv_bfloat16::operator int() const
Conversion operator to int data type.

__host__ __device__ __nv_bfloat16::operator long() const
Conversion operator to long data type.

__host__ __device__ __nv_bfloat16::operator long long() const
Conversion operator to long long data type.

__host__ __device__ __nv_bfloat16::operator short() const
Conversion operator to short data type.

__host__ __device__ __nv_bfloat16::operator signed char() const
Conversion operator to signed char data type.

__host__ __device__ __nv_bfloat16::operator unsigned char() const
Conversion operator to unsigned char data type.

__host__ __device__ __nv_bfloat16::operator unsigned int() const
Conversion operator to unsigned int data type.

__host__ __device__ __nv_bfloat16::operator unsigned long() const
Conversion operator to unsigned long data type.

__host__ __device__ __nv_bfloat16::operator unsigned long long() const
Conversion operator to unsigned long long data type.

__host__ __device__ __nv_bfloat16::operator unsigned short() const
Conversion operator to unsigned short data type.

__host__ __device__ __nv_bfloat16 & __nv_bfloat16::operator=(const __nv_bfloat16_raw &hr)
Assignment operator from __nv_bfloat16_raw .

__host__ __device__ __nv_bfloat16 & __nv_bfloat16::operator=(unsigned int val)
Type cast from unsigned int assignment operator, using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16 & __nv_bfloat16::operator=(int val)
Type cast from int assignment operator, using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16 & __nv_bfloat16::operator=(long long val)
Type cast from long long assignment operator, using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16 & __nv_bfloat16::operator=(unsigned long long val)
Type cast from unsigned long long assignment operator, using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16 & __nv_bfloat16::operator=(unsigned short val)
Type cast from unsigned short assignment operator, using default round-to-nearest-even rounding mode.

__host__ __device__ volatile __nv_bfloat16 & __nv_bfloat16::operator=(const __nv_bfloat16_raw &hr) volatile
Assignment operator from __nv_bfloat16_raw to volatile __nv_bfloat16 .

__host__ __device__ __nv_bfloat16 & __nv_bfloat16::operator=(const double f)
Type cast to __nv_bfloat16 assignment operator from double input using default round-to-nearest-even rounding mode.

__host__ __device__ __nv_bfloat16 & __nv_bfloat16::operator=(const float f)
Type cast to __nv_bfloat16 assignment operator from float input using default round-to-nearest-even rounding mode.

__host__ __device__ volatile __nv_bfloat16 & __nv_bfloat16::operator=(const volatile __nv_bfloat16_raw &hr) volatile
Assignment operator from volatile __nv_bfloat16_raw to volatile __nv_bfloat16 .

__host__ __device__ __nv_bfloat16 & __nv_bfloat16::operator=(short val)
Type cast from short assignment operator, using default round-to-nearest-even rounding mode.

__device__ __nv_bfloat162 __shfl_down_sync(const unsigned int mask, const __nv_bfloat162 var, const unsigned int delta, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __nv_bfloat16 __shfl_down_sync(const unsigned int mask, const __nv_bfloat16 var, const unsigned int delta, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __nv_bfloat162 __shfl_sync(const unsigned int mask, const __nv_bfloat162 var, const int srcLane, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __nv_bfloat16 __shfl_sync(const unsigned int mask, const __nv_bfloat16 var, const int srcLane, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __nv_bfloat16 __shfl_up_sync(const unsigned int mask, const __nv_bfloat16 var, const unsigned int delta, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __nv_bfloat162 __shfl_up_sync(const unsigned int mask, const __nv_bfloat162 var, const unsigned int delta, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __nv_bfloat16 __shfl_xor_sync(const unsigned int mask, const __nv_bfloat16 var, const int laneMask, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __nv_bfloat162 __shfl_xor_sync(const unsigned int mask, const __nv_bfloat162 var, const int laneMask, const int width=warpSize)
Exchange a variable between threads within a warp.

__device__ __nv_bfloat16 __short2bfloat16_rd(const short int i)
Convert a signed short integer to a nv_bfloat16 in round-down mode.

__host__ __device__ __nv_bfloat16 __short2bfloat16_rn(const short int i)
Convert a signed short integer to a nv_bfloat16 in round-to-nearest-even mode.

__device__ __nv_bfloat16 __short2bfloat16_ru(const short int i)
Convert a signed short integer to a nv_bfloat16 in round-up mode.

__device__ __nv_bfloat16 __short2bfloat16_rz(const short int i)
Convert a signed short integer to a nv_bfloat16 in round-towards-zero mode.

__host__ __device__ __nv_bfloat16 __short_as_bfloat16(const short int i)
Reinterprets bits in a signed short integer as a nv_bfloat16 .

__device__ void __stcg(__nv_bfloat16 *const ptr, const __nv_bfloat16 value)
Generates a st.global.cg store instruction.

__device__ void __stcg(__nv_bfloat162 *const ptr, const __nv_bfloat162 value)
Generates a st.global.cg store instruction.

__device__ void __stcs(__nv_bfloat16 *const ptr, const __nv_bfloat16 value)
Generates a st.global.cs store instruction.

__device__ void __stcs(__nv_bfloat162 *const ptr, const __nv_bfloat162 value)
Generates a st.global.cs store instruction.

__device__ void __stwb(__nv_bfloat16 *const ptr, const __nv_bfloat16 value)
Generates a st.global.wb store instruction.

__device__ void __stwb(__nv_bfloat162 *const ptr, const __nv_bfloat162 value)
Generates a st.global.wb store instruction.

__device__ void __stwt(__nv_bfloat162 *const ptr, const __nv_bfloat162 value)
Generates a st.global.wt store instruction.

__device__ void __stwt(__nv_bfloat16 *const ptr, const __nv_bfloat16 value)
Generates a st.global.wt store instruction.

__device__ __nv_bfloat16 __uint2bfloat16_rd(const unsigned int i)
Convert an unsigned integer to a nv_bfloat16 in round-down mode.

__host__ __device__ __nv_bfloat16 __uint2bfloat16_rn(const unsigned int i)
Convert an unsigned integer to a nv_bfloat16 in round-to-nearest-even mode.

__device__ __nv_bfloat16 __uint2bfloat16_ru(const unsigned int i)
Convert an unsigned integer to a nv_bfloat16 in round-up mode.

__device__ __nv_bfloat16 __uint2bfloat16_rz(const unsigned int i)
Convert an unsigned integer to a nv_bfloat16 in round-towards-zero mode.

__device__ __nv_bfloat16 __ull2bfloat16_rd(const unsigned long long int i)
Convert an unsigned 64-bit integer to a nv_bfloat16 in round-down mode.

__host__ __device__ __nv_bfloat16 __ull2bfloat16_rn(const unsigned long long int i)
Convert an unsigned 64-bit integer to a nv_bfloat16 in round-to-nearest-even mode.

__device__ __nv_bfloat16 __ull2bfloat16_ru(const unsigned long long int i)
Convert an unsigned 64-bit integer to a nv_bfloat16 in round-up mode.

__device__ __nv_bfloat16 __ull2bfloat16_rz(const unsigned long long int i)
Convert an unsigned 64-bit integer to a nv_bfloat16 in round-towards-zero mode.

__device__ __nv_bfloat16 __ushort2bfloat16_rd(const unsigned short int i)
Convert an unsigned short integer to a nv_bfloat16 in round-down mode.

__host__ __device__ __nv_bfloat16 __ushort2bfloat16_rn(const unsigned short int i)
Convert an unsigned short integer to a nv_bfloat16 in round-to-nearest-even mode.

__device__ __nv_bfloat16 __ushort2bfloat16_ru(const unsigned short int i)
Convert an unsigned short integer to a nv_bfloat16 in round-up mode.

__device__ __nv_bfloat16 __ushort2bfloat16_rz(const unsigned short int i)
Convert an unsigned short integer to a nv_bfloat16 in round-towards-zero mode.

__host__ __device__ __nv_bfloat16 __ushort_as_bfloat16(const unsigned short int i)
Reinterprets bits in an unsigned short integer as a nv_bfloat16 .

__host__ __device__ __nv_bfloat162 make_bfloat162(const __nv_bfloat16 x, const __nv_bfloat16 y)
Vector function, combines two nv_bfloat16 numbers into one nv_bfloat162 number.


## 5.5.1. Functions


__host__ __device__ float2 __bfloat1622float2(const __nv_bfloat162 a)
Converts both halves of nv_bfloat162 to float2 and returns the result.
Converts both halves of nv_bfloat162 input a to float and returns the result as a float2 packed value.

See also
__bfloat162float(__nv_bfloat16) for further details.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

float2

a converted to float2.


__host__ __device__ __nv_bfloat162 __bfloat162bfloat162(const __nv_bfloat16 a)
Returns nv_bfloat162 with both halves equal to the input value.
Returns nv_bfloat162 number with both halves equal to the input a nv_bfloat16 number.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat162

The vector which has both its halves equal to the input a.


__host__ __device__ signed char __bfloat162char_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed char in round-towards-zero mode.
Convert the nv_bfloat16 floating-point value h to a signed char in round-towards-zero mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

signed char

h converted to a signed char using round-towards-zero mode.
__bfloat162char_rz \( (\pm 0)\) returns 0.
__bfloat162char_rz \( (x), x > 127\) returns SCHAR_MAX = 0x7F.
__bfloat162char_rz \( (x), x < -128\) returns SCHAR_MIN = 0x80.
__bfloat162char_rz(NaN) returns 0.


__host__ __device__ float __bfloat162float(const __nv_bfloat16 a)
Converts nv_bfloat16 number to float.
Converts nv_bfloat16 number a to float.

Parameters

a – [in] - float. Is only being read.

Returns

float

a converted to float.
__bfloat162float \( (\pm 0)\) returns \( \pm 0 \).
__bfloat162float \( (\pm \infty)\) returns \( \pm \infty \).
__bfloat162float(NaN) returns NaN.


__device__ int __bfloat162int_rd(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed integer in round-down mode.
Convert the nv_bfloat16 floating-point value h to a signed integer in round-down mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

int

h converted to a signed integer using round-down mode.
__bfloat162int_rd \( (\pm 0)\) returns 0.
__bfloat162int_rd \( (x), x > INT_MAX\) returns INT_MAX = 0x7FFFFFFF.
__bfloat162int_rd \( (x), x < INT_MIN\) returns INT_MIN = 0x80000000.
__bfloat162int_rd(NaN) returns 0.*__device__ int __bfloat162int_rn(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed integer in round-to-nearest-even mode.
Convert the nv_bfloat16 floating-point value h to a signed integer in round-to-nearest-even mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

int

h converted to a signed integer using round-to-nearest-even mode.
__bfloat162int_rn \( (\pm 0)\) returns 0.
__bfloat162int_rn \( (x), x > INT_MAX\) returns INT_MAX = 0x7FFFFFFF.
__bfloat162int_rn \( (x), x < INT_MIN\) returns INT_MIN = 0x80000000.
__bfloat162int_rn(NaN) returns 0.


__device__ int __bfloat162int_ru(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed integer in round-up mode.
Convert the nv_bfloat16 floating-point value h to a signed integer in round-up mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

int

h converted to a signed integer using round-up mode.
__bfloat162int_ru \( (\pm 0)\) returns 0.
__bfloat162int_ru \( (x), x > INT_MAX\) returns INT_MAX = 0x7FFFFFFF.
__bfloat162int_ru \( (x), x < INT_MIN\) returns INT_MIN = 0x80000000.
__bfloat162int_ru(NaN) returns 0.


__host__ __device__ int __bfloat162int_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed integer in round-towards-zero mode.
Convert the nv_bfloat16 floating-point value h to a signed integer in round-towards-zero mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

int

h converted to a signed integer using round-towards-zero mode.
__bfloat162int_rz \( (\pm 0)\) returns 0.
__bfloat162int_rz \( (x), x > INT_MAX\) returns INT_MAX = 0x7FFFFFFF.
__bfloat162int_rz \( (x), x < INT_MIN\) returns INT_MIN = 0x80000000.
__bfloat162int_rz(NaN) returns 0.


__device__ long long int __bfloat162ll_rd(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed 64-bit integer in round-down mode.
Convert the nv_bfloat16 floating-point value h to a signed 64-bit integer in round-down mode. NaN inputs return a long long int with hex value of 0x8000000000000000.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

long long int

h converted to a signed 64-bit integer.


__device__ long long int __bfloat162ll_rn(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed 64-bit integer in round-to-nearest-even mode.
Convert the nv_bfloat16 floating-point value h to a signed 64-bit integer in round-to-nearest-even mode. NaN inputs return a long long int with hex value of 0x8000000000000000.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

long long int

h converted to a signed 64-bit integer.


__device__ long long int __bfloat162ll_ru(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed 64-bit integer in round-up mode.
Convert the nv_bfloat16 floating-point value h to a signed 64-bit integer in round-up mode. NaN inputs return a long long int with hex value of 0x8000000000000000.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

long long int

h converted to a signed 64-bit integer.


__host__ __device__ long long int __bfloat162ll_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed 64-bit integer in round-towards-zero mode.
Convert the nv_bfloat16 floating-point value h to a signed 64-bit integer in round-towards-zero mode. NaN inputs return a long long int with hex value of 0x8000000000000000.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

long long int

h converted to a signed 64-bit integer.


__device__ short int __bfloat162short_rd(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed short integer in round-down mode.
Convert the nv_bfloat16 floating-point value h to a signed short integer in round-down mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

short int

h converted to a signed short integer using round-down mode.
__bfloat162short_rd \( (\pm 0)\) returns 0.
__bfloat162short_rd \( (x), x > 32767\) returns SHRT_MAX = 0x7FFF.
__bfloat162short_rd \( (x), x < -32768\) returns SHRT_MIN = 0x8000.
__bfloat162short_rd(NaN) returns 0.


__device__ short int __bfloat162short_rn(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed short integer in round-to-nearest-even mode.
Convert the nv_bfloat16 floating-point value h to a signed short integer in round-to-nearest-even mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

short int

h converted to a signed short integer using round-to-nearest-even mode.
__bfloat162short_rn \( (\pm 0)\) returns 0.
__bfloat162short_rn \( (x), x > 32767\) returns SHRT_MAX = 0x7FFF.
__bfloat162short_rn \( (x), x < -32768\) returns SHRT_MIN = 0x8000.
__bfloat162short_rn(NaN) returns 0.


__device__ short int __bfloat162short_ru(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed short integer in round-up mode.
Convert the nv_bfloat16 floating-point value h to a signed short integer in round-up mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

short int

h converted to a signed short integer using round-up mode.
__bfloat162short_ru \( (\pm 0)\) returns 0.
__bfloat162short_ru \( (x), x > 32767\) returns SHRT_MAX = 0x7FFF.
__bfloat162short_ru \( (x), x < -32768\) returns SHRT_MIN = 0x8000.
__bfloat162short_ru(NaN) returns 0.


__host__ __device__ short int __bfloat162short_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to a signed short integer in round-towards-zero mode.
Convert the nv_bfloat16 floating-point value h to a signed short integer in round-towards-zero mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

short int

h converted to a signed short integer using round-towards-zero mode.
__bfloat162short_rz \( (\pm 0)\) returns 0.
__bfloat162short_rz \( (x), x > 32767\) returns SHRT_MAX = 0x7FFF.
__bfloat162short_rz \( (x), x < -32768\) returns SHRT_MIN = 0x8000.
__bfloat162short_rz(NaN) returns 0.


__host__ __device__ unsigned char __bfloat162uchar_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned char in round-towards-zero mode.
Convert the nv_bfloat16 floating-point value h to an unsigned char in round-towards-zero mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned char

h converted to an unsigned char using round-towards-zero mode.
__bfloat162uchar_rz \( (\pm 0)\) returns 0.
__bfloat162uchar_rz \( (x), x > 255\) returns UCHAR_MAX = 0xFF.
__bfloat162uchar_rz \( (x), x < 0.0\) returns 0.
__bfloat162uchar_rz(NaN) returns 0.


__device__ unsigned int __bfloat162uint_rd(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned integer in round-down mode.
Convert the nv_bfloat16 floating-point value h to an unsigned integer in round-down mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned int

h converted to an unsigned integer.


__device__ unsigned int __bfloat162uint_rn(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned integer in round-to-nearest-even mode.
Convert the nv_bfloat16 floating-point value h to an unsigned integer in round-to-nearest-even mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned int

h converted to an unsigned integer.


__device__ unsigned int __bfloat162uint_ru(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned integer in round-up mode.
Convert the nv_bfloat16 floating-point value h to an unsigned integer in round-up mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned int

h converted to an unsigned integer.


__host__ __device__ unsigned int __bfloat162uint_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned integer in round-towards-zero mode.
Convert the nv_bfloat16 floating-point value h to an unsigned integer in round-towards-zero mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned int

h converted to an unsigned integer.


__device__ unsigned long long int __bfloat162ull_rd(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned 64-bit integer in round-down mode.
Convert the nv_bfloat16 floating-point value h to an unsigned 64-bit integer in round-down mode. NaN inputs return 0x8000000000000000.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned long long int

h converted to an unsigned 64-bit integer.


__device__ unsigned long long int __bfloat162ull_rn(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned 64-bit integer in round-to-nearest-even mode.
Convert the nv_bfloat16 floating-point value h to an unsigned 64-bit integer in round-to-nearest-even mode. NaN inputs return 0x8000000000000000.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned long long int

h converted to an unsigned 64-bit integer.


__device__ unsigned long long int __bfloat162ull_ru(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned 64-bit integer in round-up mode.
Convert the nv_bfloat16 floating-point value h to an unsigned 64-bit integer in round-up mode. NaN inputs return 0x8000000000000000.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned long long int

h converted to an unsigned 64-bit integer.


__host__ __device__ unsigned long long int __bfloat162ull_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned 64-bit integer in round-towards-zero mode.
Convert the nv_bfloat16 floating-point value h to an unsigned 64-bit integer in round-towards-zero mode. NaN inputs return 0x8000000000000000.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned long long int

h converted to an unsigned 64-bit integer.


__device__ unsigned short int __bfloat162ushort_rd(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned short integer in round-down mode.
Convert the nv_bfloat16 floating-point value h to an unsigned short integer in round-down mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned short int

h converted to an unsigned short integer.


__device__ unsigned short int __bfloat162ushort_rn(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned short integer in round-to-nearest-even mode.
Convert the nv_bfloat16 floating-point value h to an unsigned short integer in round-to-nearest-even mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned short int

h converted to an unsigned short integer.


__device__ unsigned short int __bfloat162ushort_ru(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned short integer in round-up mode.
Convert the nv_bfloat16 floating-point value h to an unsigned short integer in round-up mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned short int

h converted to an unsigned short integer.


__host__ __device__ unsigned short int __bfloat162ushort_rz(const __nv_bfloat16 h)
Convert a nv_bfloat16 to an unsigned short integer in round-towards-zero mode.
Convert the nv_bfloat16 floating-point value h to an unsigned short integer in round-towards-zero mode. NaN inputs are converted to 0.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned short int

h converted to an unsigned short integer.


__host__ __device__ short int __bfloat16_as_short(const __nv_bfloat16 h)
Reinterprets bits in a nv_bfloat16 as a signed short integer.
Reinterprets the bits in the nv_bfloat16 floating-point number h as a signed short integer.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

short int

The reinterpreted value.


__host__ __device__ unsigned short int __bfloat16_as_ushort(const __nv_bfloat16 h)
Reinterprets bits in a nv_bfloat16 as an unsigned short integer.
Reinterprets the bits in the nv_bfloat16 floating-point h as an unsigned short number.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

unsigned short int

The reinterpreted value.


__host__ __device__ __nv_bfloat16 __double2bfloat16(const double a)
Converts double number to nv_bfloat16 precision in round-to-nearest-even mode and returns nv_bfloat16 with converted value.
Converts double number a to nv_bfloat16 precision in round-to-nearest-even mode.

Parameters

a – [in] - double. Is only being read.

Returns

nv_bfloat16

a converted to nv_bfloat16 using round-to-nearest-even mode.
__double2bfloat16 \( (\pm 0)\) returns \( \pm 0 \).
__double2bfloat16 \( (\pm \infty)\) returns \( \pm \infty \).
__double2bfloat16(NaN) returns NaN.


__host__ __device__ __nv_bfloat162 __float22bfloat162_rn(const float2 a)
Converts both components of float2 number to nv_bfloat16 precision in round-to-nearest-even mode and returns nv_bfloat162 with converted values.
Converts both components of float2 to nv_bfloat16 precision in round-to-nearest-even mode and combines the results into one nv_bfloat162 number. Low 16 bits of the return value correspond to a.x and high 16 bits of the return value correspond to a.y.

See also
__float2bfloat16_rn(float) for further details.

Parameters

a – [in] - float2. Is only being read.

Returns

nv_bfloat162

The nv_bfloat162 which has corresponding halves equal to the converted float2 components.


__host__ __device__ __nv_bfloat16 __float2bfloat16(const float a)
Converts float number to nv_bfloat16 precision in round-to-nearest-even mode and returns nv_bfloat16 with converted value.
Converts float number a to nv_bfloat16 precision in round-to-nearest-even mode.

See also
__float2bfloat16_rn(float) for further details.

Parameters

a – [in] - float. Is only being read.

Returns

nv_bfloat16

a converted to nv_bfloat16 using round-to-nearest-even mode.


__host__ __device__ __nv_bfloat162 __float2bfloat162_rn(const float a)
Converts input to nv_bfloat16 precision in round-to-nearest-even mode and populates both halves of nv_bfloat162 with converted value.
Converts input a to nv_bfloat16 precision in round-to-nearest-even mode and populates both halves of nv_bfloat162 with converted value.

See also
__float2bfloat16_rn(float) for further details.

Parameters

a – [in] - float. Is only being read.

Returns

nv_bfloat162

The nv_bfloat162 value with both halves equal to the converted nv_bfloat16 precision number.


__host__ __device__ __nv_bfloat16 __float2bfloat16_rd(const float a)
Converts float number to nv_bfloat16 precision in round-down mode and returns nv_bfloat16 with converted value.
Converts float number a to nv_bfloat16 precision in round-down mode.

Parameters

a – [in] - float. Is only being read.

Returns

nv_bfloat16

a converted to nv_bfloat16 using round-down mode.
__float2bfloat16_rd \( (\pm 0)\) returns \( \pm 0 \).
__float2bfloat16_rd \( (\pm \infty)\) returns \( \pm \infty \).
__float2bfloat16_rd(NaN) returns NaN.


__host__ __device__ __nv_bfloat16 __float2bfloat16_rn(const float a)
Converts float number to nv_bfloat16 precision in round-to-nearest-even mode and returns nv_bfloat16 with converted value.
Converts float number a to nv_bfloat16 precision in round-to-nearest-even mode.

Parameters

a – [in] - float. Is only being read.

Returns

nv_bfloat16

a converted to nv_bfloat16 using round-to-nearest-even mode.
__float2bfloat16_rn \( (\pm 0)\) returns \( \pm 0 \).
__float2bfloat16_rn \( (\pm \infty)\) returns \( \pm \infty \).
__float2bfloat16_rn(NaN) returns NaN.


__host__ __device__ __nv_bfloat16 __float2bfloat16_ru(const float a)
Converts float number to nv_bfloat16 precision in round-up mode and returns nv_bfloat16 with converted value.
Converts float number a to nv_bfloat16 precision in round-up mode.

Parameters

a – [in] - float. Is only being read.

Returns

nv_bfloat16

a converted to nv_bfloat16 using round-up mode.
__float2bfloat16_ru \( (\pm 0)\) returns \( \pm 0 \).
__float2bfloat16_ru \( (\pm \infty)\) returns \( \pm \infty \).
__float2bfloat16_ru(NaN) returns NaN.


__host__ __device__ __nv_bfloat16 __float2bfloat16_rz(const float a)
Converts float number to nv_bfloat16 precision in round-towards-zero mode and returns nv_bfloat16 with converted value.
Converts float number a to nv_bfloat16 precision in round-towards-zero mode.

Parameters

a – [in] - float. Is only being read.

Returns

nv_bfloat16

a converted to nv_bfloat16 using round-towards-zero mode.
__float2bfloat16_rz \( (\pm 0)\) returns \( \pm 0 \).
__float2bfloat16_rz \( (\pm \infty)\) returns \( \pm \infty \).
__float2bfloat16_rz(NaN) returns NaN.


__host__ __device__ __nv_bfloat162 __floats2bfloat162_rn(const float a, const float b)
Converts both input floats to nv_bfloat16 precision in round-to-nearest-even mode and returns nv_bfloat162 with converted values.
Converts both input floats to nv_bfloat16 precision in round-to-nearest-even mode and combines the results into one nv_bfloat162 number. Low 16 bits of the return value correspond to the input a, high 16 bits correspond to the input b.

See also
__float2bfloat16_rn(float) for further details.

Parameters

a – [in] - float. Is only being read.
b – [in] - float. Is only being read.

Returns

nv_bfloat162

The nv_bfloat162 value with corresponding halves equal to the converted input floats.


__host__ __device__ __nv_bfloat162 __halves2bfloat162(const __nv_bfloat16 a, const __nv_bfloat16 b)
Combines two nv_bfloat16 numbers into one nv_bfloat162 number.
Combines two input nv_bfloat16 number a and b into one nv_bfloat162 number. Input a is stored in low 16 bits of the return value, input b is stored in high 16 bits of the return value.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat162

The nv_bfloat162 with one nv_bfloat16 equal to a and the other to b.


__host__ __device__ __nv_bfloat16 __high2bfloat16(const __nv_bfloat162 a)
Returns high 16 bits of nv_bfloat162 input.
Returns high 16 bits of nv_bfloat162 input a.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat16

The high 16 bits of the input.


__host__ __device__ __nv_bfloat162 __high2bfloat162(const __nv_bfloat162 a)
Extracts high 16 bits from nv_bfloat162 input.
Extracts high 16 bits from nv_bfloat162 input a and returns a new nv_bfloat162 number which has both halves equal to the extracted bits.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The nv_bfloat162 with both halves equal to the high 16 bits of the input.


__host__ __device__ float __high2float(const __nv_bfloat162 a)
Converts high 16 bits of nv_bfloat162 to float and returns the result.
Converts high 16 bits of nv_bfloat162 input a to 32-bit floating-point number and returns the result.

See also
__bfloat162float(__nv_bfloat16) for further details.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

float

The high 16 bits of a converted to float.


__host__ __device__ __nv_bfloat162 __highs2bfloat162(const __nv_bfloat162 a, const __nv_bfloat162 b)
Extracts high 16 bits from each of the two nv_bfloat162 inputs and combines into one nv_bfloat162 number.
Extracts high 16 bits from each of the two nv_bfloat162 inputs and combines into one nv_bfloat162 number. High 16 bits from input a is stored in low 16 bits of the return value, high 16 bits from input b is stored in high 16 bits of the return value.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The high 16 bits of a and of b.


__device__ __nv_bfloat16 __int2bfloat16_rd(const int i)
Convert a signed integer to a nv_bfloat16 in round-down mode.
Convert the signed integer value i to a nv_bfloat16 floating-point value in round-down mode.

Parameters

i – [in] - int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__host__ __device__ __nv_bfloat16 __int2bfloat16_rn(const int i)
Convert a signed integer to a nv_bfloat16 in round-to-nearest-even mode.
Convert the signed integer value i to a nv_bfloat16 floating-point value in round-to-nearest-even mode.

Parameters

i – [in] - int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __int2bfloat16_ru(const int i)
Convert a signed integer to a nv_bfloat16 in round-up mode.
Convert the signed integer value i to a nv_bfloat16 floating-point value in round-up mode.

Parameters

i – [in] - int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __int2bfloat16_rz(const int i)
Convert a signed integer to a nv_bfloat16 in round-towards-zero mode.
Convert the signed integer value i to a nv_bfloat16 floating-point value in round-towards-zero mode.

Parameters

i – [in] - int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat162 __ldca(const __nv_bfloat162 *const ptr)
Generates a ld.global.ca load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __nv_bfloat16 __ldca(const __nv_bfloat16 *const ptr)
Generates a ld.global.ca load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __nv_bfloat16 __ldcg(const __nv_bfloat16 *const ptr)
Generates a ld.global.cg load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __nv_bfloat162 __ldcg(const __nv_bfloat162 *const ptr)
Generates a ld.global.cg load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __nv_bfloat162 __ldcs(const __nv_bfloat162 *const ptr)
Generates a ld.global.cs load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __nv_bfloat16 __ldcs(const __nv_bfloat16 *const ptr)
Generates a ld.global.cs load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __nv_bfloat16 __ldcv(const __nv_bfloat16 *const ptr)
Generates a ld.global.cv load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __nv_bfloat162 __ldcv(const __nv_bfloat162 *const ptr)
Generates a ld.global.cv load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __nv_bfloat162 __ldg(const __nv_bfloat162 *const ptr)
Generates a ld.global.nc load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __nv_bfloat16 __ldg(const __nv_bfloat16 *const ptr)
Generates a ld.global.nc load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __nv_bfloat162 __ldlu(const __nv_bfloat162 *const ptr)
Generates a ld.global.lu load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __nv_bfloat16 __ldlu(const __nv_bfloat16 *const ptr)
Generates a ld.global.lu load instruction.

Parameters

ptr – [in] - memory location

Returns

The value pointed by ptr


__device__ __nv_bfloat16 __ll2bfloat16_rd(const long long int i)
Convert a signed 64-bit integer to a nv_bfloat16 in round-down mode.
Convert the signed 64-bit integer value i to a nv_bfloat16 floating-point value in round-down mode.

Parameters

i – [in] - long long int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__host__ __device__ __nv_bfloat16 __ll2bfloat16_rn(const long long int i)
Convert a signed 64-bit integer to a nv_bfloat16 in round-to-nearest-even mode.
Convert the signed 64-bit integer value i to a nv_bfloat16 floating-point value in round-to-nearest-even mode.

Parameters

i – [in] - long long int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __ll2bfloat16_ru(const long long int i)
Convert a signed 64-bit integer to a nv_bfloat16 in round-up mode.
Convert the signed 64-bit integer value i to a nv_bfloat16 floating-point value in round-up mode.

Parameters

i – [in] - long long int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __ll2bfloat16_rz(const long long int i)
Convert a signed 64-bit integer to a nv_bfloat16 in round-towards-zero mode.
Convert the signed 64-bit integer value i to a nv_bfloat16 floating-point value in round-towards-zero mode.

Parameters

i – [in] - long long int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__host__ __device__ __nv_bfloat16 __low2bfloat16(const __nv_bfloat162 a)
Returns low 16 bits of nv_bfloat162 input.
Returns low 16 bits of nv_bfloat162 input a.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat16

Returns nv_bfloat16 which contains low 16 bits of the input a.


__host__ __device__ __nv_bfloat162 __low2bfloat162(const __nv_bfloat162 a)
Extracts low 16 bits from nv_bfloat162 input.
Extracts low 16 bits from nv_bfloat162 input a and returns a new nv_bfloat162 number which has both halves equal to the extracted bits.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The nv_bfloat162 with both halves equal to the low 16 bits of the input.


__host__ __device__ float __low2float(const __nv_bfloat162 a)
Converts low 16 bits of nv_bfloat162 to float and returns the result.
Converts low 16 bits of nv_bfloat162 input a to 32-bit floating-point number and returns the result.

See also
__bfloat162float(__nv_bfloat16) for further details.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

float

The low 16 bits of a converted to float.


__host__ __device__ __nv_bfloat162 __lowhigh2highlow(const __nv_bfloat162 a)
Swaps both halves of the nv_bfloat162 input.
Swaps both halves of the nv_bfloat162 input and returns a new nv_bfloat162 number with swapped halves.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

a with its halves being swapped.


__host__ __device__ __nv_bfloat162 __lows2bfloat162(const __nv_bfloat162 a, const __nv_bfloat162 b)
Extracts low 16 bits from each of the two nv_bfloat162 inputs and combines into one nv_bfloat162 number.
Extracts low 16 bits from each of the two nv_bfloat162 inputs and combines into one nv_bfloat162 number. Low 16 bits from input a is stored in low 16 bits of the return value, low 16 bits from input b is stored in high 16 bits of the return value.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The low 16 bits of a and of b.


__device__ __nv_bfloat162 __shfl_down_sync(const unsigned int mask, const __nv_bfloat162 var, const unsigned int delta, const int width = warpSize)
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

var – [in] - nv_bfloat162. Is only being read.
delta – [in] - unsigned int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 4-byte word referenced by var from the source thread ID as nv_bfloat162.


__device__ __nv_bfloat16 __shfl_down_sync(const unsigned int mask, const __nv_bfloat16 var, const unsigned int delta, const int width = warpSize)
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

var – [in] - nv_bfloat16. Is only being read.
delta – [in] - unsigned int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 2-byte word referenced by var from the source thread ID as nv_bfloat16.


__device__ __nv_bfloat162 __shfl_sync(const unsigned int mask, const __nv_bfloat162 var, const int srcLane, const int width = warpSize)
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

var – [in] - nv_bfloat162. Is only being read.
srcLane – [in] - int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 4-byte word referenced by var from the source thread ID as nv_bfloat162.


__device__ __nv_bfloat16 __shfl_sync(const unsigned int mask, const __nv_bfloat16 var, const int srcLane, const int width = warpSize)
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

var – [in] - nv_bfloat16. Is only being read.
srcLane – [in] - int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 2-byte word referenced by var from the source thread ID as nv_bfloat16.


__device__ __nv_bfloat16 __shfl_up_sync(const unsigned int mask, const __nv_bfloat16 var, const unsigned int delta, const int width = warpSize)
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

var – [in] - nv_bfloat16. Is only being read.
delta – [in] - unsigned int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 2-byte word referenced by var from the source thread ID as nv_bfloat16.


__device__ __nv_bfloat162 __shfl_up_sync(const unsigned int mask, const __nv_bfloat162 var, const unsigned int delta, const int width = warpSize)
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

var – [in] - nv_bfloat162. Is only being read.
delta – [in] - unsigned int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 4-byte word referenced by var from the source thread ID as nv_bfloat162.


__device__ __nv_bfloat16 __shfl_xor_sync(const unsigned int mask, const __nv_bfloat16 var, const int laneMask, const int width = warpSize)
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

var – [in] - nv_bfloat16. Is only being read.
laneMask – [in] - int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 2-byte word referenced by var from the source thread ID as nv_bfloat16.


__device__ __nv_bfloat162 __shfl_xor_sync(const unsigned int mask, const __nv_bfloat162 var, const int laneMask, const int width = warpSize)
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

var – [in] - nv_bfloat162. Is only being read.
laneMask – [in] - int. Is only being read.
width – [in] - int. Is only being read.

Returns

Returns the 4-byte word referenced by var from the source thread ID as nv_bfloat162.


__device__ __nv_bfloat16 __short2bfloat16_rd(const short int i)
Convert a signed short integer to a nv_bfloat16 in round-down mode.
Convert the signed short integer value i to a nv_bfloat16 floating-point value in round-down mode.

Parameters

i – [in] - short int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__host__ __device__ __nv_bfloat16 __short2bfloat16_rn(const short int i)
Convert a signed short integer to a nv_bfloat16 in round-to-nearest-even mode.
Convert the signed short integer value i to a nv_bfloat16 floating-point value in round-to-nearest-even mode.

Parameters

i – [in] - short int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __short2bfloat16_ru(const short int i)
Convert a signed short integer to a nv_bfloat16 in round-up mode.
Convert the signed short integer value i to a nv_bfloat16 floating-point value in round-up mode.

Parameters

i – [in] - short int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __short2bfloat16_rz(const short int i)
Convert a signed short integer to a nv_bfloat16 in round-towards-zero mode.
Convert the signed short integer value i to a nv_bfloat16 floating-point value in round-towards-zero mode.

Parameters

i – [in] - short int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__host__ __device__ __nv_bfloat16 __short_as_bfloat16(const short int i)
Reinterprets bits in a signed short integer as a nv_bfloat16.
Reinterprets the bits in the signed short integer i as a nv_bfloat16 floating-point number.

Parameters

i – [in] - short int. Is only being read.

Returns

nv_bfloat16

The reinterpreted value.


__device__ void __stcg(__nv_bfloat16 *const ptr, const __nv_bfloat16 value)
Generates a st.global.cg store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stcg(__nv_bfloat162 *const ptr, const __nv_bfloat162 value)
Generates a st.global.cg store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stcs(__nv_bfloat16 *const ptr, const __nv_bfloat16 value)
Generates a st.global.cs store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stcs(__nv_bfloat162 *const ptr, const __nv_bfloat162 value)
Generates a st.global.cs store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stwb(__nv_bfloat16 *const ptr, const __nv_bfloat16 value)
Generates a st.global.wb store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stwb(__nv_bfloat162 *const ptr, const __nv_bfloat162 value)
Generates a st.global.wb store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stwt(__nv_bfloat162 *const ptr, const __nv_bfloat162 value)
Generates a st.global.wt store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ void __stwt(__nv_bfloat16 *const ptr, const __nv_bfloat16 value)
Generates a st.global.wt store instruction.

Parameters

ptr – [out] - memory location
value – [in] - the value to be stored


__device__ __nv_bfloat16 __uint2bfloat16_rd(const unsigned int i)
Convert an unsigned integer to a nv_bfloat16 in round-down mode.
Convert the unsigned integer value i to a nv_bfloat16 floating-point value in round-down mode.

Parameters

i – [in] - unsigned int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__host__ __device__ __nv_bfloat16 __uint2bfloat16_rn(const unsigned int i)
Convert an unsigned integer to a nv_bfloat16 in round-to-nearest-even mode.
Convert the unsigned integer value i to a nv_bfloat16 floating-point value in round-to-nearest-even mode.

Parameters

i – [in] - unsigned int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __uint2bfloat16_ru(const unsigned int i)
Convert an unsigned integer to a nv_bfloat16 in round-up mode.
Convert the unsigned integer value i to a nv_bfloat16 floating-point value in round-up mode.

Parameters

i – [in] - unsigned int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __uint2bfloat16_rz(const unsigned int i)
Convert an unsigned integer to a nv_bfloat16 in round-towards-zero mode.
Convert the unsigned integer value i to a nv_bfloat16 floating-point value in round-towards-zero mode.

Parameters

i – [in] - unsigned int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __ull2bfloat16_rd(const unsigned long long int i)
Convert an unsigned 64-bit integer to a nv_bfloat16 in round-down mode.
Convert the unsigned 64-bit integer value i to a nv_bfloat16 floating-point value in round-down mode.

Parameters

i – [in] - unsigned long long int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__host__ __device__ __nv_bfloat16 __ull2bfloat16_rn(const unsigned long long int i)
Convert an unsigned 64-bit integer to a nv_bfloat16 in round-to-nearest-even mode.
Convert the unsigned 64-bit integer value i to a nv_bfloat16 floating-point value in round-to-nearest-even mode.

Parameters

i – [in] - unsigned long long int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __ull2bfloat16_ru(const unsigned long long int i)
Convert an unsigned 64-bit integer to a nv_bfloat16 in round-up mode.
Convert the unsigned 64-bit integer value i to a nv_bfloat16 floating-point value in round-up mode.

Parameters

i – [in] - unsigned long long int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __ull2bfloat16_rz(const unsigned long long int i)
Convert an unsigned 64-bit integer to a nv_bfloat16 in round-towards-zero mode.
Convert the unsigned 64-bit integer value i to a nv_bfloat16 floating-point value in round-towards-zero mode.

Parameters

i – [in] - unsigned long long int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __ushort2bfloat16_rd(const unsigned short int i)
Convert an unsigned short integer to a nv_bfloat16 in round-down mode.
Convert the unsigned short integer value i to a nv_bfloat16 floating-point value in round-down mode.

Parameters

i – [in] - unsigned short int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__host__ __device__ __nv_bfloat16 __ushort2bfloat16_rn(const unsigned short int i)
Convert an unsigned short integer to a nv_bfloat16 in round-to-nearest-even mode.
Convert the unsigned short integer value i to a nv_bfloat16 floating-point value in round-to-nearest-even mode.

Parameters

i – [in] - unsigned short int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __ushort2bfloat16_ru(const unsigned short int i)
Convert an unsigned short integer to a nv_bfloat16 in round-up mode.
Convert the unsigned short integer value i to a nv_bfloat16 floating-point value in round-up mode.

Parameters

i – [in] - unsigned short int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__device__ __nv_bfloat16 __ushort2bfloat16_rz(const unsigned short int i)
Convert an unsigned short integer to a nv_bfloat16 in round-towards-zero mode.
Convert the unsigned short integer value i to a nv_bfloat16 floating-point value in round-towards-zero mode.

Parameters

i – [in] - unsigned short int. Is only being read.

Returns

nv_bfloat16

i converted to nv_bfloat16.


__host__ __device__ __nv_bfloat16 __ushort_as_bfloat16(const unsigned short int i)
Reinterprets bits in an unsigned short integer as a nv_bfloat16.
Reinterprets the bits in the unsigned short integer i as a nv_bfloat16 floating-point number.

Parameters

i – [in] - unsigned short int. Is only being read.

Returns

nv_bfloat16

The reinterpreted value.


__host__ __device__ __nv_bfloat162 make_bfloat162(const __nv_bfloat16 x, const __nv_bfloat16 y)
Vector function, combines two nv_bfloat16 numbers into one nv_bfloat162 number.
Combines two input nv_bfloat16 number x and y into one nv_bfloat162 number. Input x is stored in low 16 bits of the return value, input y is stored in high 16 bits of the return value.

Parameters

x – [in] - nv_bfloat16. Is only being read.
y – [in] - nv_bfloat16. Is only being read.

Returns

__nv_bfloat162

The __nv_bfloat162 vector with one half equal to x and the other to y.