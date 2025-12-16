# libdevice User's Guide

Prototype:


```
double @__nv_log2(double %x)
```


Description:


Calculate the base 2 logarithm of the input argument x.




Returns:


 - __nv_log2(  ± 0  ) returns  − ∞  .
 - __nv_log2(1) returns +0.
 - __nv_log2(x) returns NaN for x < 0.
 - __nv_log2(  + ∞  ) returns  + ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes