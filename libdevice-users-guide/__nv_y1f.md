# libdevice User's Guide

Prototype:


```
float @__nv_y1f(float %x)
```


Description:


Calculate the value of the Bessel function of the second kind of order 1 for the input argument x,   Y 1  ( x )  .




Returns:

 Returns the value of the Bessel function of the second kind of order 1.
 - __nv_y1f(0) returns  − ∞  .
 - __nv_y1f(x) returns NaN for x < 0.
 - __nv_y1f(  + ∞  ) returns +0.
 - __nv_y1f(NaN) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes