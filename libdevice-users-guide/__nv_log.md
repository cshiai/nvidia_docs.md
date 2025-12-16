# libdevice User's Guide

Prototype:


```
double @__nv_log(double %x)
```


Description:


Calculate the base  e  logarithm of the input argument x.




Returns:


 - __nv_log(  ± 0  ) returns  − ∞  .
 - __nv_log(1) returns +0.
 - __nv_log(x) returns NaN for x < 0.
 - __nv_log(  + ∞  ) returns  + ∞

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes