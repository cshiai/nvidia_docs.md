# libdevice User's Guide

Prototype:


```
float @__nv_normcdff(float %x)
```


Description:


Calculate the cumulative distribution function of the standard normal distribution for input argument y,  Φ ( y )  .




Returns:


 - __nv_normcdff(  + ∞  ) returns 1
 - __nv_normcdff(  − ∞  ) returns +0

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes