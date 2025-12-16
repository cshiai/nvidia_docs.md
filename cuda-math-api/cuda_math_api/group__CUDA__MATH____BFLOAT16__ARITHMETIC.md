# 5.2. Bfloat16 Arithmetic Functions


To use these functions, include the header file `cuda_bf16.h` in your program.


Functions


__host__ __device__ __nv_bfloat16 __habs(const __nv_bfloat16 a)
Calculates the absolute value of input nv_bfloat16 number and returns the result.

__host__ __device__ __nv_bfloat16 __hadd(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 addition in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat16 __hadd_rn(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 addition in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat16 __hadd_sat(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 addition in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__host__ __device__ __nv_bfloat16 __hdiv(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 division in round-to-nearest-even mode.

__device__ __nv_bfloat16 __hfma(const __nv_bfloat16 a, const __nv_bfloat16 b, const __nv_bfloat16 c)
Performs nv_bfloat16 fused multiply-add in round-to-nearest-even mode.

__device__ __nv_bfloat16 __hfma_relu(const __nv_bfloat16 a, const __nv_bfloat16 b, const __nv_bfloat16 c)
Performs nv_bfloat16 fused multiply-add in round-to-nearest-even mode with relu saturation.

__device__ __nv_bfloat16 __hfma_sat(const __nv_bfloat16 a, const __nv_bfloat16 b, const __nv_bfloat16 c)
Performs nv_bfloat16 fused multiply-add in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__host__ __device__ __nv_bfloat16 __hmul(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 multiplication in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat16 __hmul_rn(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 multiplication in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat16 __hmul_sat(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 multiplication in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__host__ __device__ __nv_bfloat16 __hneg(const __nv_bfloat16 a)
Negates input nv_bfloat16 number and returns the result.

__host__ __device__ __nv_bfloat16 __hsub(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 subtraction in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat16 __hsub_rn(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 subtraction in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat16 __hsub_sat(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 subtraction in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__device__ __nv_bfloat16 atomicAdd(__nv_bfloat16 *const address, const __nv_bfloat16 val)
Adds val to the value stored at address in global or shared memory, and writes this value back to address .

__host__ __device__ __nv_bfloat16 operator*(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 multiplication operation.

__host__ __device__ __nv_bfloat16 & operator*=(__nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 compound assignment with multiplication operation.

__host__ __device__ __nv_bfloat16 operator+(const __nv_bfloat16 &h)
Implements nv_bfloat16 unary plus operator, returns input value.

__host__ __device__ __nv_bfloat16 operator+(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 addition operation.

__host__ __device__ __nv_bfloat16 operator++(__nv_bfloat16 &h, const int ignored)
Performs nv_bfloat16 postfix increment operation.

__host__ __device__ __nv_bfloat16 & operator++(__nv_bfloat16 &h)
Performs nv_bfloat16 prefix increment operation.

__host__ __device__ __nv_bfloat16 & operator+=(__nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 compound assignment with addition operation.

__host__ __device__ __nv_bfloat16 operator-(const __nv_bfloat16 &h)
Implements nv_bfloat16 unary minus operator.

__host__ __device__ __nv_bfloat16 operator-(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 subtraction operation.

__host__ __device__ __nv_bfloat16 & operator–(__nv_bfloat16 &h)
Performs nv_bfloat16 prefix decrement operation.

__host__ __device__ __nv_bfloat16 operator–(__nv_bfloat16 &h, const int ignored)
Performs nv_bfloat16 postfix decrement operation.

__host__ __device__ __nv_bfloat16 & operator-=(__nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 compound assignment with subtraction operation.

__host__ __device__ __nv_bfloat16 operator/(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 division operation.

__host__ __device__ __nv_bfloat16 & operator/=(__nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 compound assignment with division operation.


## 5.2.1. Functions


__host__ __device__ __nv_bfloat16 __habs(const __nv_bfloat16 a)
Calculates the absolute value of input nv_bfloat16 number and returns the result.
Calculates the absolute value of input nv_bfloat16 number and returns the result.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The absolute value of a.


__host__ __device__ __nv_bfloat16 __hadd(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 addition in round-to-nearest-even mode.
Performs nv_bfloat16 addition of inputs a and b, in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The sum of a and b.


__host__ __device__ __nv_bfloat16 __hadd_rn(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 addition in round-to-nearest-even mode.
Performs nv_bfloat16 addition of inputs a and b, in round-to-nearest-even mode. Prevents floating-point contractions of mul+add into fma.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The sum of a and b.


__host__ __device__ __nv_bfloat16 __hadd_sat(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 addition in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Performs nv_bfloat16 add of inputs a and b, in round-to-nearest-even mode, and clamps the result to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The sum of a and b, with respect to saturation.


__host__ __device__ __nv_bfloat16 __hdiv(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 division in round-to-nearest-even mode.
Divides nv_bfloat16 input a by input b in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The result of dividing a by b.


__device__ __nv_bfloat16 __hfma(const __nv_bfloat16 a, const __nv_bfloat16 b, const __nv_bfloat16 c)
Performs nv_bfloat16 fused multiply-add in round-to-nearest-even mode.
Performs nv_bfloat16 multiply on inputs a and b, then performs a nv_bfloat16 add of the result with c, rounding the result once in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.
c – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The result of fused multiply-add operation on a, b, and c.


__device__ __nv_bfloat16 __hfma_relu(const __nv_bfloat16 a, const __nv_bfloat16 b, const __nv_bfloat16 c)
Performs nv_bfloat16 fused multiply-add in round-to-nearest-even mode with relu saturation.
Performs nv_bfloat16 multiply on inputs a and b, then performs a nv_bfloat16 add of the result with c, rounding the result once in round-to-nearest-even mode. Then negative result is clamped to 0. NaN result is converted to canonical NaN.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.
c – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The result of fused multiply-add operation on a, b, and c with relu saturation.


__device__ __nv_bfloat16 __hfma_sat(const __nv_bfloat16 a, const __nv_bfloat16 b, const __nv_bfloat16 c)
Performs nv_bfloat16 fused multiply-add in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Performs nv_bfloat16 multiply on inputs a and b, then performs a nv_bfloat16 add of the result with c, rounding the result once in round-to-nearest-even mode, and clamps the result to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.
c – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The result of fused multiply-add operation on a, b, and c, with respect to saturation.


__host__ __device__ __nv_bfloat16 __hmul(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 multiplication in round-to-nearest-even mode.
Performs nv_bfloat16 multiplication of inputs a and b, in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The result of multiplying a and b.


__host__ __device__ __nv_bfloat16 __hmul_rn(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 multiplication in round-to-nearest-even mode.
Performs nv_bfloat16 multiplication of inputs a and b, in round-to-nearest-even mode. Prevents floating-point contractions of mul+add or sub into fma.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The result of multiplying a and b.


__host__ __device__ __nv_bfloat16 __hmul_sat(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 multiplication in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Performs nv_bfloat16 multiplication of inputs a and b, in round-to-nearest-even mode, and clamps the result to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The result of multiplying a and b, with respect to saturation.


__host__ __device__ __nv_bfloat16 __hneg(const __nv_bfloat16 a)
Negates input nv_bfloat16 number and returns the result.
Negates input nv_bfloat16 number and returns the result.

Parameters

a – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

minus a


__host__ __device__ __nv_bfloat16 __hsub(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 subtraction in round-to-nearest-even mode.
Subtracts nv_bfloat16 input b from input a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The result of subtracting b from a.


__host__ __device__ __nv_bfloat16 __hsub_rn(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 subtraction in round-to-nearest-even mode.
Subtracts nv_bfloat16 input b from input a in round-to-nearest-even mode. Prevents floating-point contractions of mul+sub into fma.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The result of subtracting b from a.


__host__ __device__ __nv_bfloat16 __hsub_sat(const __nv_bfloat16 a, const __nv_bfloat16 b)
Performs nv_bfloat16 subtraction in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Subtracts nv_bfloat16 input b from input a in round-to-nearest-even mode, and clamps the result to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - nv_bfloat16. Is only being read.
b – [in] - nv_bfloat16. Is only being read.

Returns

nv_bfloat16

The result of subtraction of b from a, with respect to saturation.


__device__ __nv_bfloat16 atomicAdd(__nv_bfloat16 *const address, const __nv_bfloat16 val)
Adds val to the value stored at address in global or shared memory, and writes this value back to address.
This operation is performed in one atomic operation.
The location of address must be in global or shared memory. This operation has undefined behavior otherwise. This operation is natively supported by devices of compute capability 9.x and higher, older devices of compute capability 7.x and 8.x use emulation path.

Note
For more details about this function, see the Atomic Functions section in the CUDA C++ Programming Guide.

Parameters

address – [in] - __nv_bfloat16*. An address in global or shared memory.
val – [in] - __nv_bfloat16. The value to be added.

Returns

__nv_bfloat16

The old value read from address.


__host__ __device__ __nv_bfloat16 operator*(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 multiplication operation.
See also __hmul(__nv_bfloat16, __nv_bfloat16)


__host__ __device__ __nv_bfloat16 &operator*=(__nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 compound assignment with multiplication operation.


__host__ __device__ __nv_bfloat16 operator+(const __nv_bfloat16 &h)
Implements nv_bfloat16 unary plus operator, returns input value.


__host__ __device__ __nv_bfloat16 operator+(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 addition operation.
See also __hadd(__nv_bfloat16, __nv_bfloat16)


__host__ __device__ __nv_bfloat16 operator++(__nv_bfloat16 &h, const int ignored)
Performs nv_bfloat16 postfix increment operation.


__host__ __device__ __nv_bfloat16 &operator++(__nv_bfloat16 &h)
Performs nv_bfloat16 prefix increment operation.


__host__ __device__ __nv_bfloat16 &operator+=(__nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 compound assignment with addition operation.


__host__ __device__ __nv_bfloat16 operator-(const __nv_bfloat16 &h)
Implements nv_bfloat16 unary minus operator.
See also __hneg(__nv_bfloat16)


__host__ __device__ __nv_bfloat16 operator-(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 subtraction operation.
See also __hsub(__nv_bfloat16, __nv_bfloat16)


__host__ __device__ __nv_bfloat16 &operator--(__nv_bfloat16 &h)
Performs nv_bfloat16 prefix decrement operation.


__host__ __device__ __nv_bfloat16 operator--(__nv_bfloat16 &h, const int ignored)
Performs nv_bfloat16 postfix decrement operation.


__host__ __device__ __nv_bfloat16 &operator-=(__nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 compound assignment with subtraction operation.


__host__ __device__ __nv_bfloat16 operator/(const __nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 division operation.
See also __hdiv(__nv_bfloat16, __nv_bfloat16)


__host__ __device__ __nv_bfloat16 &operator/=(__nv_bfloat16 &lh, const __nv_bfloat16 &rh)
Performs nv_bfloat16 compound assignment with division operation.