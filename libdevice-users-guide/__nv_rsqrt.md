# libdevice User's Guide

Prototype:


```
double @__nv_rsqrt(double %x)
```


Description:


Calculate the reciprocal of the nonnegative square root of x,  1  /   x   .




Returns:

 Returns  1  /   x   .
 - __nv_rsqrt(  + ∞  ) returns +0.
 - __nv_rsqrt(  ± 0  ) returns  ± ∞  .
 - __nv_rsqrt(x) returns NaN if x is less than 0.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes