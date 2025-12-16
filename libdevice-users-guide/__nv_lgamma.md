# libdevice User's Guide

Prototype:


```
double @__nv_lgamma(double %x)
```


Description:


Calculate the natural logarithm of the absolute value of the gamma function of the input argument x, namely the value of   log  e      ∫  0   ∞    e  − t    t  x − 1   d t




Returns:


 - __nv_lgamma(1) returns +0.
 - __nv_lgamma(2) returns +0.
 - __nv_lgamma(x) returns  ± ∞  if the correctly calculated value is outside the double floating point range.
 - __nv_lgamma(x) returns  + ∞  if x ≤  0.
 - __nv_lgamma(  − ∞  ) returns  − ∞  .
 - __nv_lgamma(  + ∞  ) returns  + ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes