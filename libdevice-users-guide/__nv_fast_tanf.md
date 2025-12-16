# libdevice User's Guide

Prototype:


```
float @__nv_fast_tanf(float %x)
```


Description:


Calculate the fast approximate tangent of the input argument x, measured in radians.




Returns:


Returns the approximate tangent of x.

   Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Intrinsic Functions section.


The result is computed as the fast divide of __nv_sinf() by __nv_cosf(). Denormal input and output are flushed to sign-preserving 0.0 at each step of the computation.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes