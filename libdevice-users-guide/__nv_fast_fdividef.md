# libdevice User's Guide

Prototype:


```
float @__nv_fast_fdividef(float %x, float %y)
```


Description:


Calculate the fast approximate division of x by y.




Returns:

 Returns x / y.
 - __nv_fast_fdividef(  ∞  , y) returns NaN for   2  126   < y <  2  128    .
 - __nv_fast_fdividef(x, y) returns 0 for   2  126   < y <  2  128    and  x ≠ ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Intrinsic Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes