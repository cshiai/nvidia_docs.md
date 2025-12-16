# 15.16. __nv_fp6x4_e2m3


struct __nv_fp6x4_e2m3
__nv_fp6x4_e2m3 datatype
This structure implements the datatype for handling four fp6 floating-point numbers of e2m3 kind each.
The structure implements converting constructors and operators.

Public Functions

__host__ __device__ inline __nv_fp6x4_e2m3()

Constructor by default.

__host__ __device__ inline explicit __nv_fp6x4_e2m3(const __half2 flo, const __half2 fhi)

Constructor from a pair of __half2 data type values, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ inline explicit __nv_fp6x4_e2m3(const __nv_bfloat162 flo, const __nv_bfloat162 fhi)

Constructor from a pair of __nv_bfloat162 data type values, relies on __NV_SATFINITE behavior for out-of-range values.

inline explicit __NV_SILENCE_DEPRECATION_BEGIN __host__ __device__ __nv_fp6x4_e2m3(const double4 f)

Constructor from double4 vector data type, relies on __NV_SATFINITE behavior for out-of-range values.

inline explicit __NV_SILENCE_DEPRECATION_END __host__ __device__ __nv_fp6x4_e2m3(const double4_16a f)

Constructor from double4_16a vector data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ inline explicit __nv_fp6x4_e2m3(const double4_32a f)

Constructor from double4_32a vector data type, relies on __NV_SATFINITE behavior for out-of-range values.

__host__ __device__ inline explicit __nv_fp6x4_e2m3(const float4 f)

Constructor from float4 vector data type, relies on __NV_SATFINITE behavior for out-of-range values.

Public Members

__nv_fp6x4_storage_t __x

Storage variable contains the vector of four fp6 floating-point data values.