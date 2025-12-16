# libdevice User's Guide

Prototype:


```
float @__nv_erfcf(float %x)
```


Description:


Calculate the complementary error function of the input argument x, 1 - erf(x).




Returns:


 - __nv_erfcf(  − ∞  ) returns 2.
 - __nv_erfcf(  + ∞  ) returns +0.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes