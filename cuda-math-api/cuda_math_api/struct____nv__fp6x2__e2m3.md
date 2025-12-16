# 15.14. __nv_fp6x2_e2m3


struct __nv_fp6x2_e2m3
__nv_fp6x2_e2m3 datatype
This structure implements the datatype for handling two fp6 floating-point numbers of e2m3 kind each.
The structure implements converting constructors and operators.

Public Functions

__host__ __device__ inline __nv_fp6x2_e2m3()

Constructor by default.

__host__ __device__ inline explicit __nv_fp6x2_e2m3(const __half2 f)

Constructor from __half2 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ inline explicit __nv_fp6x2_e2m3(const __nv_bfloat162 f)

Constructor from __nv_bfloat162 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ inline explicit __nv_fp6x2_e2m3(const double2 f)

Constructor from double2 data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ inline explicit __nv_fp6x2_e2m3(const float2 f)

Constructor from float2 data type, relies on __NV_SATFINITE behavior for out-of-range values.

Public Members

__nv_fp6x2_storage_t __x

Storage variable contains the vector of two fp6 floating-point data values.