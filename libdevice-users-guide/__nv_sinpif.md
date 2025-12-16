# libdevice User's Guide

Prototype:


```
float @__nv_sinpif(float %x)
```


Description:


Calculate the sine of x × π  (measured in radians), where x is the input argument.




Returns:


 - __nv_sinpif(  ± 0  ) returns  ± 0  .
 - __nv_sinpif(  ± ∞  ) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes