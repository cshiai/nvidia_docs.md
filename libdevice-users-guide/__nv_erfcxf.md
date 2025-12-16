# libdevice User's Guide

Prototype:


```
float @__nv_erfcxf(float %x)
```


Description:


Calculate the scaled complementary error function of the input argument x,   e   x 2    ⋅  erfc  ( x )  .




Returns:


 - __nv_erfcxf(  - ∞  ) returns  + ∞
 - __nv_erfcxf(  + ∞  ) returns +0
 - __nv_erfcxf(x) returns  + ∞  if the correctly calculated value is outside the double floating point range.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes