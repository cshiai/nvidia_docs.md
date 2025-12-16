# libdevice User's Guide

Prototype:


```
float @__nv_remquof(float %x, float %y, i32* %quo)
```


Description:


Compute a double-precision floating-point remainder in the same way as the remainder() function. Argument quo returns part of quotient upon division of x by y. Value quo has the same sign as   x y   and may not be the exact quotient but agrees with the exact quotient in the low order 3 bits.




Returns:

 Returns the remainder.
 - __nv_remquof(x, 0, quo) returns NaN.
 - __nv_remquof(  ± ∞  , y, quo) returns NaN.
 - __nv_remquof(x,  ± ∞  , quo) returns x.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes