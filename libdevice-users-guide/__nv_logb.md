# libdevice User's Guide

Prototype:


```
double @__nv_logb(double %x)
```


Description:


Calculate the floating point representation of the exponent of the input argument x.




Returns:


 - __nv_logb  ± 0  returns  − ∞
 - __nv_logb  ± ∞  returns  + ∞

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes