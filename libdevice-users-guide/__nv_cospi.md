# libdevice User's Guide

Prototype:


```
double @__nv_cospi(double %x)
```


Description:


Calculate the cosine of x × π  (measured in radians), where x is the input argument.




Returns:


 - __nv_cospi(  ± 0  ) returns 1.
 - __nv_cospi(  ± ∞  ) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes