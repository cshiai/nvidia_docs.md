# libdevice User's Guide

Prototype:


```
float @__nv_cosf(float %x)
```


Description:


Calculate the cosine of the input argument x (measured in radians).




Returns:


 - __nv_cosf(  ± 0  ) returns 1.
 - __nv_cosf(  ± ∞  ) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes