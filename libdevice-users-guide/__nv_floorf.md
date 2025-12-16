# libdevice User's Guide

Prototype:


```
float @__nv_floorf(float %f)
```


Description:


Calculates the largest integer value which is less than or equal to x.




Returns:

 Returns the largest integer value which is less than or equal to x expressed as a floating-point number.
 - __nv_floorf(  ± ∞  ) returns  ± ∞  .
 - __nv_floorf(  ± 0  ) returns  ± 0  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes