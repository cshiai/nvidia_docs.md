# libdevice User's Guide

Prototype:


```
float @__nv_powf(float %x, float %y)
```


Description:


Calculate the value of x to the power of y




Returns:


 - __nv_powf(  ± 0  , y) returns  ± ∞  for y an integer less than 0.
 - __nv_powf(  ± 0  , y) returns  ± 0  for y an odd integer greater than 0.
 - __nv_powf(  ± 0  , y) returns +0 for y > 0 and not and odd integer.
 - __nv_powf(-1,  ± ∞  ) returns 1.
 - __nv_powf(+1, y) returns 1 for any y, even a NaN.
 - __nv_powf(x,  ± 0  ) returns 1 for any x, even a NaN.
 - __nv_powf(x, y) returns a NaN for finite x < 0 and finite non-integer y.
 - __nv_powf(x,  − ∞  ) returns  + ∞  for   |  x  |  < 1  .
 - __nv_powf(x,  − ∞  ) returns +0 for   |  x  |  > 1  .
 - __nv_powf(x,  + ∞  ) returns +0 for   |  x  |  < 1  .
 - __nv_powf(x,  + ∞  ) returns  + ∞  for   |  x  |  > 1  .
 - __nv_powf(  − ∞  , y) returns -0 for y an odd integer less than 0.
 - __nv_powf(  − ∞  , y) returns +0 for y < 0 and not an odd integer.
 - __nv_powf(  − ∞  , y) returns  − ∞  for y an odd integer greater than 0.
 - __nv_powf(  − ∞  , y) returns  + ∞  for y > 0 and not an odd integer.
 - __nv_powf(  + ∞  , y) returns +0 for y < 0.
 - __nv_powf(  + ∞  , y) returns  + ∞  for y > 0.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes