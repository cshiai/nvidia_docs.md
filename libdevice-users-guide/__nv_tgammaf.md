# libdevice User's Guide

Prototype:


```
float @__nv_tgammaf(float %x)
```


Description:


Calculate the gamma function of the input argument x, namely the value of   ∫  0   ∞    e  − t    t  x − 1   d t  .




Returns:


 - __nv_tgammaf(  ± 0  ) returns  ± ∞  .
 - __nv_tgammaf(2) returns +0.
 - __nv_tgammaf(x) returns  ± ∞  if the correctly calculated value is outside the double floating point range.
 - __nv_tgammaf(x) returns NaN if x < 0.
 - __nv_tgammaf(  − ∞  ) returns NaN.
 - __nv_tgammaf(  + ∞  ) returns  + ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes