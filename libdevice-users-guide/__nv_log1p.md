# libdevice User's Guide

Prototype:


```
double @__nv_log1p(double %x)
```


Description:


Calculate the value of  l o  g  e   ( 1 + x )  of the input argument x.




Returns:


 - __nv_log1p(  ± 0  ) returns  − ∞  .
 - __nv_log1p(-1) returns +0.
 - __nv_log1p(x) returns NaN for x < -1.
 - __nv_log1p(  + ∞  ) returns  + ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes