# libdevice User's Guide

Prototype:


```
float @__nv_jnf(i32 %n, float %x)
```


Description:


Calculate the value of the Bessel function of the first kind of order n for the input argument x,   J n  ( x )  .




Returns:

 Returns the value of the Bessel function of the first kind of order n.
 - __nv_jnf(n, NaN) returns NaN.
 - __nv_jnf(n, x) returns NaN for n < 0.
 - __nv_jnf(n,  + ∞  ) returns +0.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes