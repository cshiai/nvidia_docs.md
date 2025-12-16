# libdevice User's Guide

Prototype:


```
double @__nv_erfinv(double %x)
```


Description:


Calculate the inverse error function of the input argument y, for y in the interval [-1, 1]. The inverse error function finds the value x that satisfies the equation y = erf(x), for  − 1 ≤ y ≤ 1  , and  − ∞ ≤ x ≤ ∞  .




Returns:


 - __nv_erfinv(1) returns  + ∞  .
 - __nv_erfinv(-1) returns  − ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes