# libdevice User's Guide

Prototype:


```
double @__nv_erfc(double %x)
```


Description:


Calculate the complementary error function of the input argument x, 1 - erf(x).




Returns:


 - __nv_erfc(  − ∞  ) returns 2.
 - __nv_erfc(  + ∞  ) returns +0.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes