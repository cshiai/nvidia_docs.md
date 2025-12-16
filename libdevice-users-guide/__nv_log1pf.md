# libdevice User's Guide

Prototype:


```
float @__nv_log1pf(float %x)
```


Description:


Calculate the value of  l o  g  e   ( 1 + x )  of the input argument x.




Returns:


 - __nv_log1pf(  ± 0  ) returns  − ∞  .
 - __nv_log1pf(-1) returns +0.
 - __nv_log1pf(x) returns NaN for x < -1.
 - __nv_log1pf(  + ∞  ) returns  + ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes