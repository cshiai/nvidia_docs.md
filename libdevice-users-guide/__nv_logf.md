# libdevice User's Guide

Prototype:


```
float @__nv_logf(float %x)
```


Description:


Calculate the base  e  logarithm of the input argument x.




Returns:


 - __nv_logf(  ± 0  ) returns  − ∞  .
 - __nv_logf(1) returns +0.
 - __nv_logf(x) returns NaN for x < 0.
 - __nv_logf(  + ∞  ) returns  + ∞

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes