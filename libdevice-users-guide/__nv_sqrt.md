# libdevice User's Guide

Prototype:


```
double @__nv_sqrt(double %x)
```


Description:


Calculate the nonnegative square root of x,   x   .




Returns:

 Returns   x   .
 - __nv_sqrt(  ± 0  ) returns  ± 0  .
 - __nv_sqrt(  + ∞  ) returns  + ∞  .
 - __nv_sqrt(x) returns NaN if x is less than 0.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes