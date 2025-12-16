# libdevice User's Guide

Prototype:


```
double @__nv_j0(double %x)
```


Description:


Calculate the value of the Bessel function of the first kind of order 0 for the input argument x,   J 0  ( x )  .




Returns:

 Returns the value of the Bessel function of the first kind of order 0.
 - __nv_j0(  ± ∞  ) returns +0.
 - __nv_j0(NaN) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes