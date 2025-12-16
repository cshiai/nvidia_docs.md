# libdevice User's Guide

Prototype:


```
float @__nv_atanf(float %x)
```


Description:


Calculate the principal value of the arc tangent of the input argument x.




Returns:

 Result will be in radians, in the interval [-  π  /2, +  π  /2].
 - __nv_atan(0) returns +0.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes