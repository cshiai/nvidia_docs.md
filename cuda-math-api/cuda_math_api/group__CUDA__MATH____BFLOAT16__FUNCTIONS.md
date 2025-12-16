# 5.4. Bfloat16 Math Functions


To use these functions, include the header file `cuda_bf16.h` in your program.


Functions


__device__ __nv_bfloat16 hceil(const __nv_bfloat16 h)
Calculate ceiling of the input argument.

__device__ __nv_bfloat16 hcos(const __nv_bfloat16 a)
Calculates nv_bfloat16 cosine in round-to-nearest-even mode.

__device__ __nv_bfloat16 hexp(const __nv_bfloat16 a)
Calculates nv_bfloat16 natural exponential function in round-to-nearest-even mode.

__device__ __nv_bfloat16 hexp10(const __nv_bfloat16 a)
Calculates nv_bfloat16 decimal exponential function in round-to-nearest-even mode.

__device__ __nv_bfloat16 hexp2(const __nv_bfloat16 a)
Calculates nv_bfloat16 binary exponential function in round-to-nearest-even mode.

__device__ __nv_bfloat16 hfloor(const __nv_bfloat16 h)
Calculate the largest integer less than or equal to h .

__device__ __nv_bfloat16 hlog(const __nv_bfloat16 a)
Calculates nv_bfloat16 natural logarithm in round-to-nearest-even mode.

__device__ __nv_bfloat16 hlog10(const __nv_bfloat16 a)
Calculates nv_bfloat16 decimal logarithm in round-to-nearest-even mode.

__device__ __nv_bfloat16 hlog2(const __nv_bfloat16 a)
Calculates nv_bfloat16 binary logarithm in round-to-nearest-even mode.

__device__ __nv_bfloat16 hrcp(const __nv_bfloat16 a)
Calculates nv_bfloat16 reciprocal in round-to-nearest-even mode.

__device__ __nv_bfloat16 hrint(const __nv_bfloat16 h)
Round input to nearest integer value in nv_bfloat16 floating-point number.

__device__ __nv_bfloat16 hrsqrt(const __nv_bfloat16 a)
Calculates nv_bfloat16 reciprocal square root in round-to-nearest-even mode.

__device__ __nv_bfloat16 hsin(const __nv_bfloat16 a)
Calculates nv_bfloat16 sine in round-to-nearest-even mode.

__device__ __nv_bfloat16 hsqrt(const __nv_bfloat16 a)
Calculates nv_bfloat16 square root in round-to-nearest-even mode.

__device__ __nv_bfloat16 htanh(const __nv_bfloat16 a)
Calculates nv_bfloat16 hyperbolic tangent function in round-to-nearest-even mode.

__device__ __nv_bfloat16 htanh_approx(const __nv_bfloat16 a)
Calculates approximate nv_bfloat16 hyperbolic tangent function.

__device__ __nv_bfloat16 htrunc(const __nv_bfloat16 h)
Truncate input argument to the integral part.


## 5.4.1. Functions


__device__ __nv_bfloat16 hceil(const __nv_bfloat16 h)
Calculate ceiling of the input argument.
Compute the smallest integer value not less than h.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The smallest integer value not less than h.


__device__ __nv_bfloat16 hcos(const __nv_bfloat16 a)
Calculates nv_bfloat16 cosine in round-to-nearest-even mode.
Calculates nv_bfloat16 cosine of input a in round-to-nearest-even mode.
NOTE: this function’s implementation calls cosf(float) function and is exposed to compiler optimizations. Specifically, --use_fast_math flag changes cosf(float) into an intrinsic __cosf(float), which has less accurate numeric behavior.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The cosine of a.


__device__ __nv_bfloat16 hexp(const __nv_bfloat16 a)
Calculates nv_bfloat16 natural exponential function in round-to-nearest-even mode.
Calculates nv_bfloat16 natural exponential function of input a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The natural exponential function on a.


__device__ __nv_bfloat16 hexp10(const __nv_bfloat16 a)
Calculates nv_bfloat16 decimal exponential function in round-to-nearest-even mode.
Calculates nv_bfloat16 decimal exponential function of input a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The decimal exponential function on a.


__device__ __nv_bfloat16 hexp2(const __nv_bfloat16 a)
Calculates nv_bfloat16 binary exponential function in round-to-nearest-even mode.
Calculates nv_bfloat16 binary exponential function of input a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The binary exponential function on a.


__device__ __nv_bfloat16 hfloor(const __nv_bfloat16 h)
Calculate the largest integer less than or equal to h.
Calculate the largest integer value which is less than or equal to h.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The largest integer value which is less than or equal to h.


__device__ __nv_bfloat16 hlog(const __nv_bfloat16 a)
Calculates nv_bfloat16 natural logarithm in round-to-nearest-even mode.
Calculates nv_bfloat16 natural logarithm of input a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The natural logarithm of a.


__device__ __nv_bfloat16 hlog10(const __nv_bfloat16 a)
Calculates nv_bfloat16 decimal logarithm in round-to-nearest-even mode.
Calculates nv_bfloat16 decimal logarithm of input a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The decimal logarithm of a.


__device__ __nv_bfloat16 hlog2(const __nv_bfloat16 a)
Calculates nv_bfloat16 binary logarithm in round-to-nearest-even mode.
Calculates nv_bfloat16 binary logarithm of input a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The binary logarithm of a.


__device__ __nv_bfloat16 hrcp(const __nv_bfloat16 a)
Calculates nv_bfloat16 reciprocal in round-to-nearest-even mode.
Calculates nv_bfloat16 reciprocal of input a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The reciprocal of a.


__device__ __nv_bfloat16 hrint(const __nv_bfloat16 h)
Round input to nearest integer value in nv_bfloat16 floating-point number.
Round h to the nearest integer value in nv_bfloat16 floating-point format, with halfway cases rounded to the nearest even integer value.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The nearest integer to h.


__device__ __nv_bfloat16 hrsqrt(const __nv_bfloat16 a)
Calculates nv_bfloat16 reciprocal square root in round-to-nearest-even mode.
Calculates nv_bfloat16 reciprocal square root of input a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The reciprocal square root of a.


__device__ __nv_bfloat16 hsin(const __nv_bfloat16 a)
Calculates nv_bfloat16 sine in round-to-nearest-even mode.
Calculates nv_bfloat16 sine of input a in round-to-nearest-even mode.
NOTE: this function’s implementation calls sinf(float) function and is exposed to compiler optimizations. Specifically, --use_fast_math flag changes sinf(float) into an intrinsic __sinf(float), which has less accurate numeric behavior.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The sine of a.


__device__ __nv_bfloat16 hsqrt(const __nv_bfloat16 a)
Calculates nv_bfloat16 square root in round-to-nearest-even mode.
Calculates nv_bfloat16 square root of input a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The square root of a.


__device__ __nv_bfloat16 htanh(const __nv_bfloat16 a)
Calculates nv_bfloat16 hyperbolic tangent function in round-to-nearest-even mode.
Calculates nv_bfloat16 hyperbolic tangent function: \( \tanh(a)\) in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The hyperbolic tangent function of a.
htanh \( (\pm 0)\) returns \( (\pm 0)\).
htanh \( (\pm\infty)\) returns \( (\pm 1)\).
htanh(NaN) returns NaN.


__device__ __nv_bfloat16 htanh_approx(const __nv_bfloat16 a)
Calculates approximate nv_bfloat16 hyperbolic tangent function.
Calculates approximate nv_bfloat16 hyperbolic tangent function: \( \tanh(a)\). This operation uses HW acceleration on devices of compute capability 9.x and higher.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The approximate hyperbolic tangent function of a.
htanh_approx \( (\pm 0)\) returns \( (\pm 0)\).
htanh_approx \( (\pm\infty)\) returns \( (\pm 1)\).
htanh_approx(NaN) returns NaN.


__device__ __nv_bfloat16 htrunc(const __nv_bfloat16 h)
Truncate input argument to the integral part.
Round h to the nearest integer value that does not exceed h in magnitude.

Parameters

h – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The truncated integer value.