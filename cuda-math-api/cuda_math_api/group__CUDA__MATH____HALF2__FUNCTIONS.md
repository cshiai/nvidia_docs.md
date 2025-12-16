# 4.8. Half2 Math Functions


To use these functions, include the header file `cuda_fp16.h` in your program.


Functions


__device__ __half2 h2ceil(const __half2 h)
Calculate half2 vector ceiling of the input argument.

__device__ __half2 h2cos(const __half2 a)
Calculates half2 vector cosine in round-to-nearest-even mode.

__device__ __half2 h2exp(const __half2 a)
Calculates half2 vector exponential function in round-to-nearest-even mode.

__device__ __half2 h2exp10(const __half2 a)
Calculates half2 vector decimal exponential function in round-to-nearest-even mode.

__device__ __half2 h2exp2(const __half2 a)
Calculates half2 vector binary exponential function in round-to-nearest-even mode.

__device__ __half2 h2floor(const __half2 h)
Calculate the largest integer less than or equal to h .

__device__ __half2 h2log(const __half2 a)
Calculates half2 vector natural logarithm in round-to-nearest-even mode.

__device__ __half2 h2log10(const __half2 a)
Calculates half2 vector decimal logarithm in round-to-nearest-even mode.

__device__ __half2 h2log2(const __half2 a)
Calculates half2 vector binary logarithm in round-to-nearest-even mode.

__device__ __half2 h2rcp(const __half2 a)
Calculates half2 vector reciprocal in round-to-nearest-even mode.

__device__ __half2 h2rint(const __half2 h)
Round input to nearest integer value in half-precision floating-point number.

__device__ __half2 h2rsqrt(const __half2 a)
Calculates half2 vector reciprocal square root in round-to-nearest-even mode.

__device__ __half2 h2sin(const __half2 a)
Calculates half2 vector sine in round-to-nearest-even mode.

__device__ __half2 h2sqrt(const __half2 a)
Calculates half2 vector square root in round-to-nearest-even mode.

__device__ __half2 h2tanh(const __half2 a)
Calculates half2 vector hyperbolic tangent function in round-to-nearest-even mode.

__device__ __half2 h2tanh_approx(const __half2 a)
Calculates half2 vector approximate hyperbolic tangent function.

__device__ __half2 h2trunc(const __half2 h)
Truncate half2 vector input argument to the integral part.


## 4.8.1. Functions


__device__ __half2 h2ceil(const __half2 h)
Calculate half2 vector ceiling of the input argument.
For each component of vector h compute the smallest integer value not less than h.

See also
hceil(__half) for further details.

Parameters

h – [in] - half2. Is only being read.

Returns

half2

The vector of smallest integers not less than h.


__device__ __half2 h2cos(const __half2 a)
Calculates half2 vector cosine in round-to-nearest-even mode.
Calculates half2 cosine of input vector a in round-to-nearest-even mode.

See also
hcos(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise cosine on vector a.


__device__ __half2 h2exp(const __half2 a)
Calculates half2 vector exponential function in round-to-nearest-even mode.
Calculates half2 exponential function of input vector a in round-to-nearest-even mode.

See also
hexp(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise exponential function on vector a.


__device__ __half2 h2exp10(const __half2 a)
Calculates half2 vector decimal exponential function in round-to-nearest-even mode.
Calculates half2 decimal exponential function of input vector a in round-to-nearest-even mode.

See also
hexp10(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise decimal exponential function on vector a.


__device__ __half2 h2exp2(const __half2 a)
Calculates half2 vector binary exponential function in round-to-nearest-even mode.
Calculates half2 binary exponential function of input vector a in round-to-nearest-even mode.

See also
hexp2(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise binary exponential function on vector a.


__device__ __half2 h2floor(const __half2 h)
Calculate the largest integer less than or equal to h.
For each component of vector h calculate the largest integer value which is less than or equal to h.

See also
hfloor(__half) for further details.

Parameters

h – [in] - half2. Is only being read.

Returns

half2

The vector of largest integers which is less than or equal to h.


__device__ __half2 h2log(const __half2 a)
Calculates half2 vector natural logarithm in round-to-nearest-even mode.
Calculates half2 natural logarithm of input vector a in round-to-nearest-even mode.

See also
hlog(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise natural logarithm on vector a.


__device__ __half2 h2log10(const __half2 a)
Calculates half2 vector decimal logarithm in round-to-nearest-even mode.
Calculates half2 decimal logarithm of input vector a in round-to-nearest-even mode.

See also
hlog10(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise decimal logarithm on vector a.


__device__ __half2 h2log2(const __half2 a)
Calculates half2 vector binary logarithm in round-to-nearest-even mode.
Calculates half2 binary logarithm of input vector a in round-to-nearest-even mode.

See also
hlog2(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise binary logarithm on vector a.


__device__ __half2 h2rcp(const __half2 a)
Calculates half2 vector reciprocal in round-to-nearest-even mode.
Calculates half2 reciprocal of input vector a in round-to-nearest-even mode.

See also
hrcp(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise reciprocal on vector a.


__device__ __half2 h2rint(const __half2 h)
Round input to nearest integer value in half-precision floating-point number.
Round each component of half2 vector h to the nearest integer value in half-precision floating-point format, with halfway cases rounded to the nearest even integer value.

See also
hrint(__half) for further details.

Parameters

h – [in] - half2. Is only being read.

Returns

half2

The vector of rounded integer values.


__device__ __half2 h2rsqrt(const __half2 a)
Calculates half2 vector reciprocal square root in round-to-nearest-even mode.
Calculates half2 reciprocal square root of input vector a in round-to-nearest-even mode.

See also
hrsqrt(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise reciprocal square root on vector a.


__device__ __half2 h2sin(const __half2 a)
Calculates half2 vector sine in round-to-nearest-even mode.
Calculates half2 sine of input vector a in round-to-nearest-even mode.

See also
hsin(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise sine on vector a.


__device__ __half2 h2sqrt(const __half2 a)
Calculates half2 vector square root in round-to-nearest-even mode.
Calculates half2 square root of input vector a in round-to-nearest-even mode.

See also
hsqrt(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise square root on vector a.


__device__ __half2 h2tanh(const __half2 a)
Calculates half2 vector hyperbolic tangent function in round-to-nearest-even mode.
Calculates half2 hyperbolic tangent function of input vector a in round-to-nearest-even mode.

See also
htanh(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise hyperbolic tangent function on vector a.


__device__ __half2 h2tanh_approx(const __half2 a)
Calculates half2 vector approximate hyperbolic tangent function.
Calculates half2 approximate hyperbolic tangent function of input vector a. This operation uses HW acceleration on devices of compute capability 7.5 and higher.

See also
htanh_approx(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The elementwise approximate hyperbolic tangent function on vector a.


__device__ __half2 h2trunc(const __half2 h)
Truncate half2 vector input argument to the integral part.
Round each component of vector h to the largest integer value that does not exceed h in magnitude.

See also
htrunc(__half) for further details.

Parameters

h – [in] - half2. Is only being read.

Returns

half2

The truncated h.