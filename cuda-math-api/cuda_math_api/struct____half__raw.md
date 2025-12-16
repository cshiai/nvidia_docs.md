# 15.4. __half_raw


struct __half_raw
__half_raw data type
Type allows static initialization of half until it becomes a built-in type.

Note: this initialization is as a bit-field representation of half, and not a conversion from short to half. Such representation will be deprecated in a future version of CUDA.
Note: this is visible to non-nvcc compilers, including C-only compilations

Public Members

unsigned short x

Storage field contains bits representation of the half floating-point number.