# libdevice User's Guide

Prototype:


```
float @__nv_fabsf(float %f)
```


Description:


Calculate the absolute value of the input argument x.




Returns:

 Returns the absolute value of the input argument.
 - __nv_fabsf(  ± ∞  ) returns  + ∞  .
 - __nv_fabsf(  ± 0  ) returns 0.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes