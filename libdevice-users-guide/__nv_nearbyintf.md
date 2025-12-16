# libdevice User's Guide

Prototype:


```
float @__nv_nearbyintf(float %x)
```


Description:


Round argument x to an integer value in double precision floating-point format.




Returns:


 - __nv_nearbyintf(  ± 0  ) returns  ± 0  .
 - __nv_nearbyintf(  ± ∞  ) returns  ± ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes