# libdevice User's Guide

Prototype:


```
float @__nv_lgammaf(float %x)
```


Description:


Calculate the natural logarithm of the absolute value of the gamma function of the input argument x, namely the value of   log  e      ∫  0   ∞    e  − t    t  x − 1   d t




Returns:


 - __nv_lgammaf(1) returns +0.
 - __nv_lgammaf(2) returns +0.
 - __nv_lgammaf(x) returns  ± ∞  if the correctly calculated value is outside the double floating point range.
 - __nv_lgammaf(x) returns  + ∞  if x ≤  0.
 - __nv_lgammaf(  − ∞  ) returns  − ∞  .
 - __nv_lgammaf(  + ∞  ) returns  + ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes