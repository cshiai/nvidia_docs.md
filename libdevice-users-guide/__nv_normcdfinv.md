# libdevice User's Guide

Prototype:


```
double @__nv_normcdfinv(double %x)
```


Description:


Calculate the inverse of the standard normal cumulative distribution function for input argument y,   Φ  − 1   ( y )  . The function is defined for input values in the interval  ( 0 , 1 )  .




Returns:


 - __nv_normcdfinv(0) returns  − ∞  .
 - __nv_normcdfinv(1) returns  + ∞  .
 - __nv_normcdfinv(x) returns NaN if x is not in the interval [0,1].

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes