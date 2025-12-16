# libdevice User's Guide

Prototype:


```
float @__nv_fdimf(float %x, float %y)
```


Description:


Compute the positive difference between x and y. The positive difference is x - y when x > y and +0 otherwise.




Returns:

 Returns the positive difference between x and y.
 - __nv_fdimf(x, y) returns x - y if x > y.
 - __nv_fdimf(x, y) returns +0 if x ≤ y.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes