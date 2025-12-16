# 5.1. Bfloat16 Arithmetic Constants


To use these constants, include the header file `cuda_bf16.h` in your program.


Macros


CUDART_INF_BF16
Defines floating-point positive infinity value for the nv_bfloat16 data type.

CUDART_MAX_NORMAL_BF16
Defines a maximum representable value for the nv_bfloat16 data type.

CUDART_MIN_DENORM_BF16
Defines a minimum representable (denormalized) value for the nv_bfloat16 data type.

CUDART_NAN_BF16
Defines canonical NaN value for the nv_bfloat16 data type.

CUDART_NEG_ZERO_BF16
Defines a negative zero value for the nv_bfloat16 data type.

CUDART_ONE_BF16
Defines a value of 1.0 for the nv_bfloat16 data type.

CUDART_ZERO_BF16
Defines a positive zero value for the nv_bfloat16 data type.


## 5.1.1. Macros


CUDART_INF_BF16 __ushort_as_bfloat16((unsigned short)0x7F80U)
Defines floating-point positive infinity value for the nv_bfloat16 data type.


CUDART_MAX_NORMAL_BF16 __ushort_as_bfloat16((unsigned short)0x7F7FU)
Defines a maximum representable value for the nv_bfloat16 data type.


CUDART_MIN_DENORM_BF16 __ushort_as_bfloat16((unsigned short)0x0001U)
Defines a minimum representable (denormalized) value for the nv_bfloat16 data type.


CUDART_NAN_BF16 __ushort_as_bfloat16((unsigned short)0x7FFFU)
Defines canonical NaN value for the nv_bfloat16 data type.


CUDART_NEG_ZERO_BF16 __ushort_as_bfloat16((unsigned short)0x8000U)
Defines a negative zero value for the nv_bfloat16 data type.


CUDART_ONE_BF16 __ushort_as_bfloat16((unsigned short)0x3F80U)
Defines a value of 1.0 for the nv_bfloat16 data type.


CUDART_ZERO_BF16 __ushort_as_bfloat16((unsigned short)0x0000U)
Defines a positive zero value for the nv_bfloat16 data type.