# libdevice User's Guide

Prototype:


```
float @__nv_fast_powf(float %x, float %y)
```


Description:


Calculate the fast approximate of x, the first input argument, raised to the power of y, the second input argument,   x y   .




Returns:


Returns an approximation to   x y   .

   Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Intrinsic Functions section.


Most input and output values around denormal range are flushed to sign preserving 0.0.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes