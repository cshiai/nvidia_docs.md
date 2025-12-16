# 4.1. Half Arithmetic Constants


To use these constants, include the header file `cuda_fp16.h` in your program.


Macros


CUDART_INF_FP16
Defines floating-point positive infinity value for the half data type.

CUDART_MAX_NORMAL_FP16
Defines a maximum representable value for the half data type.

CUDART_MIN_DENORM_FP16
Defines a minimum representable (denormalized) value for the half data type.

CUDART_NAN_FP16
Defines canonical NaN value for the half data type.

CUDART_NEG_ZERO_FP16
Defines a negative zero value for the half data type.

CUDART_ONE_FP16
Defines a value of 1.0 for the half data type.

CUDART_ZERO_FP16
Defines a positive zero value for the half data type.


## 4.1.1. Macros


CUDART_INF_FP16 __ushort_as_half((unsigned short)0x7C00U)
Defines floating-point positive infinity value for the half data type.


CUDART_MAX_NORMAL_FP16 __ushort_as_half((unsigned short)0x7BFFU)
Defines a maximum representable value for the half data type.


CUDART_MIN_DENORM_FP16 __ushort_as_half((unsigned short)0x0001U)
Defines a minimum representable (denormalized) value for the half data type.


CUDART_NAN_FP16 __ushort_as_half((unsigned short)0x7FFFU)
Defines canonical NaN value for the half data type.


CUDART_NEG_ZERO_FP16 __ushort_as_half((unsigned short)0x8000U)
Defines a negative zero value for the half data type.


CUDART_ONE_FP16 __ushort_as_half((unsigned short)0x3C00U)
Defines a value of 1.0 for the half data type.


CUDART_ZERO_FP16 __ushort_as_half((unsigned short)0x0000U)
Defines a positive zero value for the half data type.