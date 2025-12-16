# 5.3. Bfloat16 Comparison Functions


To use these functions, include the header file `cuda_bf16.h` in your program.


Functions


__host__ __device__ bool __heq(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 if-equal comparison.

__host__ __device__ bool __hequ(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 unordered if-equal comparison.

__host__ __device__ bool __hge(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 greater-equal comparison.

__host__ __device__ bool __hgeu(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 unordered greater-equal comparison.

__host__ __device__ bool __hgt(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 greater-than comparison.

__host__ __device__ bool __hgtu(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 unordered greater-than comparison.

__host__ __device__ int __hisinf(const __nv_bfloat16 a)
Checks if the input nv_bfloat16 number is infinite.

__host__ __device__ bool __hisnan(const __nv_bfloat16 a)
Determine whether nv_bfloat16 argument is a NaN.

__host__ __device__ bool __hle(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 less-equal comparison.

__host__ __device__ bool __hleu(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 unordered less-equal comparison.

__host__ __device__ bool __hlt(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 less-than comparison.

__host__ __device__ bool __hltu(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 unordered less-than comparison.

__host__ __device__ __nv_bfloat16 __hmax(const __nv_bfloat16 a, const __nv_bfloat16 b)
Calculates nv_bfloat16 maximum of two input values.

__host__ __device__ __nv_bfloat16 __hmax_nan(const __nv_bfloat16 a, const __nv_bfloat16 b)
Calculates nv_bfloat16 maximum of two input values, NaNs pass through.

__host__ __device__ __nv_bfloat16 __hmin(const __nv_bfloat16 a, const __nv_bfloat16 b)
Calculates nv_bfloat16 minimum of two input values.

__host__ __device__ __nv_bfloat16 __hmin_nan(const __nv_bfloat16 a, const __nv_bfloat16 b)
Calculates nv_bfloat16 minimum of two input values, NaNs pass through.

__host__ __device__ bool __hne(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 not-equal comparison.

__host__ __device__ bool __hneu(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 unordered not-equal comparison.

__host__ __device__ bool operator!=(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 unordered compare not-equal operation.

__host__ __device__ bool operator<(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 ordered less-than compare operation.

__host__ __device__ bool operator<=(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 ordered less-or-equal compare operation.

__host__ __device__ bool operator==(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 ordered compare equal operation.

__host__ __device__ bool operator>(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 ordered greater-than compare operation.

__host__ __device__ bool operator>=(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 ordered greater-or-equal compare operation.


## 5.3.1. Functions


__host__ __device__ bool __heq(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 if-equal comparison.
Performs nv_bfloat16 if-equal comparison of inputs a and b. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

bool

The boolean result of if-equal comparison of a and b.


__host__ __device__ bool __hequ(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 unordered if-equal comparison.
Performs nv_bfloat16 if-equal comparison of inputs a and b. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

bool

The boolean result of unordered if-equal comparison of a and b.


__host__ __device__ bool __hge(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 greater-equal comparison.
Performs nv_bfloat16 greater-equal comparison of inputs a and b. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

bool

The boolean result of greater-equal comparison of a and b.


__host__ __device__ bool __hgeu(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 unordered greater-equal comparison.
Performs nv_bfloat16 greater-equal comparison of inputs a and b. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

bool

The boolean result of unordered greater-equal comparison of a and b.


__host__ __device__ bool __hgt(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 greater-than comparison.
Performs nv_bfloat16 greater-than comparison of inputs a and b. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

bool

The boolean result of greater-than comparison of a and b.


__host__ __device__ bool __hgtu(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 unordered greater-than comparison.
Performs nv_bfloat16 greater-than comparison of inputs a and b. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

bool

The boolean result of unordered greater-than comparison of a and b.


__host__ __device__ int __hisinf(const __nv_bfloat16 a)
Checks if the input nv_bfloat16 number is infinite.
Checks if the input nv_bfloat16 number a is infinite.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

int

-1 if a is equal to negative infinity,
1 if a is equal to positive infinity,
0 otherwise.


__host__ __device__ bool __hisnan(const __nv_bfloat16 a)
Determine whether nv_bfloat16 argument is a NaN.
Determine whether nv_bfloat16 value a is a NaN.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

bool

true if argument is NaN.


__host__ __device__ bool __hle(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 less-equal comparison.
Performs nv_bfloat16 less-equal comparison of inputs a and b. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

bool

The boolean result of less-equal comparison of a and b.


__host__ __device__ bool __hleu(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 unordered less-equal comparison.
Performs nv_bfloat16 less-equal comparison of inputs a and b. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

bool

The boolean result of unordered less-equal comparison of a and b.


__host__ __device__ bool __hlt(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 less-than comparison.
Performs nv_bfloat16 less-than comparison of inputs a and b. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

bool

The boolean result of less-than comparison of a and b.


__host__ __device__ bool __hltu(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 unordered less-than comparison.
Performs nv_bfloat16 less-than comparison of inputs a and b. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

bool

The boolean result of unordered less-than comparison of a and b.


__host__ __device__ __nv_bfloat16 __hmax(const __nv_bfloat16 a, const __nv_bfloat16 b)
Calculates nv_bfloat16 maximum of two input values.
Calculates nv_bfloat16 max(a, b) defined as (a > b) ? a : b.

If either of inputs is NaN, the other input is returned.
If both inputs are NaNs, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16


__host__ __device__ __nv_bfloat16 __hmax_nan(const __nv_bfloat16 a, const __nv_bfloat16 b)
Calculates nv_bfloat16 maximum of two input values, NaNs pass through.
Calculates nv_bfloat16 max(a, b) defined as (a > b) ? a : b.

If either of inputs is NaN, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16


__host__ __device__ __nv_bfloat16 __hmin(const __nv_bfloat16 a, const __nv_bfloat16 b)
Calculates nv_bfloat16 minimum of two input values.
Calculates nv_bfloat16 min(a, b) defined as (a < b) ? a : b.

If either of inputs is NaN, the other input is returned.
If both inputs are NaNs, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16


__host__ __device__ __nv_bfloat16 __hmin_nan(const __nv_bfloat16 a, const __nv_bfloat16 b)
Calculates nv_bfloat16 minimum of two input values, NaNs pass through.
Calculates nv_bfloat16 min(a, b) defined as (a < b) ? a : b.

If either of inputs is NaN, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16


__host__ __device__ bool __hne(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 not-equal comparison.
Performs nv_bfloat16 not-equal comparison of inputs a and b. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

bool

The boolean result of not-equal comparison of a and b.


__host__ __device__ bool __hneu(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 unordered not-equal comparison.
Performs nv_bfloat16 not-equal comparison of inputs a and b. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

bool

The boolean result of unordered not-equal comparison of a and b.


__host__ __device__ bool operator!=(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 unordered compare not-equal operation.
See also __hneu(__nv_bfloat16, __nv_bfloat16)


__host__ __device__ bool operator<(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 ordered less-than compare operation.
See also __hlt(__nv_bfloat16, __nv_bfloat16)


__host__ __device__ bool operator<=(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 ordered less-or-equal compare operation.
See also __hle(__nv_bfloat16, __nv_bfloat16)


__host__ __device__ bool operator==(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 ordered compare equal operation.
See also __heq(__nv_bfloat16, __nv_bfloat16)


__host__ __device__ bool operator>(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 ordered greater-than compare operation.
See also __hgt(__nv_bfloat16, __nv_bfloat16)


__host__ __device__ bool operator>=(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 ordered greater-or-equal compare operation.
See also __hge(__nv_bfloat16, __nv_bfloat16)