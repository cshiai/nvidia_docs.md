# libdevice User's Guide

Prototype:


```
double @__nv_cbrt(double %x)
```


Description:


Calculate the cube root of x,   x  1  /  3    .




Returns:

 Returns   x  1  /  3    .
 - __nv_cbrt(  ± 0  ) returns  ± 0  .
 - __nv_cbrt(  ± ∞  ) returns  ± ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes