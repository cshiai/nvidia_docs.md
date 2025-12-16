# libdevice User's Guide

Prototype:


```
float @__nv_fmodf(float %x, float %y)
```


Description:


Calculate the floating-point remainder of x / y. The floating-point remainder of the division operation x / y calculated by this function is exactly the value x - n*y, where n is x / y with its fractional part truncated. The computed value will have the same sign as x, and its magnitude will be less than the magnitude of y.


Returns:


 - Returns the floating-point remainder of x / y.
 - __nv_fmodf(  ± 0  , y) returns  ± 0  if y is not zero.
 - __nv_fmodf(x,  ± ∞  ) returns x if x is finite.
 - __nv_fmodf(x, y) returns NaN if x is  ± ∞  or y is zero.
 - If either argument is NaN, NaN is returned.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes