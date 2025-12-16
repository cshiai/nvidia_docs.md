# libdevice User's Guide

Prototype:


```
double @__nv_erfcinv(double %x)
```


Description:


Calculate the inverse complementary error function of the input argument y, for y in the interval [0, 2]. The inverse complementary error function find the value x that satisfies the equation y = erfc(x), for  0 ≤ y ≤ 2  , and  − ∞ ≤ x ≤ ∞  .




Returns:


 - __nv_erfcinv(0) returns  + ∞  .
 - __nv_erfcinv(2) returns  − ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes