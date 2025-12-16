# libdevice User's Guide

Prototype:


```
double @__nv_remainder(double %x, double %y)
```


Description:


Compute double-precision floating-point remainder r of dividing x by y for nonzero y. Thus  r = x − n y  . The value n is the integer value nearest   x y   . In the case when   |  n −  x y   |  =  1 2   , the even n value is chosen.




Returns:


 - __nv_remainder(x, 0) returns NaN.
 - __nv_remainder(  ± ∞  , y) returns NaN.
 - __nv_remainder(x,  ± ∞  ) returns x for finite x.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes