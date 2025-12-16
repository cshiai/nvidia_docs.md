# libdevice User's Guide

Prototype:


```
float @__nv_ceilf(float %x)
```


Description:


Compute the smallest integer value not less than x.




Returns:

 Returns  ⌈ x ⌉  expressed as a floating-point number.
 - __nv_ceilf(  ± 0  ) returns  ± 0  .
 - __nv_ceilf(  ± ∞  ) returns  ± ∞  .




Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes