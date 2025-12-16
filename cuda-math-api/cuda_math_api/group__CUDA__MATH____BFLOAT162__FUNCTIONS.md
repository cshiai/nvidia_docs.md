# 5.8. Bfloat162 Math Functions


To use these functions, include the header file `cuda_bf16.h` in your program.


Functions


__device__ __nv_bfloat162 h2ceil(const __nv_bfloat162 h)
Calculate nv_bfloat162 vector ceiling of the input argument.

__device__ __nv_bfloat162 h2cos(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector cosine in round-to-nearest-even mode.

__device__ __nv_bfloat162 h2exp(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector exponential function in round-to-nearest-even mode.

__device__ __nv_bfloat162 h2exp10(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector decimal exponential function in round-to-nearest-even mode.

__device__ __nv_bfloat162 h2exp2(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector binary exponential function in round-to-nearest-even mode.

__device__ __nv_bfloat162 h2floor(const __nv_bfloat162 h)
Calculate the largest integer less than or equal to h .

__device__ __nv_bfloat162 h2log(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector natural logarithm in round-to-nearest-even mode.

__device__ __nv_bfloat162 h2log10(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector decimal logarithm in round-to-nearest-even mode.

__device__ __nv_bfloat162 h2log2(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector binary logarithm in round-to-nearest-even mode.

__device__ __nv_bfloat162 h2rcp(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector reciprocal in round-to-nearest-even mode.

__device__ __nv_bfloat162 h2rint(const __nv_bfloat162 h)
Round input to nearest integer value in nv_bfloat16 floating-point number.

__device__ __nv_bfloat162 h2rsqrt(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector reciprocal square root in round-to-nearest-even mode.

__device__ __nv_bfloat162 h2sin(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector sine in round-to-nearest-even mode.

__device__ __nv_bfloat162 h2sqrt(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector square root in round-to-nearest-even mode.

__device__ __nv_bfloat162 h2tanh(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector hyperbolic tangent function in round-to-nearest-even mode.

__device__ __nv_bfloat162 h2tanh_approx(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector approximate hyperbolic tangent function.

__device__ __nv_bfloat162 h2trunc(const __nv_bfloat162 h)
Truncate nv_bfloat162 vector input argument to the integral part.


## 5.8.1. Functions


__device__ __nv_bfloat162 h2ceil(const __nv_bfloat162 h)
Calculate nv_bfloat162 vector ceiling of the input argument.
For each component of vector h compute the smallest integer value not less than h.

Parameters

h – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The vector of smallest integers not less than h.


__device__ __nv_bfloat162 h2cos(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector cosine in round-to-nearest-even mode.
Calculates nv_bfloat162 cosine of input vector a in round-to-nearest-even mode.
NOTE: this function’s implementation calls cosf(float) function and is exposed to compiler optimizations. Specifically, --use_fast_math flag changes cosf(float) into an intrinsic __cosf(float), which has less accurate numeric behavior.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise cosine on vector a.


__device__ __nv_bfloat162 h2exp(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector exponential function in round-to-nearest-even mode.
Calculates nv_bfloat162 exponential function of input vector a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise exponential function on vector a.


__device__ __nv_bfloat162 h2exp10(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector decimal exponential function in round-to-nearest-even mode.
Calculates nv_bfloat162 decimal exponential function of input vector a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise decimal exponential function on vector a.


__device__ __nv_bfloat162 h2exp2(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector binary exponential function in round-to-nearest-even mode.
Calculates nv_bfloat162 binary exponential function of input vector a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise binary exponential function on vector a.


__device__ __nv_bfloat162 h2floor(const __nv_bfloat162 h)
Calculate the largest integer less than or equal to h.
For each component of vector h calculate the largest integer value which is less than or equal to h.

Parameters

h – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The vector of largest integers which is less than or equal to h.


__device__ __nv_bfloat162 h2log(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector natural logarithm in round-to-nearest-even mode.
Calculates nv_bfloat162 natural logarithm of input vector a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise natural logarithm on vector a.


__device__ __nv_bfloat162 h2log10(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector decimal logarithm in round-to-nearest-even mode.
Calculates nv_bfloat162 decimal logarithm of input vector a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise decimal logarithm on vector a.


__device__ __nv_bfloat162 h2log2(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector binary logarithm in round-to-nearest-even mode.
Calculates nv_bfloat162 binary logarithm of input vector a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise binary logarithm on vector a.


__device__ __nv_bfloat162 h2rcp(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector reciprocal in round-to-nearest-even mode.
Calculates nv_bfloat162 reciprocal of input vector a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise reciprocal on vector a.


__device__ __nv_bfloat162 h2rint(const __nv_bfloat162 h)
Round input to nearest integer value in nv_bfloat16 floating-point number.
Round each component of nv_bfloat162 vector h to the nearest integer value in nv_bfloat16 floating-point format, with halfway cases rounded to the nearest even integer value.

Parameters

h – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The vector of rounded integer values.


__device__ __nv_bfloat162 h2rsqrt(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector reciprocal square root in round-to-nearest-even mode.
Calculates nv_bfloat162 reciprocal square root of input vector a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise reciprocal square root on vector a.


__device__ __nv_bfloat162 h2sin(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector sine in round-to-nearest-even mode.
Calculates nv_bfloat162 sine of input vector a in round-to-nearest-even mode.
NOTE: this function’s implementation calls sinf(float) function and is exposed to compiler optimizations. Specifically, --use_fast_math flag changes sinf(float) into an intrinsic __sinf(float), which has less accurate numeric behavior.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise sine on vector a.


__device__ __nv_bfloat162 h2sqrt(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector square root in round-to-nearest-even mode.
Calculates nv_bfloat162 square root of input vector a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise square root on vector a.


__device__ __nv_bfloat162 h2tanh(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector hyperbolic tangent function in round-to-nearest-even mode.
Calculates nv_bfloat162 hyperbolic tangent function of input vector a in round-to-nearest-even mode.

See also
htanh(__nv_bfloat16) for further details.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise hyperbolic tangent function on vector a.


__device__ __nv_bfloat162 h2tanh_approx(const __nv_bfloat162 a)
Calculates nv_bfloat162 vector approximate hyperbolic tangent function.
Calculates nv_bfloat162 approximate hyperbolic tangent function of input vector a. This operation uses HW acceleration on devices of compute capability 9.x and higher.

See also
htanh_approx(__nv_bfloat16) for further details.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise approximate hyperbolic tangent function on vector a.


__device__ __nv_bfloat162 h2trunc(const __nv_bfloat162 h)
Truncate nv_bfloat162 vector input argument to the integral part.
Round each component of vector h to the nearest integer value that does not exceed h in magnitude.

Parameters

h – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The truncated h.