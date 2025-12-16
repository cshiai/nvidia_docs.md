# 5.6. Bfloat162 Arithmetic Functions


To use these functions, include the header file `cuda_bf16.h` in your program.


Functions


__host__ __device__ __nv_bfloat162 __h2div(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector division in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat162 __habs2(const __nv_bfloat162 a)
Calculates the absolute value of both halves of the input nv_bfloat162 number and returns the result.

__host__ __device__ __nv_bfloat162 __hadd2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector addition in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat162 __hadd2_rn(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector addition in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat162 __hadd2_sat(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector addition in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__device__ __nv_bfloat162 __hcmadd(const __nv_bfloat162 a, const __nv_bfloat162 b, const __nv_bfloat162 c)
Performs fast complex multiply-accumulate.

__device__ __nv_bfloat162 __hfma2(const __nv_bfloat162 a, const __nv_bfloat162 b, const __nv_bfloat162 c)
Performs nv_bfloat162 vector fused multiply-add in round-to-nearest-even mode.

__device__ __nv_bfloat162 __hfma2_relu(const __nv_bfloat162 a, const __nv_bfloat162 b, const __nv_bfloat162 c)
Performs nv_bfloat162 vector fused multiply-add in round-to-nearest-even mode with relu saturation.

__device__ __nv_bfloat162 __hfma2_sat(const __nv_bfloat162 a, const __nv_bfloat162 b, const __nv_bfloat162 c)
Performs nv_bfloat162 vector fused multiply-add in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__host__ __device__ __nv_bfloat162 __hmul2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector multiplication in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat162 __hmul2_rn(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector multiplication in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat162 __hmul2_sat(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector multiplication in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__host__ __device__ __nv_bfloat162 __hneg2(const __nv_bfloat162 a)
Negates both halves of the input nv_bfloat162 number and returns the result.

__host__ __device__ __nv_bfloat162 __hsub2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector subtraction in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat162 __hsub2_rn(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector subtraction in round-to-nearest-even mode.

__host__ __device__ __nv_bfloat162 __hsub2_sat(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector subtraction in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__device__ __nv_bfloat162 atomicAdd(__nv_bfloat162 *const address, const __nv_bfloat162 val)
Vector add val to the value stored at address in global or shared memory, and writes this value back to address .

__host__ __device__ __nv_bfloat162 operator*(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 multiplication operation.

__host__ __device__ __nv_bfloat162 & operator*=(__nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 compound assignment with multiplication operation.

__host__ __device__ __nv_bfloat162 operator+(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 addition operation.

__host__ __device__ __nv_bfloat162 operator+(const __nv_bfloat162 &h)
Implements packed nv_bfloat16 unary plus operator, returns input value.

__host__ __device__ __nv_bfloat162 operator++(__nv_bfloat162 &h, const int ignored)
Performs packed nv_bfloat16 postfix increment operation.

__host__ __device__ __nv_bfloat162 & operator++(__nv_bfloat162 &h)
Performs packed nv_bfloat16 prefix increment operation.

__host__ __device__ __nv_bfloat162 & operator+=(__nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 compound assignment with addition operation.

__host__ __device__ __nv_bfloat162 operator-(const __nv_bfloat162 &h)
Implements packed nv_bfloat16 unary minus operator.

__host__ __device__ __nv_bfloat162 operator-(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 subtraction operation.

__host__ __device__ __nv_bfloat162 operator–(__nv_bfloat162 &h, const int ignored)
Performs packed nv_bfloat16 postfix decrement operation.

__host__ __device__ __nv_bfloat162 & operator–(__nv_bfloat162 &h)
Performs packed nv_bfloat16 prefix decrement operation.

__host__ __device__ __nv_bfloat162 & operator-=(__nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 compound assignment with subtraction operation.

__host__ __device__ __nv_bfloat162 operator/(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 division operation.

__host__ __device__ __nv_bfloat162 & operator/=(__nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 compound assignment with division operation.


## 5.6.1. Functions


__host__ __device__ __nv_bfloat162 __h2div(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector division in round-to-nearest-even mode.
Divides nv_bfloat162 input vector a by input vector b in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The elementwise division of a with b.


__host__ __device__ __nv_bfloat162 __habs2(const __nv_bfloat162 a)
Calculates the absolute value of both halves of the input nv_bfloat162 number and returns the result.
Calculates the absolute value of both halves of the input nv_bfloat162 number and returns the result.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

bfloat2

Returns a with the absolute value of both halves.


__host__ __device__ __nv_bfloat162 __hadd2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector addition in round-to-nearest-even mode.
Performs nv_bfloat162 vector add of inputs a and b, in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The sum of vectors a and b.


__host__ __device__ __nv_bfloat162 __hadd2_rn(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector addition in round-to-nearest-even mode.
Performs nv_bfloat162 vector add of inputs a and b, in round-to-nearest-even mode. Prevents floating-point contractions of mul+add into fma.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The sum of vectors a and b.


__host__ __device__ __nv_bfloat162 __hadd2_sat(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector addition in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Performs nv_bfloat162 vector add of inputs a and b, in round-to-nearest-even mode, and clamps the results to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The sum of a and b, with respect to saturation.


__device__ __nv_bfloat162 __hcmadd(const __nv_bfloat162 a, const __nv_bfloat162 b, const __nv_bfloat162 c)
Performs fast complex multiply-accumulate.
Interprets vector nv_bfloat162 input pairs a, b, and c as complex numbers in nv_bfloat16 precision and performs complex multiply-accumulate operation: a*b + c

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.
c – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The result of complex multiply-accumulate operation on complex numbers a, b, and c


__device__ __nv_bfloat162 __hfma2(const __nv_bfloat162 a, const __nv_bfloat162 b, const __nv_bfloat162 c)
Performs nv_bfloat162 vector fused multiply-add in round-to-nearest-even mode.
Performs nv_bfloat162 vector multiply on inputs a and b, then performs a nv_bfloat162 vector add of the result with c, rounding the result once in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.
c – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The result of elementwise fused multiply-add operation on vectors a, b, and c.


__device__ __nv_bfloat162 __hfma2_relu(const __nv_bfloat162 a, const __nv_bfloat162 b, const __nv_bfloat162 c)
Performs nv_bfloat162 vector fused multiply-add in round-to-nearest-even mode with relu saturation.
Performs nv_bfloat162 vector multiply on inputs a and b, then performs a nv_bfloat162 vector add of the result with c, rounding the result once in round-to-nearest-even mode. Then negative result is clamped to 0. NaN result is converted to canonical NaN.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.
c – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The result of elementwise fused multiply-add operation on vectors a, b, and c with relu saturation.


__device__ __nv_bfloat162 __hfma2_sat(const __nv_bfloat162 a, const __nv_bfloat162 b, const __nv_bfloat162 c)
Performs nv_bfloat162 vector fused multiply-add in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Performs nv_bfloat162 vector multiply on inputs a and b, then performs a nv_bfloat162 vector add of the result with c, rounding the result once in round-to-nearest-even mode, and clamps the results to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.
c – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The result of elementwise fused multiply-add operation on vectors a, b, and c, with respect to saturation.


__host__ __device__ __nv_bfloat162 __hmul2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector multiplication in round-to-nearest-even mode.
Performs nv_bfloat162 vector multiplication of inputs a and b, in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The result of elementwise multiplying the vectors a and b.


__host__ __device__ __nv_bfloat162 __hmul2_rn(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector multiplication in round-to-nearest-even mode.
Performs nv_bfloat162 vector multiplication of inputs a and b, in round-to-nearest-even mode. Prevents floating-point contractions of mul+add or sub into fma.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The result of elementwise multiplying the vectors a and b.


__host__ __device__ __nv_bfloat162 __hmul2_sat(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector multiplication in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Performs nv_bfloat162 vector multiplication of inputs a and b, in round-to-nearest-even mode, and clamps the results to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The result of elementwise multiplication of vectors a and b, with respect to saturation.


__host__ __device__ __nv_bfloat162 __hneg2(const __nv_bfloat162 a)
Negates both halves of the input nv_bfloat162 number and returns the result.
Negates both halves of the input nv_bfloat162 number a and returns the result.

Parameters

a – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

Returns a with both halves negated.


__host__ __device__ __nv_bfloat162 __hsub2(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector subtraction in round-to-nearest-even mode.
Subtracts nv_bfloat162 input vector b from input vector a in round-to-nearest-even mode.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The subtraction of vector b from a.


__host__ __device__ __nv_bfloat162 __hsub2_rn(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector subtraction in round-to-nearest-even mode.
Subtracts nv_bfloat162 input vector b from input vector a in round-to-nearest-even mode. Prevents floating-point contractions of mul+sub into fma.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The subtraction of vector b from a.


__host__ __device__ __nv_bfloat162 __hsub2_sat(const __nv_bfloat162 a, const __nv_bfloat162 b)
Performs nv_bfloat162 vector subtraction in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Subtracts nv_bfloat162 input vector b from input vector a in round-to-nearest-even mode, and clamps the results to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - nv_bfloat162. Is only being read.
b – [in] - nv_bfloat162. Is only being read.

Returns

nv_bfloat162

The subtraction of vector b from a, with respect to saturation.


__device__ __nv_bfloat162 atomicAdd(__nv_bfloat162 *const address, const __nv_bfloat162 val)
Vector add val to the value stored at address in global or shared memory, and writes this value back to address.
The atomicity of the add operation is guaranteed separately for each of the two nv_bfloat16 elements; the entire __nv_bfloat162 is not guaranteed to be atomic as a single 32-bit access.
The location of address must be in global or shared memory. This operation has undefined behavior otherwise. This operation is natively supported by devices of compute capability 9.x and higher, older devices use emulation path.

Note
For more details about this function, see the Atomic Functions section in the CUDA C++ Programming Guide.

Parameters

address – [in] - __nv_bfloat162*. An address in global or shared memory.
val – [in] - __nv_bfloat162. The value to be added.

Returns

__nv_bfloat162

The old value read from address.


__host__ __device__ __nv_bfloat162 operator*(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 multiplication operation.
See also __hmul2(__nv_bfloat162, __nv_bfloat162)


__host__ __device__ __nv_bfloat162 &operator*=(__nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 compound assignment with multiplication operation.


__host__ __device__ __nv_bfloat162 operator+(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 addition operation.
See also __hadd2(__nv_bfloat162, __nv_bfloat162)


__host__ __device__ __nv_bfloat162 operator+(const __nv_bfloat162 &h)
Implements packed nv_bfloat16 unary plus operator, returns input value.


__host__ __device__ __nv_bfloat162 operator++(__nv_bfloat162 &h, const int ignored)
Performs packed nv_bfloat16 postfix increment operation.


__host__ __device__ __nv_bfloat162 &operator++(__nv_bfloat162 &h)
Performs packed nv_bfloat16 prefix increment operation.


__host__ __device__ __nv_bfloat162 &operator+=(__nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 compound assignment with addition operation.


__host__ __device__ __nv_bfloat162 operator-(const __nv_bfloat162 &h)
Implements packed nv_bfloat16 unary minus operator.
See also __hneg2(__nv_bfloat162)


__host__ __device__ __nv_bfloat162 operator-(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 subtraction operation.
See also __hsub2(__nv_bfloat162, __nv_bfloat162)


__host__ __device__ __nv_bfloat162 operator--(__nv_bfloat162 &h, const int ignored)
Performs packed nv_bfloat16 postfix decrement operation.


__host__ __device__ __nv_bfloat162 &operator--(__nv_bfloat162 &h)
Performs packed nv_bfloat16 prefix decrement operation.


__host__ __device__ __nv_bfloat162 &operator-=(__nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 compound assignment with subtraction operation.


__host__ __device__ __nv_bfloat162 operator/(const __nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 division operation.
See also __h2div(__nv_bfloat162, __nv_bfloat162)


__host__ __device__ __nv_bfloat162 &operator/=(__nv_bfloat162 &lh, const __nv_bfloat162 &rh)
Performs packed nv_bfloat16 compound assignment with division operation.