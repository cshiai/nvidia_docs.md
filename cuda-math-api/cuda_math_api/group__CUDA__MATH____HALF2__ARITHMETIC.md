# 4.6. Half2 Arithmetic Functions


To use these functions, include the header file `cuda_fp16.h` in your program.


Functions


__host__ __device__ __half2 __h2div(const __half2 a, const __half2 b)
Performs half2 vector division in round-to-nearest-even mode.

__host__ __device__ __half2 __habs2(const __half2 a)
Calculates the absolute value of both halves of the input half2 number and returns the result.

__host__ __device__ __half2 __hadd2(const __half2 a, const __half2 b)
Performs half2 vector addition in round-to-nearest-even mode.

__host__ __device__ __half2 __hadd2_rn(const __half2 a, const __half2 b)
Performs half2 vector addition in round-to-nearest-even mode.

__host__ __device__ __half2 __hadd2_sat(const __half2 a, const __half2 b)
Performs half2 vector addition in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__device__ __half2 __hcmadd(const __half2 a, const __half2 b, const __half2 c)
Performs fast complex multiply-accumulate.

__device__ __half2 __hfma2(const __half2 a, const __half2 b, const __half2 c)
Performs half2 vector fused multiply-add in round-to-nearest-even mode.

__device__ __half2 __hfma2_relu(const __half2 a, const __half2 b, const __half2 c)
Performs half2 vector fused multiply-add in round-to-nearest-even mode with relu saturation.

__device__ __half2 __hfma2_sat(const __half2 a, const __half2 b, const __half2 c)
Performs half2 vector fused multiply-add in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__host__ __device__ __half2 __hmul2(const __half2 a, const __half2 b)
Performs half2 vector multiplication in round-to-nearest-even mode.

__host__ __device__ __half2 __hmul2_rn(const __half2 a, const __half2 b)
Performs half2 vector multiplication in round-to-nearest-even mode.

__host__ __device__ __half2 __hmul2_sat(const __half2 a, const __half2 b)
Performs half2 vector multiplication in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__host__ __device__ __half2 __hneg2(const __half2 a)
Negates both halves of the input half2 number and returns the result.

__host__ __device__ __half2 __hsub2(const __half2 a, const __half2 b)
Performs half2 vector subtraction in round-to-nearest-even mode.

__host__ __device__ __half2 __hsub2_rn(const __half2 a, const __half2 b)
Performs half2 vector subtraction in round-to-nearest-even mode.

__host__ __device__ __half2 __hsub2_sat(const __half2 a, const __half2 b)
Performs half2 vector subtraction in round-to-nearest-even mode, with saturation to [0.0, 1.0].

__device__ __half2 atomicAdd(__half2 *const address, const __half2 val)
Vector add val to the value stored at address in global or shared memory, and writes this value back to address .

__host__ __device__ __half2 operator*(const __half2 &lh, const __half2 &rh)
Performs packed half multiplication operation.

__host__ __device__ __half2 & operator*=(__half2 &lh, const __half2 &rh)
Performs packed half compound assignment with multiplication operation.

__host__ __device__ __half2 operator+(const __half2 &h)
Implements packed half unary plus operator, returns input value.

__host__ __device__ __half2 operator+(const __half2 &lh, const __half2 &rh)
Performs packed half addition operation.

__host__ __device__ __half2 operator++(__half2 &h, const int ignored)
Performs packed half postfix increment operation.

__host__ __device__ __half2 & operator++(__half2 &h)
Performs packed half prefix increment operation.

__host__ __device__ __half2 & operator+=(__half2 &lh, const __half2 &rh)
Performs packed half compound assignment with addition operation.

__host__ __device__ __half2 operator-(const __half2 &h)
Implements packed half unary minus operator.

__host__ __device__ __half2 operator-(const __half2 &lh, const __half2 &rh)
Performs packed half subtraction operation.

__host__ __device__ __half2 & operator–(__half2 &h)
Performs packed half prefix decrement operation.

__host__ __device__ __half2 operator–(__half2 &h, const int ignored)
Performs packed half postfix decrement operation.

__host__ __device__ __half2 & operator-=(__half2 &lh, const __half2 &rh)
Performs packed half compound assignment with subtraction operation.

__host__ __device__ __half2 operator/(const __half2 &lh, const __half2 &rh)
Performs packed half division operation.

__host__ __device__ __half2 & operator/=(__half2 &lh, const __half2 &rh)
Performs packed half compound assignment with division operation.


## 4.6.1. Functions


__host__ __device__ __half2 __h2div(const __half2 a, const __half2 b)
Performs half2 vector division in round-to-nearest-even mode.
Divides half2 input vector a by input vector b in round-to-nearest-even mode.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The elementwise division of a with b.


__host__ __device__ __half2 __habs2(const __half2 a)
Calculates the absolute value of both halves of the input half2 number and returns the result.
Calculates the absolute value of both halves of the input half2 number and returns the result.

See also
__habs(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

Returns a with the absolute value of both halves.


__host__ __device__ __half2 __hadd2(const __half2 a, const __half2 b)
Performs half2 vector addition in round-to-nearest-even mode.
Performs half2 vector add of inputs a and b, in round-to-nearest-even mode.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The sum of vectors a and b.


__host__ __device__ __half2 __hadd2_rn(const __half2 a, const __half2 b)
Performs half2 vector addition in round-to-nearest-even mode.
Performs half2 vector add of inputs a and b, in round-to-nearest-even mode. Prevents floating-point contractions of mul+add into fma.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The sum of vectors a and b.


__host__ __device__ __half2 __hadd2_sat(const __half2 a, const __half2 b)
Performs half2 vector addition in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Performs half2 vector add of inputs a and b, in round-to-nearest-even mode, and clamps the results to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The sum of a and b, with respect to saturation.


__device__ __half2 __hcmadd(const __half2 a, const __half2 b, const __half2 c)
Performs fast complex multiply-accumulate.
Interprets vector half2 input pairs a, b, and c as complex numbers in half precision: (a.x + I*a.y), (b.x + I*b.y), (c.x + I*c.y) and performs complex multiply-accumulate operation: a*b + c in a simple way: ((a.x*b.x + c.x) - a.y*b.y) + I*((a.x*b.y + c.y) + a.y*b.x)

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.
c – [in] - half2. Is only being read.

Returns

half2

The result of complex multiply-accumulate operation on complex numbers a, b, and c
__half2 result = __hcmadd(a, b, c) is numerically in agreement with:
result.x = __hfma(-a.y, b.y, __hfma(a.x, b.x, c.x))
result.y = __hfma( a.y, b.x, __hfma(a.x, b.y, c.y))


__device__ __half2 __hfma2(const __half2 a, const __half2 b, const __half2 c)
Performs half2 vector fused multiply-add in round-to-nearest-even mode.
Performs half2 vector multiply on inputs a and b, then performs a half2 vector add of the result with c, rounding the result once in round-to-nearest-even mode.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.
c – [in] - half2. Is only being read.

Returns

half2

The result of elementwise fused multiply-add operation on vectors a, b, and c.


__device__ __half2 __hfma2_relu(const __half2 a, const __half2 b, const __half2 c)
Performs half2 vector fused multiply-add in round-to-nearest-even mode with relu saturation.
Performs half2 vector multiply on inputs a and b, then performs a half2 vector add of the result with c, rounding the result once in round-to-nearest-even mode. Then negative result is clamped to 0. NaN result is converted to canonical NaN.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.
c – [in] - half2. Is only being read.

Returns

half2

The result of elementwise fused multiply-add operation on vectors a, b, and c with relu saturation.


__device__ __half2 __hfma2_sat(const __half2 a, const __half2 b, const __half2 c)
Performs half2 vector fused multiply-add in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Performs half2 vector multiply on inputs a and b, then performs a half2 vector add of the result with c, rounding the result once in round-to-nearest-even mode, and clamps the results to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.
c – [in] - half2. Is only being read.

Returns

half2

The result of elementwise fused multiply-add operation on vectors a, b, and c, with respect to saturation.


__host__ __device__ __half2 __hmul2(const __half2 a, const __half2 b)
Performs half2 vector multiplication in round-to-nearest-even mode.
Performs half2 vector multiplication of inputs a and b, in round-to-nearest-even mode.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The result of elementwise multiplying the vectors a and b.


__host__ __device__ __half2 __hmul2_rn(const __half2 a, const __half2 b)
Performs half2 vector multiplication in round-to-nearest-even mode.
Performs half2 vector multiplication of inputs a and b, in round-to-nearest-even mode. Prevents floating-point contractions of mul+add or sub into fma.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The result of elementwise multiplying the vectors a and b.


__host__ __device__ __half2 __hmul2_sat(const __half2 a, const __half2 b)
Performs half2 vector multiplication in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Performs half2 vector multiplication of inputs a and b, in round-to-nearest-even mode, and clamps the results to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The result of elementwise multiplication of vectors a and b, with respect to saturation.


__host__ __device__ __half2 __hneg2(const __half2 a)
Negates both halves of the input half2 number and returns the result.
Negates both halves of the input half2 number a and returns the result.

See also
__hneg(__half) for further details.

Parameters

a – [in] - half2. Is only being read.

Returns

half2

Returns a with both halves negated.


__host__ __device__ __half2 __hsub2(const __half2 a, const __half2 b)
Performs half2 vector subtraction in round-to-nearest-even mode.
Subtracts half2 input vector b from input vector a in round-to-nearest-even mode.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The subtraction of vector b from a.


__host__ __device__ __half2 __hsub2_rn(const __half2 a, const __half2 b)
Performs half2 vector subtraction in round-to-nearest-even mode.
Subtracts half2 input vector b from input vector a in round-to-nearest-even mode. Prevents floating-point contractions of mul+sub into fma.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The subtraction of vector b from a.


__host__ __device__ __half2 __hsub2_sat(const __half2 a, const __half2 b)
Performs half2 vector subtraction in round-to-nearest-even mode, with saturation to [0.0, 1.0].
Subtracts half2 input vector b from input vector a in round-to-nearest-even mode, and clamps the results to range [0.0, 1.0]. NaN results are flushed to +0.0.

Parameters

a – [in] - half2. Is only being read.
b – [in] - half2. Is only being read.

Returns

half2

The subtraction of vector b from a, with respect to saturation.


__device__ __half2 atomicAdd(__half2 *const address, const __half2 val)
Vector add val to the value stored at address in global or shared memory, and writes this value back to address.
The atomicity of the add operation is guaranteed separately for each of the two __half elements; the entire __half2 is not guaranteed to be atomic as a single 32-bit access.
The location of address must be in global or shared memory. This operation has undefined behavior otherwise. This operation is natively supported by devices of compute capability 6.x and higher, older devices use emulation path.

Note
For more details about this function, see the Atomic Functions section in the CUDA C++ Programming Guide.

Parameters

address – [in] - half2*. An address in global or shared memory.
val – [in] - half2. The value to be added.

Returns

half2

The old value read from address.


__host__ __device__ __half2 operator*(const __half2 &lh, const __half2 &rh)
Performs packed half multiplication operation.

See also
__hmul2(__half2, __half2)


__host__ __device__ __half2 &operator*=(__half2 &lh, const __half2 &rh)
Performs packed half compound assignment with multiplication operation.

See also
__hmul2(__half2, __half2)


__host__ __device__ __half2 operator+(const __half2 &h)
Implements packed half unary plus operator, returns input value.


__host__ __device__ __half2 operator+(const __half2 &lh, const __half2 &rh)
Performs packed half addition operation.

See also
__hadd2(__half2, __half2)


__host__ __device__ __half2 operator++(__half2 &h, const int ignored)
Performs packed half postfix increment operation.

See also
__hadd2(__half2, __half2)


__host__ __device__ __half2 &operator++(__half2 &h)
Performs packed half prefix increment operation.

See also
__hadd2(__half2, __half2)


__host__ __device__ __half2 &operator+=(__half2 &lh, const __half2 &rh)
Performs packed half compound assignment with addition operation.

See also
__hadd2(__half2, __half2)


__host__ __device__ __half2 operator-(const __half2 &h)
Implements packed half unary minus operator.

See also
__hneg2(__half2)


__host__ __device__ __half2 operator-(const __half2 &lh, const __half2 &rh)
Performs packed half subtraction operation.

See also
__hsub2(__half2, __half2)


__host__ __device__ __half2 &operator--(__half2 &h)
Performs packed half prefix decrement operation.

See also
__hsub2(__half2, __half2)


__host__ __device__ __half2 operator--(__half2 &h, const int ignored)
Performs packed half postfix decrement operation.

See also
__hsub2(__half2, __half2)


__host__ __device__ __half2 &operator-=(__half2 &lh, const __half2 &rh)
Performs packed half compound assignment with subtraction operation.

See also
__hsub2(__half2, __half2)


__host__ __device__ __half2 operator/(const __half2 &lh, const __half2 &rh)
Performs packed half division operation.

See also
__h2div(__half2, __half2)


__host__ __device__ __half2 &operator/=(__half2 &lh, const __half2 &rh)
Performs packed half compound assignment with division operation.

See also
__h2div(__half2, __half2)