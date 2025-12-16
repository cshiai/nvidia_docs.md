# libdevice User's Guide

Prototype:


```
float @__nv_sqrtf(float %x)
```


Description:


Calculate the nonnegative square root of x,   x   .




Returns:

 Returns   x   .
 - __nv_sqrtf(  ± 0  ) returns  ± 0  .
 - __nv_sqrtf(  + ∞  ) returns  + ∞  .
 - __nv_sqrtf(x) returns NaN if x is less than 0.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes