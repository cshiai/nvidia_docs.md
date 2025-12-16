# libdevice User's Guide

Prototype:


```
float @__nv_logbf(float %x)
```


Description:


Calculate the floating point representation of the exponent of the input argument x.




Returns:


 - __nv_logbf  ± 0  returns  − ∞
 - __nv_logbf  ± ∞  returns  + ∞

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes