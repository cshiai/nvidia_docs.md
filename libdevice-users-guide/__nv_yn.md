# libdevice User's Guide

Prototype:


```
double @__nv_yn(i32 %n, double %x)
```


Description:


Calculate the value of the Bessel function of the second kind of order n for the input argument x,   Y n  ( x )  .




Returns:

 Returns the value of the Bessel function of the second kind of order n.
 - __nv_yn(n, x) returns NaN for n < 0.
 - __nv_yn(n, 0) returns  − ∞  .
 - __nv_yn(n, x) returns NaN for x < 0.
 - __nv_yn(n,  + ∞  ) returns +0.
 - __nv_yn(n, NaN) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes