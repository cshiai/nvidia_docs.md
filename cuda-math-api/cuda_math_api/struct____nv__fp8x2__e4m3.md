# 15.21. __nv_fp8x2_e4m3


struct __nv_fp8x2_e4m3
__nv_fp8x2_e4m3 datatype
This structure implements the datatype for storage and operations on the vector of two fp8 values of e4m3 kind each: with 1 sign, 4 exponent, 1 implicit and 3 explicit mantissa bits. The encoding doesn’t support Infinity. NaNs are limited to 0x7F and 0xFF values.

Public Functions

__nv_fp8x2_e4m3() = default

Constructor by default.

__host__ __device__ inline explicit __nv_fp8x2_e4m3(const __half2 f)

Constructor from __half2 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ inline explicit __nv_fp8x2_e4m3(const __nv_bfloat162 f)

Constructor from __nv_bfloat162 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ inline explicit __nv_fp8x2_e4m3(const double2 f)

Constructor from double2 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ inline explicit __nv_fp8x2_e4m3(const float2 f)

Constructor from float2 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ inline explicit operator __half2() const

Conversion operator to __half2 data type.

__host__ __device__ inline explicit operator float2() const

Conversion operator to float2 data type.

Public Members

__nv_fp8x2_storage_t __x

Storage variable contains the vector of two fp8 floating-point data values.