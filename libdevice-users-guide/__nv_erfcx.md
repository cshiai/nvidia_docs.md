# libdevice User's Guide

Prototype:


```
double @__nv_erfcx(double %x)
```


Description:


Calculate the scaled complementary error function of the input argument x,   e   x 2    ⋅  erfc  ( x )  .




Returns:


 - __nv_erfcx(  - ∞  ) returns  + ∞
 - __nv_erfcx(  + ∞  ) returns +0
 - __nv_erfcx(x) returns  + ∞  if the correctly calculated value is outside the double floating point range.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes