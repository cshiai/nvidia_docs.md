# libdevice User's Guide

Prototype:


```
float @__nv_tanf(float %x)
```


Description:


Calculate the tangent of the input argument x (measured in radians).




Returns:


 - __nv_tanf(  ± 0  ) returns  ± 0  .
 - __nv_tanf(  ± ∞  ) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes