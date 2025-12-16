# 4.2. Half Arithmetic Functions


To use these functions, include the header file `cuda_fp16.h` in your program.


Functions


__host__ __device__ __half __habs(const __half a)
Calculates the absolute value of input half number and returns the result.

__host__ __device__ __half __hadd(const __half a, const __half b)
Performs half addition in round-to-nearest-even mode.

__host__ __device__ __half __hadd_rn(const __half a, const __half b)
Performs half addition in round-to-nearest-even mode.

__host__ __device__ __half __hadd_sat(const __half a, const __half b)
Performs half addition in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__host__ __device__ __half __hdiv(const __half a, const __half b)
Performs half division in round-to-nearest-even mode.

__device__ __half __hfma(const __half a, const __half b, const __half c)
Performs half fused multiply-add in round-to-nearest-even mode.

__device__ __half __hfma_relu(const __half a, const __half b, const __half c)
Performs half fused multiply-add in round-to-nearest-even mode with relu saturation.

__device__ __half __hfma_sat(const __half a, const __half b, const __half c)
Performs half fused multiply-add in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__host__ __device__ __half __hmul(const __half a, const __half b)
Performs half multiplication in round-to-nearest-even mode.

__host__ __device__ __half __hmul_rn(const __half a, const __half b)
Performs half multiplication in round-to-nearest-even mode.

__host__ __device__ __half __hmul_sat(const __half a, const __half b)
Performs half multiplication in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__host__ __device__ __half __hneg(const __half a)
Negates input half number and returns the result.

__host__ __device__ __half __hsub(const __half a, const __half b)
Performs half subtraction in round-to-nearest-even mode.

__host__ __device__ __half __hsub_rn(const __half a, const __half b)
Performs half subtraction in round-to-nearest-even mode.

__host__ __device__ __half __hsub_sat(const __half a, const __half b)
Performs half subtraction in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__device__ __half atomicAdd(__half *const address, const __half val)
Adds val to the value stored at address in global or shared memory, and writes this value back to address .

__host__ __device__ __half operator*(const __half &lh, const __half &rh)
Performs half multiplication operation.

__host__ __device__ __half & operator*=(__half &lh, const __half &rh)
Performs half compound assignment with multiplication operation.

__host__ __device__ __half operator+(const __half &h)
Implements half unary plus operator, returns input value.

__host__ __device__ __half operator+(const __half &lh, const __half &rh)
Performs half addition operation.

__host__ __device__ __half & operator++(__half &h)
Performs half prefix increment operation.

__host__ __device__ __half operator++(__half &h, const int ignored)
Performs half postfix increment operation.

__host__ __device__ __half & operator+=(__half &lh, const __half &rh)
Performs half compound assignment with addition operation.

__host__ __device__ __half operator-(const __half &lh, const __half &rh)
Performs half subtraction operation.

__host__ __device__ __half operator-(const __half &h)
Implements half unary minus operator.

__host__ __device__ __half operator–(__half &h, const int ignored)
Performs half postfix decrement operation.

__host__ __device__ __half & operator–(__half &h)
Performs half prefix decrement operation.

__host__ __device__ __half & operator-=(__half &lh, const __half &rh)
Performs half compound assignment with subtraction operation.

__host__ __device__ __half operator/(const __half &lh, const __half &rh)
Performs half division operation.

__host__ __device__ __half & operator/=(__half &lh, const __half &rh)
Performs half compound assignment with division operation.


## 4.2.1. Functions


__host__ __device__ __half __habs(const __half a)
Calculates the absolute value of input half number and returns the result.
Calculates the absolute value of input half number and returns the result.

Parameters

a – [in] - half. Is only being read.

Returns

half

The absolute value of a.
__habs \( (\pm 0)\) returns +0.
__habs \( (\pm \infty)\) returns \( +\infty \).
__habs(NaN) returns NaN.


__host__ __device__ __half __hadd(const __half a, const __half b)
Performs half addition in round-to-nearest-even mode.
Performs half addition of inputs a and b, in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half

The sum of a and b.


__host__ __device__ __half __hadd_rn(const __half a, const __half b)
Performs half addition in round-to-nearest-even mode.
Performs half addition of inputs a and b, in round-to-nearest-even mode. Prevents floating-point contractions of mul+add into fma.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half

The sum of a and b.


__host__ __device__ __half __hadd_sat(const __half a, const __half b)
Performs half addition in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Performs half add of inputs a and b, in round-to-nearest-even mode, and clamps the result to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half

The sum of a and b, with respect to saturation.


__host__ __device__ __half __hdiv(const __half a, const __half b)
Performs half division in round-to-nearest-even mode.
Divides half input a by input b in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half

The result of dividing a by b.


__device__ __half __hfma(const __half a, const __half b, const __half c)
Performs half fused multiply-add in round-to-nearest-even mode.
Performs half multiply on inputs a and b, then performs a half add of the result with c, rounding the result once in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.
c – [in] - half. Is only being read.

Returns

half

The result of fused multiply-add operation on a, b, and c.


__device__ __half __hfma_relu(const __half a, const __half b, const __half c)
Performs half fused multiply-add in round-to-nearest-even mode with relu saturation.
Performs half multiply on inputs a and b, then performs a half add of the result with c, rounding the result once in round-to-nearest-even mode. Then negative result is clamped to 0. NaN result is converted to canonical NaN.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.
c – [in] - half. Is only being read.

Returns

half

The result of fused multiply-add operation on a, b, and c with relu saturation.


__device__ __half __hfma_sat(const __half a, const __half b, const __half c)
Performs half fused multiply-add in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Performs half multiply on inputs a and b, then performs a half add of the result with c, rounding the result once in round-to-nearest-even mode, and clamps the result to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.
c – [in] - half. Is only being read.

Returns

half

The result of fused multiply-add operation on a, b, and c, with respect to saturation.


__host__ __device__ __half __hmul(const __half a, const __half b)
Performs half multiplication in round-to-nearest-even mode.
Performs half multiplication of inputs a and b, in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half

The result of multiplying a and b.


__host__ __device__ __half __hmul_rn(const __half a, const __half b)
Performs half multiplication in round-to-nearest-even mode.
Performs half multiplication of inputs a and b, in round-to-nearest-even mode. Prevents floating-point contractions of mul+add or sub into fma.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half

The result of multiplying a and b.


__host__ __device__ __half __hmul_sat(const __half a, const __half b)
Performs half multiplication in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Performs half multiplication of inputs a and b, in round-to-nearest-even mode, and clamps the result to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half

The result of multiplying a and b, with respect to saturation.


__host__ __device__ __half __hneg(const __half a)
Negates input half number and returns the result.
Negates input half number and returns the result.

Parameters

a – [in] - half. Is only being read.

Returns

half

Negated input a.
__hneg \( (\pm 0)\) returns \( \mp 0 \).
__hneg \( (\pm \infty)\) returns \( \mp \infty \).
__hneg(NaN) returns NaN.


__host__ __device__ __half __hsub(const __half a, const __half b)
Performs half subtraction in round-to-nearest-even mode.
Subtracts half input b from input a in round-to-nearest-even mode.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half

The result of subtracting b from a.


__host__ __device__ __half __hsub_rn(const __half a, const __half b)
Performs half subtraction in round-to-nearest-even mode.
Subtracts half input b from input a in round-to-nearest-even mode. Prevents floating-point contractions of mul+sub into fma.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half

The result of subtracting b from a.


__host__ __device__ __half __hsub_sat(const __half a, const __half b)
Performs half subtraction in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Subtracts half input b from input a in round-to-nearest-even mode, and clamps the result to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - half. Is only being read.
b – [in] - half. Is only being read.

Returns

half

The result of subtraction of b from a, with respect to saturation.


__device__ __half atomicAdd(__half *const address, const __half val)
Adds val to the value stored at address in global or shared memory, and writes this value back to address.
This operation is performed in one atomic operation.
The location of address must be in global or shared memory. This operation has undefined behavior otherwise. This operation is only supported by devices of compute capability 7.x and higher.

Note
For more details about this function, see the Atomic Functions section in the CUDA C++ Programming Guide.

Parameters

address – [in] - half*. An address in global or shared memory.
val – [in] - half. The value to be added.

Returns

half

The old value read from address.


__host__ __device__ __half operator*(const __half &lh, const __half &rh)
Performs half multiplication operation.

See also
__hmul(__half, __half)


__host__ __device__ __half &operator*=(__half &lh, const __half &rh)
Performs half compound assignment with multiplication operation.

See also
__hmul(__half, __half)


__host__ __device__ __half operator+(const __half &h)
Implements half unary plus operator, returns input value.


__host__ __device__ __half operator+(const __half &lh, const __half &rh)
Performs half addition operation.

See also
__hadd(__half, __half)


__host__ __device__ __half &operator++(__half &h)
Performs half prefix increment operation.

See also
__hadd(__half, __half)


__host__ __device__ __half operator++(__half &h, const int ignored)
Performs half postfix increment operation.

See also
__hadd(__half, __half)


__host__ __device__ __half &operator+=(__half &lh, const __half &rh)
Performs half compound assignment with addition operation.

See also
__hadd(__half, __half)


__host__ __device__ __half operator-(const __half &lh, const __half &rh)
Performs half subtraction operation.

See also
__hsub(__half, __half)


__host__ __device__ __half operator-(const __half &h)
Implements half unary minus operator.

See also
__hneg(__half)


__host__ __device__ __half operator--(__half &h, const int ignored)
Performs half postfix decrement operation.

See also
__hsub(__half, __half)


__host__ __device__ __half &operator--(__half &h)
Performs half prefix decrement operation.

See also
__hsub(__half, __half)


__host__ __device__ __half &operator-=(__half &lh, const __half &rh)
Performs half compound assignment with subtraction operation.

See also
__hsub(__half, __half)


__host__ __device__ __half operator/(const __half &lh, const __half &rh)
Performs half division operation.

See also
__hdiv(__half, __half)


__host__ __device__ __half &operator/=(__half &lh, const __half &rh)
Performs half compound assignment with division operation.

See also
__hdiv(__half, __half)