# libdevice User's Guide

Prototype:


```
double @__nv_cos(double %x)
```


Description:


Calculate the cosine of the input argument x (measured in radians).




Returns:


 - __nv_cos(  ± 0  ) returns 1.
 - __nv_cos(  ± ∞  ) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes