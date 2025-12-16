# libdevice User's Guide

Prototype:


```
double @__nv_atanh(double %x)
```


Description:


Calculate the arc hyperbolic tangent of the input argument x.




Returns:


 - __nv_atanh(  ± 0  ) returns  ± 0  .
 - __nv_atanh(  ± 1  ) returns  ± ∞  .
 - __nv_atanh(x) returns NaN for x outside interval [-1, 1].

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes