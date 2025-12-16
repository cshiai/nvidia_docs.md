# libdevice User's Guide

Prototype:


```
float @__nv_rcbrtf(float %x)
```


Description:


Calculate reciprocal cube root function of x




Returns:


 - __nv_rcbrtf(  ± 0  ) returns  ± ∞  .
 - __nv_rcbrtf(  ± ∞  ) returns  ± 0  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes