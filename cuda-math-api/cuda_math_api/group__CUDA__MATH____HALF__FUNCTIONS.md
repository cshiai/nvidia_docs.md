# 4.4. Half Math Functions


To use these functions, include the header file `cuda_fp16.h` in your program.


Functions


__device__ __half hceil(const __half h)
Calculate ceiling of the input argument.

__device__ __half hcos(const __half a)
Calculates half cosine in round-to-nearest-even mode.

__device__ __half hexp(const __half a)
Calculates half natural exponential function in round-to-nearest-even mode.

__device__ __half hexp10(const __half a)
Calculates half decimal exponential function in round-to-nearest-even mode.

__device__ __half hexp2(const __half a)
Calculates half binary exponential function in round-to-nearest-even mode.

__device__ __half hfloor(const __half h)
Calculate the largest integer less than or equal to h .

__device__ __half hlog(const __half a)
Calculates half natural logarithm in round-to-nearest-even mode.

__device__ __half hlog10(const __half a)
Calculates half decimal logarithm in round-to-nearest-even mode.

__device__ __half hlog2(const __half a)
Calculates half binary logarithm in round-to-nearest-even mode.

__device__ __half hrcp(const __half a)
Calculates half reciprocal in round-to-nearest-even mode.

__device__ __half hrint(const __half h)
Round input to nearest integer value in half-precision floating-point number.

__device__ __half hrsqrt(const __half a)
Calculates half reciprocal square root in round-to-nearest-even mode.

__device__ __half hsin(const __half a)
Calculates half sine in round-to-nearest-even mode.

__device__ __half hsqrt(const __half a)
Calculates half square root in round-to-nearest-even mode.

__device__ __half htanh(const __half a)
Calculates half hyperbolic tangent function in round-to-nearest-even mode.

__device__ __half htanh_approx(const __half a)
Calculates approximate half hyperbolic tangent function.

__device__ __half htrunc(const __half h)
Truncate input argument to the integral part.


## 4.4.1. Functions


__device__ __half hceil(const __half h)
Calculate ceiling of the input argument.
Compute the smallest integer value not less than h.

Parameters

h – [in] - half. Is only being read.

Returns

half

The smallest integer value not less than h.
hceil( \( \pm 0 \) ) returns \( \pm 0 \).
hceil( \( \pm \infty \) ) returns \( \pm \infty \).
hceil(NaN) returns NaN.


__device__ __half hcos(const __half a)
Calculates half cosine in round-to-nearest-even mode.
Calculates half cosine of input a in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.

Returns

half

The cosine of a.
hcos \( (\pm 0)\) returns 1.
hcos \( (\pm \infty)\) returns NaN.
hcos(NaN) returns NaN.


__device__ __half hexp(const __half a)
Calculates half natural exponential function in round-to-nearest-even mode.
Calculates half natural exponential function of input: \( e^{a}\) in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.

Returns

half

The natural exponential function on a.
hexp \( (\pm 0)\) returns 1.
hexp \( (-\infty)\) returns +0.
hexp \( (+\infty)\) returns \( +\infty \).
hexp(NaN) returns NaN.


__device__ __half hexp10(const __half a)
Calculates half decimal exponential function in round-to-nearest-even mode.
Calculates half decimal exponential function of input: \( 10^{a}\) in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.

Returns

half

The decimal exponential function on a.
hexp10 \( (\pm 0)\) returns 1.
hexp10 \( (-\infty)\) returns +0.
hexp10 \( (+\infty)\) returns \( +\infty \).
hexp10(NaN) returns NaN.


__device__ __half hexp2(const __half a)
Calculates half binary exponential function in round-to-nearest-even mode.
Calculates half binary exponential function of input: \( 2^{a}\) in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.

Returns

half

The binary exponential function on a.
hexp2 \( (\pm 0)\) returns 1.
hexp2 \( (-\infty)\) returns +0.
hexp2 \( (+\infty)\) returns \( +\infty \).
hexp2(NaN) returns NaN.


__device__ __half hfloor(const __half h)
Calculate the largest integer less than or equal to h.
Calculate the largest integer value which is less than or equal to h.

Parameters

h – [in] - half. Is only being read.

Returns

half

The largest integer value which is less than or equal to h.
hfloor( \( \pm 0 \) ) returns \( \pm 0 \).
hfloor( \( \pm \infty \) ) returns \( \pm \infty \).
hfloor(NaN) returns NaN.


__device__ __half hlog(const __half a)
Calculates half natural logarithm in round-to-nearest-even mode.
Calculates half natural logarithm of input: \( \ln(a)\) in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.

Returns

half

The natural logarithm of a.
hlog \( (\pm 0)\) returns \( -\infty \).
hlog(1) returns +0.
hlog(x), x < 0 returns NaN.
hlog \( (+\infty)\) returns \( +\infty \).
hlog(NaN) returns NaN.


__device__ __half hlog10(const __half a)
Calculates half decimal logarithm in round-to-nearest-even mode.
Calculates half decimal logarithm of input: \( \log_{10}(a)\) in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.

Returns

half

The decimal logarithm of a.
hlog10 \( (\pm 0)\) returns \( -\infty \).
hlog10(1) returns +0.
hlog10(x), x < 0 returns NaN.
hlog10 \( (+\infty)\) returns \( +\infty \).
hlog10(NaN) returns NaN.


__device__ __half hlog2(const __half a)
Calculates half binary logarithm in round-to-nearest-even mode.
Calculates half binary logarithm of input: \( \log_{2}(a)\) in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.

Returns

half

The binary logarithm of a.
hlog2 \( (\pm 0)\) returns \( -\infty \).
hlog2(1) returns +0.
hlog2(x), x < 0 returns NaN.
hlog2 \( (+\infty)\) returns \( +\infty \).
hlog2(NaN) returns NaN.


__device__ __half hrcp(const __half a)
Calculates half reciprocal in round-to-nearest-even mode.
Calculates half reciprocal of input: \( \frac{1}{a}\) in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.

Returns

half

The reciprocal of a.
hrcp \( (\pm 0)\) returns \( \pm \infty \).
hrcp \( (\pm \infty)\) returns \( \pm 0 \).
hrcp(NaN) returns NaN.


__device__ __half hrint(const __half h)
Round input to nearest integer value in half-precision floating-point number.
Round h to the nearest integer value in half-precision floating-point format, with halfway cases rounded to the nearest even integer value.

Parameters

h – [in] - half. Is only being read.

Returns

half

The nearest integer to h.
hrint( \( \pm 0 \) ) returns \( \pm 0 \).
hrint( \( \pm \infty \) ) returns \( \pm \infty \).
hrint(NaN) returns NaN.


__device__ __half hrsqrt(const __half a)
Calculates half reciprocal square root in round-to-nearest-even mode.
Calculates half reciprocal square root of input: \( \frac{1}{\sqrt{a}}\) in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.

Returns

half

The reciprocal square root of a.
hrsqrt \( (\pm 0)\) returns \( \pm \infty \).
hrsqrt \( (+\infty)\) returns +0.
hrsqrt \( (x), x < 0.0\) returns NaN.
hrsqrt(NaN) returns NaN.


__device__ __half hsin(const __half a)
Calculates half sine in round-to-nearest-even mode.
Calculates half sine of input a in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.

Returns

half

The sine of a.
hsin \( (\pm 0)\) returns \( (\pm 0)\).
hsin \( (\pm \infty)\) returns NaN.
hsin(NaN) returns NaN.


__device__ __half hsqrt(const __half a)
Calculates half square root in round-to-nearest-even mode.
Calculates half square root of input: \( \sqrt{a} \) in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.

Returns

half

The square root of a.
hsqrt \( (+\infty)\) returns \( +\infty \).
hsqrt \( (\pm 0)\) returns \( \pm 0 \).
hsqrt \( (x), x < 0.0\) returns NaN.
hsqrt(NaN) returns NaN.


__device__ __half htanh(const __half a)
Calculates half hyperbolic tangent function in round-to-nearest-even mode.
Calculates half hyperbolic tangent function: \( \tanh(a)\) in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.

Returns

half

The hyperbolic tangent function of a.
htanh \( (\pm 0)\) returns \( (\pm 0)\).
htanh \( (\pm\infty)\) returns \( (\pm 1)\).
htanh(NaN) returns NaN.


__device__ __half htanh_approx(const __half a)
Calculates approximate half hyperbolic tangent function.
Calculates approximate half hyperbolic tangent function: \( \tanh(a)\). This operation uses HW acceleration on devices of compute capability 7.5 and higher.

Parameters

a – [in] - half. Is only being read.

Returns

half

The approximate hyperbolic tangent function of a.
htanh_approx \( (\pm 0)\) returns \( (\pm 0)\).
htanh_approx \( (\pm\infty)\) returns \( (\pm 1)\).
htanh_approx(NaN) returns NaN.


__device__ __half htrunc(const __half h)
Truncate input argument to the integral part.
Round h to the largest integer value that does not exceed h in magnitude.

Parameters

h – [in] - half. Is only being read.

Returns

half

The truncated value.
htrunc( \( \pm 0 \) ) returns \( \pm 0 \).
htrunc( \( \pm \infty \) ) returns \( \pm \infty \).
htrunc(NaN) returns NaN.