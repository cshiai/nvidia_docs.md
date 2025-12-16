# 4.3. Half Comparison Functions


To use these functions, include the header file `cuda_fp16.h` in your program.


Functions


__host__ __device__ bool __heq(const __half a, const __half b)
Performs half if-equal comparison.

__host__ __device__ bool __hequ(const __half a, const __half b)
Performs half unordered if-equal comparison.

__host__ __device__ bool __hge(const __half a, const __half b)
Performs half greater-equal comparison.

__host__ __device__ bool __hgeu(const __half a, const __half b)
Performs half unordered greater-equal comparison.

__host__ __device__ bool __hgt(const __half a, const __half b)
Performs half greater-than comparison.

__host__ __device__ bool __hgtu(const __half a, const __half b)
Performs half unordered greater-than comparison.

__host__ __device__ int __hisinf(const __half a)
Checks if the input half number is infinite.

__host__ __device__ bool __hisnan(const __half a)
Determine whether half argument is a NaN.

__host__ __device__ bool __hle(const __half a, const __half b)
Performs half less-equal comparison.

__host__ __device__ bool __hleu(const __half a, const __half b)
Performs half unordered less-equal comparison.

__host__ __device__ bool __hlt(const __half a, const __half b)
Performs half less-than comparison.

__host__ __device__ bool __hltu(const __half a, const __half b)
Performs half unordered less-than comparison.

__host__ __device__ __half __hmax(const __half a, const __half b)
Calculates half maximum of two input values.

__host__ __device__ __half __hmax_nan(const __half a, const __half b)
Calculates half maximum of two input values, NaNs pass through.

__host__ __device__ __half __hmin(const __half a, const __half b)
Calculates half minimum of two input values.

__host__ __device__ __half __hmin_nan(const __half a, const __half b)
Calculates half minimum of two input values, NaNs pass through.

__host__ __device__ bool __hne(const __half a, const __half b)
Performs half not-equal comparison.

__host__ __device__ bool __hneu(const __half a, const __half b)
Performs half unordered not-equal comparison.

__host__ __device__ bool operator!=(const __half &lh, const __half &rh)
Performs half unordered compare not-equal operation.

__host__ __device__ bool operator<(const __half &lh, const __half &rh)
Performs half ordered less-than compare operation.

__host__ __device__ bool operator<=(const __half &lh, const __half &rh)
Performs half ordered less-or-equal compare operation.

__host__ __device__ bool operator==(const __half &lh, const __half &rh)
Performs half ordered compare equal operation.

__host__ __device__ bool operator>(const __half &lh, const __half &rh)
Performs half ordered greater-than compare operation.

__host__ __device__ bool operator>=(const __half &lh, const __half &rh)
Performs half ordered greater-or-equal compare operation.


## 4.3.1. Functions


__host__ __device__ bool __heq(const __half a, const __half b)
Performs half if-equal comparison.
Performs half if-equal comparison of inputs a and b. NaN inputs generate false results.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

bool

The boolean result of if-equal comparison of a and b.


__host__ __device__ bool __hequ(const __half a, const __half b)
Performs half unordered if-equal comparison.
Performs half if-equal comparison of inputs a and b. NaN inputs generate true results.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

bool

The boolean result of unordered if-equal comparison of a and b.


__host__ __device__ bool __hge(const __half a, const __half b)
Performs half greater-equal comparison.
Performs half greater-equal comparison of inputs a and b. NaN inputs generate false results.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

bool

The boolean result of greater-equal comparison of a and b.


__host__ __device__ bool __hgeu(const __half a, const __half b)
Performs half unordered greater-equal comparison.
Performs half greater-equal comparison of inputs a and b. NaN inputs generate true results.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

bool

The boolean result of unordered greater-equal comparison of a and b.


__host__ __device__ bool __hgt(const __half a, const __half b)
Performs half greater-than comparison.
Performs half greater-than comparison of inputs a and b. NaN inputs generate false results.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

bool

The boolean result of greater-than comparison of a and b.


__host__ __device__ bool __hgtu(const __half a, const __half b)
Performs half unordered greater-than comparison.
Performs half greater-than comparison of inputs a and b. NaN inputs generate true results.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

bool

The boolean result of unordered greater-than comparison of a and b.


__host__ __device__ int __hisinf(const __half a)
Checks if the input half number is infinite.
Checks if the input half number a is infinite.

Parameters

a – [in] - half. Is only being read.

Returns

int

-1 if a is equal to negative infinity,
1 if a is equal to positive infinity,
0 otherwise.


__host__ __device__ bool __hisnan(const __half a)
Determine whether half argument is a NaN.
Determine whether half value a is a NaN.

Parameters

a – [in] - half. Is only being read.

Returns

bool

true if argument is NaN.


__host__ __device__ bool __hle(const __half a, const __half b)
Performs half less-equal comparison.
Performs half less-equal comparison of inputs a and b. NaN inputs generate false results.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

bool

The boolean result of less-equal comparison of a and b.


__host__ __device__ bool __hleu(const __half a, const __half b)
Performs half unordered less-equal comparison.
Performs half less-equal comparison of inputs a and b. NaN inputs generate true results.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

bool

The boolean result of unordered less-equal comparison of a and b.


__host__ __device__ bool __hlt(const __half a, const __half b)
Performs half less-than comparison.
Performs half less-than comparison of inputs a and b. NaN inputs generate false results.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

bool

The boolean result of less-than comparison of a and b.


__host__ __device__ bool __hltu(const __half a, const __half b)
Performs half unordered less-than comparison.
Performs half less-than comparison of inputs a and b. NaN inputs generate true results.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

bool

The boolean result of unordered less-than comparison of a and b.


__host__ __device__ __half __hmax(const __half a, const __half b)
Calculates half maximum of two input values.
Calculates half max(a, b) defined as (a > b) ? a : b.

If either of inputs is NaN, the other input is returned.
If both inputs are NaNs, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half


__host__ __device__ __half __hmax_nan(const __half a, const __half b)
Calculates half maximum of two input values, NaNs pass through.
Calculates half max(a, b) defined as (a > b) ? a : b.

If either of inputs is NaN, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half


__host__ __device__ __half __hmin(const __half a, const __half b)
Calculates half minimum of two input values.
Calculates half min(a, b) defined as (a < b) ? a : b.

If either of inputs is NaN, the other input is returned.
If both inputs are NaNs, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half


__host__ __device__ __half __hmin_nan(const __half a, const __half b)
Calculates half minimum of two input values, NaNs pass through.
Calculates half min(a, b) defined as (a < b) ? a : b.

If either of inputs is NaN, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half


__host__ __device__ bool __hne(const __half a, const __half b)
Performs half not-equal comparison.
Performs half not-equal comparison of inputs a and b. NaN inputs generate false results.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

bool

The boolean result of not-equal comparison of a and b.


__host__ __device__ bool __hneu(const __half a, const __half b)
Performs half unordered not-equal comparison.
Performs half not-equal comparison of inputs a and b. NaN inputs generate true results.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

bool

The boolean result of unordered not-equal comparison of a and b.


__host__ __device__ bool operator!=(const __half &lh, const __half &rh)
Performs half unordered compare not-equal operation.

See also
__hneu(__half, __half)


__host__ __device__ bool operator<(const __half &lh, const __half &rh)
Performs half ordered less-than compare operation.

See also
__hlt(__half, __half)


__host__ __device__ bool operator<=(const __half &lh, const __half &rh)
Performs half ordered less-or-equal compare operation.

See also
__hle(__half, __half)


__host__ __device__ bool operator==(const __half &lh, const __half &rh)
Performs half ordered compare equal operation.

See also
__heq(__half, __half)


__host__ __device__ bool operator>(const __half &lh, const __half &rh)
Performs half ordered greater-than compare operation.

See also
__hgt(__half, __half)


__host__ __device__ bool operator>=(const __half &lh, const __half &rh)
Performs half ordered greater-or-equal compare operation.

See also
__hge(__half, __half)