# 5.7. Bfloat162 Comparison Functions


To use these functions, include the header file `cuda_bf16.h` in your program.


Functions


__host__ __device__ bool __hbeq2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector if-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.

__host__ __device__ bool __hbequ2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered if-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.

__host__ __device__ bool __hbge2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector greater-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.

__host__ __device__ bool __hbgeu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered greater-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.

__host__ __device__ bool __hbgt2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector greater-than comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.

__host__ __device__ bool __hbgtu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered greater-than comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.

__host__ __device__ bool __hble2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector less-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.

__host__ __device__ bool __hbleu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered less-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.

__host__ __device__ bool __hblt2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector less-than comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.

__host__ __device__ bool __hbltu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered less-than comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.

__host__ __device__ bool __hbne2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector not-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.

__host__ __device__ bool __hbneu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered not-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.

__host__ __device__ __nv_bfloat162 __heq2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector if-equal comparison.

__host__ __device__ unsigned int __heq2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector if-equal comparison.

__host__ __device__ __nv_bfloat162 __hequ2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered if-equal comparison.

__host__ __device__ unsigned int __hequ2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered if-equal comparison.

__host__ __device__ __nv_bfloat162 __hge2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector greater-equal comparison.

__host__ __device__ unsigned int __hge2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector greater-equal comparison.

__host__ __device__ __nv_bfloat162 __hgeu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered greater-equal comparison.

__host__ __device__ unsigned int __hgeu2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered greater-equal comparison.

__host__ __device__ __nv_bfloat162 __hgt2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector greater-than comparison.

__host__ __device__ unsigned int __hgt2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector greater-than comparison.

__host__ __device__ __nv_bfloat162 __hgtu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered greater-than comparison.

__host__ __device__ unsigned int __hgtu2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered greater-than comparison.

__host__ __device__ __nv_bfloat162 __hisnan2(const __nv_bfloat162 a)
Determine whether nv_bfloat162 argument is a NaN.

__host__ __device__ __nv_bfloat162 __hle2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector less-equal comparison.

__host__ __device__ unsigned int __hle2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector less-equal comparison.

__host__ __device__ __nv_bfloat162 __hleu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered less-equal comparison.

__host__ __device__ unsigned int __hleu2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered less-equal comparison.

__host__ __device__ __nv_bfloat162 __hlt2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector less-than comparison.

__host__ __device__ unsigned int __hlt2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector less-than comparison.

__host__ __device__ __nv_bfloat162 __hltu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered less-than comparison.

__host__ __device__ unsigned int __hltu2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered less-than comparison.

__host__ __device__ __nv_bfloat162 __hmax2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Calculates nv_bfloat162 vector maximum of two inputs.

__host__ __device__ __nv_bfloat162 __hmax2_nan(const __nv_bfloat162 a, const __nv_bfloat162 b)
Calculates nv_bfloat162 vector maximum of two inputs, NaNs pass through.

__host__ __device__ __nv_bfloat162 __hmin2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Calculates nv_bfloat162 vector minimum of two inputs.

__host__ __device__ __nv_bfloat162 __hmin2_nan(const __nv_bfloat162 a, const __nv_bfloat162 b)
Calculates nv_bfloat162 vector minimum of two inputs, NaNs pass through.

__host__ __device__ __nv_bfloat162 __hne2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector not-equal comparison.

__host__ __device__ unsigned int __hne2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector not-equal comparison.

__host__ __device__ __nv_bfloat162 __hneu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered not-equal comparison.

__host__ __device__ unsigned int __hneu2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered not-equal comparison.

__host__ __device__ bool operator!=(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 unordered compare not-equal operation.

__host__ __device__ bool operator<(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 ordered less-than compare operation.

__host__ __device__ bool operator<=(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 ordered less-or-equal compare operation.

__host__ __device__ bool operator==(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 ordered compare equal operation.

__host__ __device__ bool operator>(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 ordered greater-than compare operation.

__host__ __device__ bool operator>=(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 ordered greater-or-equal compare operation.


## 5.7.1. Functions


__host__ __device__ bool __hbeq2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector if-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.
Performs nv_bfloat162 vector if-equal comparison of inputs a and b. The bool result is set to true only if both nv_bfloat16 if-equal comparisons evaluate to true, or false otherwise. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

bool

true if both nv_bfloat16 results of if-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbequ2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered if-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.
Performs nv_bfloat162 vector if-equal comparison of inputs a and b. The bool result is set to true only if both nv_bfloat16 if-equal comparisons evaluate to true, or false otherwise. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

bool

true if both nv_bfloat16 results of unordered if-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbge2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector greater-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.
Performs nv_bfloat162 vector greater-equal comparison of inputs a and b. The bool result is set to true only if both nv_bfloat16 greater-equal comparisons evaluate to true, or false otherwise. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

bool

true if both nv_bfloat16 results of greater-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbgeu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered greater-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.
Performs nv_bfloat162 vector greater-equal comparison of inputs a and b. The bool result is set to true only if both nv_bfloat16 greater-equal comparisons evaluate to true, or false otherwise. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

bool

true if both nv_bfloat16 results of unordered greater-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbgt2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector greater-than comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.
Performs nv_bfloat162 vector greater-than comparison of inputs a and b. The bool result is set to true only if both nv_bfloat16 greater-than comparisons evaluate to true, or false otherwise. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

bool

true if both nv_bfloat16 results of greater-than comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbgtu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered greater-than comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.
Performs nv_bfloat162 vector greater-than comparison of inputs a and b. The bool result is set to true only if both nv_bfloat16 greater-than comparisons evaluate to true, or false otherwise. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

bool

true if both nv_bfloat16 results of unordered greater-than comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hble2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector less-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.
Performs nv_bfloat162 vector less-equal comparison of inputs a and b. The bool result is set to true only if both nv_bfloat16 less-equal comparisons evaluate to true, or false otherwise. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

bool

true if both nv_bfloat16 results of less-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbleu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered less-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.
Performs nv_bfloat162 vector less-equal comparison of inputs a and b. The bool result is set to true only if both nv_bfloat16 less-equal comparisons evaluate to true, or false otherwise. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

bool

true if both nv_bfloat16 results of unordered less-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hblt2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector less-than comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.
Performs nv_bfloat162 vector less-than comparison of inputs a and b. The bool result is set to true only if both nv_bfloat16 less-than comparisons evaluate to true, or false otherwise. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

bool

true if both nv_bfloat16 results of less-than comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbltu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered less-than comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.
Performs nv_bfloat162 vector less-than comparison of inputs a and b. The bool result is set to true only if both nv_bfloat16 less-than comparisons evaluate to true, or false otherwise. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

bool

true if both nv_bfloat16 results of unordered less-than comparison of vectors a and b are true;
false otherwise.


__host__ __device__ bool __hbne2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector not-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.
Performs nv_bfloat162 vector not-equal comparison of inputs a and b. The bool result is set to true only if both nv_bfloat16 not-equal comparisons evaluate to true, or false otherwise. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

bool

true if both nv_bfloat16 results of not-equal comparison of vectors a and b are true,
false otherwise.


__host__ __device__ bool __hbneu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered not-equal comparison and returns boolean true if both nv_bfloat16 results are true, boolean false otherwise.
Performs nv_bfloat162 vector not-equal comparison of inputs a and b. The bool result is set to true only if both nv_bfloat16 not-equal comparisons evaluate to true, or false otherwise. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

bool

true if both nv_bfloat16 results of unordered not-equal comparison of vectors a and b are true;
false otherwise.


__host__ __device__ __nv_bfloat162 __heq2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector if-equal comparison.
Performs nv_bfloat162 vector if-equal comparison of inputs a and b. The corresponding nv_bfloat16 results are set to 1.0 for true, or 0.0 for false. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The vector result of if-equal comparison of vectors a and b.


__host__ __device__ unsigned int __heq2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector if-equal comparison.
Performs nv_bfloat162 vector if-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

unsigned int

The vector mask result of if-equal comparison of vectors a and b.


__host__ __device__ __nv_bfloat162 __hequ2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered if-equal comparison.
Performs nv_bfloat162 vector if-equal comparison of inputs a and b. The corresponding nv_bfloat16 results are set to 1.0 for true, or 0.0 for false. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The vector result of unordered if-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hequ2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered if-equal comparison.
Performs nv_bfloat162 vector if-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

unsigned int

The vector mask result of unordered if-equal comparison of vectors a and b.


__host__ __device__ __nv_bfloat162 __hge2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector greater-equal comparison.
Performs nv_bfloat162 vector greater-equal comparison of inputs a and b. The corresponding nv_bfloat16 results are set to 1.0 for true, or 0.0 for false. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The vector result of greater-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hge2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector greater-equal comparison.
Performs nv_bfloat162 vector greater-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

unsigned int

The vector mask result of greater-equal comparison of vectors a and b.


__host__ __device__ __nv_bfloat162 __hgeu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered greater-equal comparison.
Performs nv_bfloat162 vector greater-equal comparison of inputs a and b. The corresponding nv_bfloat16 results are set to 1.0 for true, or 0.0 for false. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The nv_bfloat162 vector result of unordered greater-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hgeu2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered greater-equal comparison.
Performs nv_bfloat162 vector greater-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

unsigned int

The vector mask result of unordered greater-equal comparison of vectors a and b.


__host__ __device__ __nv_bfloat162 __hgt2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector greater-than comparison.
Performs nv_bfloat162 vector greater-than comparison of inputs a and b. The corresponding nv_bfloat16 results are set to 1.0 for true, or 0.0 for false. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The vector result of greater-than comparison of vectors a and b.


__host__ __device__ unsigned int __hgt2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector greater-than comparison.
Performs nv_bfloat162 vector greater-than comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

unsigned int

The vector mask result of greater-than comparison of vectors a and b.


__host__ __device__ __nv_bfloat162 __hgtu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered greater-than comparison.
Performs nv_bfloat162 vector greater-than comparison of inputs a and b. The corresponding nv_bfloat16 results are set to 1.0 for true, or 0.0 for false. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The nv_bfloat162 vector result of unordered greater-than comparison of vectors a and b.


__host__ __device__ unsigned int __hgtu2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered greater-than comparison.
Performs nv_bfloat162 vector greater-than comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

unsigned int

The vector mask result of unordered greater-than comparison of vectors a and b.


__host__ __device__ __nv_bfloat162 __hisnan2(const __nv_bfloat162 a)
Determine whether nv_bfloat162 argument is a NaN.
Determine whether each nv_bfloat16 of input nv_bfloat162 number a is a NaN.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The nv_bfloat162 with the corresponding nv_bfloat16 results set to 1.0 for NaN, 0.0 otherwise.


__host__ __device__ __nv_bfloat162 __hle2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector less-equal comparison.
Performs nv_bfloat162 vector less-equal comparison of inputs a and b. The corresponding nv_bfloat16 results are set to 1.0 for true, or 0.0 for false. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The nv_bfloat162 result of less-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hle2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector less-equal comparison.
Performs nv_bfloat162 vector less-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

unsigned int

The vector mask result of less-equal comparison of vectors a and b.


__host__ __device__ __nv_bfloat162 __hleu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered less-equal comparison.
Performs nv_bfloat162 vector less-equal comparison of inputs a and b. The corresponding nv_bfloat16 results are set to 1.0 for true, or 0.0 for false. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The vector result of unordered less-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hleu2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered less-equal comparison.
Performs nv_bfloat162 vector less-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

unsigned int

The vector mask result of unordered less-equal comparison of vectors a and b.


__host__ __device__ __nv_bfloat162 __hlt2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector less-than comparison.
Performs nv_bfloat162 vector less-than comparison of inputs a and b. The corresponding nv_bfloat16 results are set to 1.0 for true, or 0.0 for false. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The nv_bfloat162 vector result of less-than comparison of vectors a and b.


__host__ __device__ unsigned int __hlt2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector less-than comparison.
Performs nv_bfloat162 vector less-than comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

unsigned int

The vector mask result of less-than comparison of vectors a and b.


__host__ __device__ __nv_bfloat162 __hltu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered less-than comparison.
Performs nv_bfloat162 vector less-than comparison of inputs a and b. The corresponding nv_bfloat16 results are set to 1.0 for true, or 0.0 for false. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The vector result of unordered less-than comparison of vectors a and b.


__host__ __device__ unsigned int __hltu2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered less-than comparison.
Performs nv_bfloat162 vector less-than comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

unsigned int

The vector mask result of unordered less-than comparison of vectors a and b.


__host__ __device__ __nv_bfloat162 __hmax2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Calculates nv_bfloat162 vector maximum of two inputs.
Calculates nv_bfloat162 vector max(a, b). Elementwise nv_bfloat16 operation is defined as (a > b) ? a : b.

If either of inputs is NaN, the other input is returned.
If both inputs are NaNs, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0
The result of elementwise maximum of vectors a and b

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162


__host__ __device__ __nv_bfloat162 __hmax2_nan(const __nv_bfloat162 a, const __nv_bfloat162 b)
Calculates nv_bfloat162 vector maximum of two inputs, NaNs pass through.
Calculates nv_bfloat162 vector max(a, b). Elementwise nv_bfloat16 operation is defined as (a > b) ? a : b.

If either of inputs is NaN, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0
The result of elementwise maximum of vectors a and b, with NaNs pass through

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162


__host__ __device__ __nv_bfloat162 __hmin2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Calculates nv_bfloat162 vector minimum of two inputs.
Calculates nv_bfloat162 vector min(a, b). Elementwise nv_bfloat16 operation is defined as (a < b) ? a : b.

If either of inputs is NaN, the other input is returned.
If both inputs are NaNs, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0
The result of elementwise minimum of vectors a and b

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162


__host__ __device__ __nv_bfloat162 __hmin2_nan(const __nv_bfloat162 a, const __nv_bfloat162 b)
Calculates nv_bfloat162 vector minimum of two inputs, NaNs pass through.
Calculates nv_bfloat162 vector min(a, b). Elementwise nv_bfloat16 operation is defined as (a < b) ? a : b.

If either of inputs is NaN, then canonical NaN is returned.
If values of both inputs are 0.0, then +0.0 > -0.0
The result of elementwise minimum of vectors a and b, with NaNs pass through

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162


__host__ __device__ __nv_bfloat162 __hne2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector not-equal comparison.
Performs nv_bfloat162 vector not-equal comparison of inputs a and b. The corresponding nv_bfloat16 results are set to 1.0 for true, or 0.0 for false. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The vector result of not-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hne2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector not-equal comparison.
Performs nv_bfloat162 vector not-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate false results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

unsigned int

The vector mask result of not-equal comparison of vectors a and b.


__host__ __device__ __nv_bfloat162 __hneu2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered not-equal comparison.
Performs nv_bfloat162 vector not-equal comparison of inputs a and b. The corresponding nv_bfloat16 results are set to 1.0 for true, or 0.0 for false. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The vector result of unordered not-equal comparison of vectors a and b.


__host__ __device__ unsigned int __hneu2_mask(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector unordered not-equal comparison.
Performs nv_bfloat162 vector not-equal comparison of inputs a and b. The corresponding unsigned bits are set to 0xFFFF for true, or 0x0 for false. NaN inputs generate true results.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

unsigned int

The vector mask result of unordered not-equal comparison of vectors a and b.


__host__ __device__ bool operator!=(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 unordered compare not-equal operation.
See also __hbneu2(__nv_bfloat162, __nv_bfloat162)


__host__ __device__ bool operator<(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 ordered less-than compare operation.
See also __hblt2(__nv_bfloat162, __nv_bfloat162)


__host__ __device__ bool operator<=(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 ordered less-or-equal compare operation.
See also __hble2(__nv_bfloat162, __nv_bfloat162)


__host__ __device__ bool operator==(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 ordered compare equal operation.
See also __hbeq2(__nv_bfloat162, __nv_bfloat162)


__host__ __device__ bool operator>(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 ordered greater-than compare operation.
See also __hbgt2(__nv_bfloat162, __nv_bfloat162)


__host__ __device__ bool operator>=(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 ordered greater-or-equal compare operation.
See also __hbge2(__nv_bfloat162, __nv_bfloat162)