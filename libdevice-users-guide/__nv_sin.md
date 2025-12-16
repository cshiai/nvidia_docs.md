# libdevice User's Guide

Prototype:


```
double @__nv_sin(double %x)
```


Description:


Calculate the sine of the input argument x (measured in radians).




Returns:


 - __nv_sin(  ± 0  ) returns  ± 0  .
 - __nv_sin(  ± ∞  ) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes