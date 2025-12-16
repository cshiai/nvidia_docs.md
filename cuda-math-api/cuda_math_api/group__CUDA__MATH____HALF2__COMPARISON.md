# 4.7. Half2 Comparison Functions


To use these functions, include the header file `cuda_fp16.h` in your program.


Functions


__host__ __device__ bool __hbeq2(const __half2 a, const __half2 b)
Performs half2 vector if-equal comparison and returns boolean true if both half results are true, boolean false otherwise.

__host__ __device__ bool __hbequ2(const __half2 a, const __half2 b)
Performs half2 vector unordered if-equal comparison and returns boolean true if both half results are true, boolean false otherwise.

__host__ __device__ bool __hbge2(const __half2 a, const __half2 b)
Performs half2 vector greater-equal comparison and returns boolean true if both half results are true, boolean false otherwise.

__host__ __device__ bool __hbgeu2(const __half2 a, const __half2 b)
Performs half2 vector unordered greater-equal comparison and returns boolean true if both half results are true, boolean false otherwise.

__host__ __device__ bool __hbgt2(const __half2 a, const __half2 b)
Performs half2 vector greater-than comparison and returns boolean true if both half results are true, boolean false otherwise.

__host__ __device__ bool __hbgtu2(const __half2 a, const __half2 b)
Performs half2 vector unordered greater-than comparison and returns boolean true if both half results are true, boolean false otherwise.

__host__ __device__ bool __hble2(const __half2 a, const __half2 b)
Performs half2 vector less-equal comparison and returns boolean true if both half results are true, boolean false otherwise.

__host__ __device__ bool __hbleu2(const __half2 a, const __half2 b)
Performs half2 vector unordered less-equal comparison and returns boolean true if both half results are true, boolean false otherwise.

__host__ __device__ bool __hblt2(const __half2 a, const __half2 b)
Performs half2 vector less-than comparison and returns boolean true if both half results are true, boolean false otherwise.

__host__ __device__ bool __hbltu2(const __half2 a, const __half2 b)
Performs half2 vector unordered less-than comparison and returns boolean true if both half results are true, boolean false otherwise.

__host__ __device__ bool __hbne2(const __half2 a, const __half2 b)
Performs half2 vector not-equal comparison and returns boolean true if both half results are true, boolean false otherwise.

__host__ __device__ bool __hbneu2(const __half2 a, const __half2 b)
Performs half2 vector unordered not-equal comparison and returns boolean true if both half results are true, boolean false otherwise.

__host__ __device__ __half2 __heq2(const __half2 a, const __half2 b)
Performs half2 vector if-equal comparison.

__host__ __device__ unsigned int __heq2_mask(const __half2 a, const __half2 b)
Performs half2 vector if-equal comparison.

__host__ __device__ __half2 __hequ2(const __half2 a, const __half2 b)
Performs half2 vector unordered if-equal comparison.

__host__ __device__ unsigned int __hequ2_mask(const __half2 a, const __half2 b)
Performs half2 vector unordered if-equal comparison.

__host__ __device__ __half2 __hge2(const __half2 a, const __half2 b)
Performs half2 vector greater-equal comparison.

__host__ __device__ unsigned int __hge2_mask(const __half2 a, const __half2 b)
Performs half2 vector greater-equal comparison.

__host__ __device__ __half2 __hgeu2(const __half2 a, const __half2 b)
Performs half2 vector unordered greater-equal comparison.

__host__ __device__ unsigned int __hgeu2_mask(const __half2 a, const __half2 b)
Performs half2 vector unordered greater-equal comparison.

__host__ __device__ __half2 __hgt2(const __half2 a, const __half2 b)
Performs half2 vector greater-than comparison.

__host__ __device__ unsigned int __hgt2_mask(const __half2 a, const __half2 b)
Performs half2 vector greater-than comparison.

__host__ __device__ __half2 __hgtu2(const __half2 a, const __half2 b)
Performs half2 vector unordered greater-than comparison.

__host__ __device__ unsigned int __hgtu2_mask(const __half2 a, const __half2 b)
Performs half2 vector unordered greater-than comparison.

__host__ __device__ __half2 __hisnan2(const __half2 a)
Determine whether half2 argument is a NaN.

__host__ __device__ __half2 __hle2(const __half2 a, const __half2 b)
Performs half2 vector less-equal comparison.

__host__ __device__ unsigned int __hle2_mask(const __half2 a, const __half2 b)
Performs half2 vector less-equal comparison.

__host__ __device__ __half2 __hleu2(const __half2 a, const __half2 b)
Performs half2 vector unordered less-equal comparison.

__host__ __device__ unsigned int __hleu2_mask(const __half2 a, const __half2 b)
Performs half2 vector unordered less-equal comparison.

__host__ __device__ __half2 __hlt2(const __half2 a, const __half2 b)
Performs half2 vector less-than comparison.

__host__ __device__ unsigned int __hlt2_mask(const __half2 a, const __half2 b)
Performs half2 vector less-than comparison.

__host__ __device__ __half2 __hltu2(const __half2 a, const __half2 b)
Performs half2 vector unordered less-than comparison.

__host__ __device__ unsigned int __hltu2_mask(const __half2 a, const __half2 b)
Performs half2 vector unordered less-than comparison.

__host__ __device__ __half2 __hmax2(const __half2 a, const __half2 b)
Calculates half2 vector maximum of two inputs.

__host__ __device__ __half2 __hmax2_nan(const __half2 a, const __half2 b)
Calculates half2 vector maximum of two inputs, NaNs pass through.

__host__ __device__ __half2 __hmin2(const __half2 a, const __half2 b)
Calculates half2 vector minimum of two inputs.

__host__ __device__ __half2 __hmin2_nan(const __half2 a, const __half2 b)
Calculates half2 vector minimum of two inputs, NaNs pass through.

__host__ __device__ __half2 __hne2(const __half2 a, const __half2 b)
Performs half2 vector not-equal comparison.

__host__ __device__ unsigned int __hne2_mask(const __half2 a, const __half2 b)
Performs half2 vector not-equal comparison.

__host__ __device__ __half2 __hneu2(const __half2 a, const __half2 b)
Performs half2 vector unordered not-equal comparison.

__host__ __device__ unsigned int __hneu2_mask(const __half2 a, const __half2 b)
Performs half2 vector unordered not-equal comparison.

__host__ __device__ bool operator!=(const __half2 &lh, const __half2 &rh)
Performs packed half unordered compare not-equal operation.

__host__ __device__ bool operator<(const __half2 &lh, const __half2 &rh)
Performs packed half ordered less-than compare operation.

__host__ __device__ bool operator<=(const __half2 &lh, const __half2 &rh)
Performs packed half ordered less-or-equal compare operation.

__host__ __device__ bool operator==(const __half2 &lh, const __half2 &rh)
Performs packed half ordered compare equal operation.

__host__ __device__ bool operator>(const __half2 &lh, const __half2 &rh)
Performs packed half ordered greater-than compare operation.

__host__ __device__ bool operator>=(const __half2 &lh, const __half2 &rh)
Performs packed half ordered greater-or-equal compare operation.


## 4.7.1. Functions


__host__ __device__ bool __hbeq2(const __half2 a, const __half2 b)
Performs half2 vector if-equal comparison and returns boolean true if both half results are true, boolean false otherwise.
Performs half2 vector if-equal comparison of inputs a and b. The bool result is set to true only if both half if-equal comparisons evaluate to true, or false otherwise. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

bool

true if both half results of if-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbequ2(const __half2 a, const __half2 b)
Performs half2 vector unordered if-equal comparison and returns boolean true if both half results are true, boolean false otherwise.
Performs half2 vector if-equal comparison of inputs a and b. The bool result is set to true only if both half if-equal comparisons evaluate to true, or false otherwise. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

bool

true if both half results of unordered if-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbge2(const __half2 a, const __half2 b)
Performs half2 vector greater-equal comparison and returns boolean true if both half results are true, boolean false otherwise.
Performs half2 vector greater-equal comparison of inputs a and b. The bool result is set to true only if both half greater-equal comparisons evaluate to true, or false otherwise. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

bool

true if both half results of greater-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbgeu2(const __half2 a, const __half2 b)
Performs half2 vector unordered greater-equal comparison and returns boolean true if both half results are true, boolean false otherwise.
Performs half2 vector greater-equal comparison of inputs a and b. The bool result is set to true only if both half greater-equal comparisons evaluate to true, or false otherwise. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

bool

true if both half results of unordered greater-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbgt2(const __half2 a, const __half2 b)
Performs half2 vector greater-than comparison and returns boolean true if both half results are true, boolean false otherwise.
Performs half2 vector greater-than comparison of inputs a and b. The bool result is set to true only if both half greater-than comparisons evaluate to true, or false otherwise. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

bool

true if both half results of greater-than comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbgtu2(const __half2 a, const __half2 b)
Performs half2 vector unordered greater-than comparison and returns boolean true if both half results are true, boolean false otherwise.
Performs half2 vector greater-than comparison of inputs a and b. The bool result is set to true only if both half greater-than comparisons evaluate to true, or false otherwise. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

bool

true if both half results of unordered greater-than comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hble2(const __half2 a, const __half2 b)
Performs half2 vector less-equal comparison and returns boolean true if both half results are true, boolean false otherwise.
Performs half2 vector less-equal comparison of inputs a and b. The bool result is set to true only if both half less-equal comparisons evaluate to true, or false otherwise. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

bool

true if both half results of less-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbleu2(const __half2 a, const __half2 b)
Performs half2 vector unordered less-equal comparison and returns boolean true if both half results are true, boolean false otherwise.
Performs half2 vector less-equal comparison of inputs a and b. The bool result is set to true only if both half less-equal comparisons evaluate to true, or false otherwise. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

bool

true if both half results of unordered less-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hblt2(const __half2 a, const __half2 b)
Performs half2 vector less-than comparison and returns boolean true if both half results are true, boolean false otherwise.
Performs half2 vector less-than comparison of inputs a and b. The bool result is set to true only if both half less-than comparisons evaluate to true, or false otherwise. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

bool

true if both half results of less-than comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbltu2(const __half2 a, const __half2 b)
Performs half2 vector unordered less-than comparison and returns boolean true if both half results are true, boolean false otherwise.
Performs half2 vector less-than comparison of inputs a and b. The bool result is set to true only if both half less-than comparisons evaluate to true, or false otherwise. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

bool

true if both half results of unordered less-than comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbne2(const __half2 a, const __half2 b)
Performs half2 vector not-equal comparison and returns boolean true if both half results are true, boolean false otherwise.
Performs half2 vector not-equal comparison of inputs a and b. The bool result is set to true only if both half not-equal comparisons evaluate to true, or false otherwise. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

bool

true if both half results of not-equal comparison of vectors a and b are true,
false otherwise.


__host__ __device__ bool __hbneu2(const __half2 a, const __half2 b)
Performs half2 vector unordered not-equal comparison and returns boolean true if both half results are true, boolean false otherwise.
Performs half2 vector not-equal comparison of inputs a and b. The bool result is set to true only if both half not-equal comparisons evaluate to true, or false otherwise. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

bool

true if both half results of unordered not-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ __half2 __heq2(const __half2 a, const __half2 b)
Performs half2 vector if-equal comparison.
Performs half2 vector if-equal comparison of inputs a and b. The corresponding half results are set to 1.0 for true, or 0.0 for false. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The vector result of if-equal comparison of vectors a and b.


__host__ __device__ unsigned int __heq2_mask(const __half2 a, const __half2 b)
Performs half2 vector if-equal comparison.
Performs half2 vector if-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

unsigned int

The vector mask result of if-equal comparison of vectors a and b.


__host__ __device__ __half2 __hequ2(const __half2 a, const __half2 b)
Performs half2 vector unordered if-equal comparison.
Performs half2 vector if-equal comparison of inputs a and b. The corresponding half results are set to 1.0 for true, or 0.0 for false. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The vector result of unordered if-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hequ2_mask(const __half2 a, const __half2 b)
Performs half2 vector unordered if-equal comparison.
Performs half2 vector if-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

unsigned int

The vector mask result of unordered if-equal comparison of vectors a and b.


__host__ __device__ __half2 __hge2(const __half2 a, const __half2 b)
Performs half2 vector greater-equal comparison.
Performs half2 vector greater-equal comparison of inputs a and b. The corresponding half results are set to 1.0 for true, or 0.0 for false. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The vector result of greater-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hge2_mask(const __half2 a, const __half2 b)
Performs half2 vector greater-equal comparison.
Performs half2 vector greater-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

unsigned int

The vector mask result of greater-equal comparison of vectors a and b.


__host__ __device__ __half2 __hgeu2(const __half2 a, const __half2 b)
Performs half2 vector unordered greater-equal comparison.
Performs half2 vector greater-equal comparison of inputs a and b. The corresponding half results are set to 1.0 for true, or 0.0 for false. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The half2 vector result of unordered greater-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hgeu2_mask(const __half2 a, const __half2 b)
Performs half2 vector unordered greater-equal comparison.
Performs half2 vector greater-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

unsigned int

The vector mask result of unordered greater-equal comparison of vectors a and b.


__host__ __device__ __half2 __hgt2(const __half2 a, const __half2 b)
Performs half2 vector greater-than comparison.
Performs half2 vector greater-than comparison of inputs a and b. The corresponding half results are set to 1.0 for true, or 0.0 for false. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The vector result of greater-than comparison of vectors a and b.


__host__ __device__ unsigned int __hgt2_mask(const __half2 a, const __half2 b)
Performs half2 vector greater-than comparison.
Performs half2 vector greater-than comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

unsigned int

The vector mask result of greater-than comparison of vectors a and b.


__host__ __device__ __half2 __hgtu2(const __half2 a, const __half2 b)
Performs half2 vector unordered greater-than comparison.
Performs half2 vector greater-than comparison of inputs a and b. The corresponding half results are set to 1.0 for true, or 0.0 for false. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The half2 vector result of unordered greater-than comparison of vectors a and b.


__host__ __device__ unsigned int __hgtu2_mask(const __half2 a, const __half2 b)
Performs half2 vector unordered greater-than comparison.
Performs half2 vector greater-than comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

unsigned int

The vector mask result of unordered greater-than comparison of vectors a and b.


__host__ __device__ __half2 __hisnan2(const __half2 a)
Determine whether half2 argument is a NaN.
Determine whether each half of input half2 number a is a NaN.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

The half2 with the corresponding half results set to 1.0 for NaN, 0.0 otherwise.


__host__ __device__ __half2 __hle2(const __half2 a, const __half2 b)
Performs half2 vector less-equal comparison.
Performs half2 vector less-equal comparison of inputs a and b. The corresponding half results are set to 1.0 for true, or 0.0 for false. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The half2 result of less-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hle2_mask(const __half2 a, const __half2 b)
Performs half2 vector less-equal comparison.
Performs half2 vector less-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

unsigned int

The vector mask result of less-equal comparison of vectors a and b.


__host__ __device__ __half2 __hleu2(const __half2 a, const __half2 b)
Performs half2 vector unordered less-equal comparison.
Performs half2 vector less-equal comparison of inputs a and b. The corresponding half results are set to 1.0 for true, or 0.0 for false. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The vector result of unordered less-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hleu2_mask(const __half2 a, const __half2 b)
Performs half2 vector unordered less-equal comparison.
Performs half2 vector less-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

unsigned int

The vector mask result of unordered less-equal comparison of vectors a and b.


__host__ __device__ __half2 __hlt2(const __half2 a, const __half2 b)
Performs half2 vector less-than comparison.
Performs half2 vector less-than comparison of inputs a and b. The corresponding half results are set to 1.0 for true, or 0.0 for false. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The half2 vector result of less-than comparison of vectors a and b.


__host__ __device__ unsigned int __hlt2_mask(const __half2 a, const __half2 b)
Performs half2 vector less-than comparison.
Performs half2 vector less-than comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

unsigned int

The vector mask result of less-than comparison of vectors a and b.


__host__ __device__ __half2 __hltu2(const __half2 a, const __half2 b)
Performs half2 vector unordered less-than comparison.
Performs half2 vector less-than comparison of inputs a and b. The corresponding half results are set to 1.0 for true, or 0.0 for false. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The vector result of unordered less-than comparison of vectors a and b.


__host__ __device__ unsigned int __hltu2_mask(const __half2 a, const __half2 b)
Performs half2 vector unordered less-than comparison.
Performs half2 vector less-than comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

unsigned int

The vector mask result of unordered less-than comparison of vectors a and b.


__host__ __device__ __half2 __hmax2(const __half2 a, const __half2 b)
Calculates half2 vector maximum of two inputs.
Calculates half2 vector max(a, b). Elementwise half operation is defined as (a > b) ? a : b.

If either of inputs is NaN, the other input is returned.
If both inputs are NaNs, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0
The result of elementwise maximum of vectors a and b

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2


__host__ __device__ __half2 __hmax2_nan(const __half2 a, const __half2 b)
Calculates half2 vector maximum of two inputs, NaNs pass through.
Calculates half2 vector max(a, b). Elementwise half operation is defined as (a > b) ? a : b.

If either of inputs is NaN, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0
The result of elementwise maximum of vectors a and b, with NaNs pass through

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2


__host__ __device__ __half2 __hmin2(const __half2 a, const __half2 b)
Calculates half2 vector minimum of two inputs.
Calculates half2 vector min(a, b). Elementwise half operation is defined as (a < b) ? a : b.

If either of inputs is NaN, the other input is returned.
If both inputs are NaNs, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0
The result of elementwise minimum of vectors a and b

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2


__host__ __device__ __half2 __hmin2_nan(const __half2 a, const __half2 b)
Calculates half2 vector minimum of two inputs, NaNs pass through.
Calculates half2 vector min(a, b). Elementwise half operation is defined as (a < b) ? a : b.

If either of inputs is NaN, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0
The result of elementwise minimum of vectors a and b, with NaNs pass through

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2


__host__ __device__ __half2 __hne2(const __half2 a, const __half2 b)
Performs half2 vector not-equal comparison.
Performs half2 vector not-equal comparison of inputs a and b. The corresponding half results are set to 1.0 for true, or 0.0 for false. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The vector result of not-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hne2_mask(const __half2 a, const __half2 b)
Performs half2 vector not-equal comparison.
Performs half2 vector not-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate false results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

unsigned int

The vector mask result of not-equal comparison of vectors a and b.


__host__ __device__ __half2 __hneu2(const __half2 a, const __half2 b)
Performs half2 vector unordered not-equal comparison.
Performs half2 vector not-equal comparison of inputs a and b. The corresponding half results are set to 1.0 for true, or 0.0 for false. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The vector result of unordered not-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hneu2_mask(const __half2 a, const __half2 b)
Performs half2 vector unordered not-equal comparison.
Performs half2 vector not-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate true results.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

unsigned int

The vector mask result of unordered not-equal comparison of vectors a and b.


__host__ __device__ bool operator!=(const __half2 &lh, const __half2 &rh)
Performs packed half unordered compare not-equal operation.

See also
__hbneu2(__half2, __half2)


__host__ __device__ bool operator<(const __half2 &lh, const __half2 &rh)
Performs packed half ordered less-than compare operation.

See also
__hblt2(__half2, __half2)


__host__ __device__ bool operator<=(const __half2 &lh, const __half2 &rh)
Performs packed half ordered less-or-equal compare operation.

See also
__hble2(__half2, __half2)


__host__ __device__ bool operator==(const __half2 &lh, const __half2 &rh)
Performs packed half ordered compare equal operation.

See also
__hbeq2(__half2, __half2)


__host__ __device__ bool operator>(const __half2 &lh, const __half2 &rh)
Performs packed half ordered greater-than compare operation.

See also
__hbgt2(__half2, __half2)


__host__ __device__ bool operator>=(const __half2 &lh, const __half2 &rh)
Performs packed half ordered greater-or-equal compare operation.

See also
__hbge2(__half2, __half2)