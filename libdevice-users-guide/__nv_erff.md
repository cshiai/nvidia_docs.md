# libdevice User's Guide

Prototype:


```
float @__nv_erff(float %x)
```


Description:


Calculate the value of the error function for the input argument x,   2  π    ∫ 0 x   e  −  t 2    d t  .




Returns:


 - __nv_erff(  ± 0  ) returns  ± 0  .
 - __nv_erff(  ± ∞  ) returns  ± 1  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes