# libdevice User's Guide

Prototype:


```
float @__nv_ldexpf(float %x, i32 %y)
```


Description:


Calculate the value of  x ⋅  2  e x p    of the input arguments x and exp.




Returns:


 - __nv_ldexpf(x) returns  ± ∞  if the correctly calculated value is outside the double floating point range.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes