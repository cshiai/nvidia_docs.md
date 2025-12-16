# libdevice User's Guide

Prototype:


```
float @__nv_normcdfinvf(float %x)
```


Description:


Calculate the inverse of the standard normal cumulative distribution function for input argument y,   Φ  − 1   ( y )  . The function is defined for input values in the interval  ( 0 , 1 )  .




Returns:


 - __nv_normcdfinvf(0) returns  − ∞  .
 - __nv_normcdfinvf(1) returns  + ∞  .
 - __nv_normcdfinvf(x) returns NaN if x is not in the interval [0,1].

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes