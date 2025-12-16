# libdevice User's Guide

Prototype:


```
double @__nv_nearbyint(double %x)
```


Description:


Round argument x to an integer value in double precision floating-point format.




Returns:


 - __nv_nearbyint(  ± 0  ) returns  ± 0  .
 - __nv_nearbyint(  ± ∞  ) returns  ± ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes