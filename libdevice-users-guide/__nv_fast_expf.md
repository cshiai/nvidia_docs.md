# libdevice User's Guide

Prototype:


```
float @__nv_fast_expf(float %x)
```


Description:


Calculate the fast approximate base  e  exponential of the input argument x,   e x   .




Returns:


Returns an approximation to   e x   .

   Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Intrinsic Functions section.


Most input and output values around denormal range are flushed to sign preserving 0.0.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes