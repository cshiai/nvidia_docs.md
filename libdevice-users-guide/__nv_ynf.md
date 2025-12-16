# libdevice User's Guide

Prototype:


```
float @__nv_ynf(i32 %n, float %x)
```


Description:


Calculate the value of the Bessel function of the second kind of order n for the input argument x,   Y n  ( x )  .




Returns:

 Returns the value of the Bessel function of the second kind of order n.
 - __nv_ynf(n, x) returns NaN for n < 0.
 - __nv_ynf(n, 0) returns  − ∞  .
 - __nv_ynf(n, x) returns NaN for x < 0.
 - __nv_ynf(n,  + ∞  ) returns +0.
 - __nv_ynf(n, NaN) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes