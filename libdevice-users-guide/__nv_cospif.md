# libdevice User's Guide

Prototype:


```
float @__nv_cospif(float %x)
```


Description:


Calculate the cosine of x × π  (measured in radians), where x is the input argument.




Returns:


 - __nv_cospif(  ± 0  ) returns 1.
 - __nv_cospif(  ± ∞  ) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes