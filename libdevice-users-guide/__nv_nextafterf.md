# libdevice User's Guide

Prototype:


```
float @__nv_nextafterf(float %x, float %y)
```


Description:


Calculate the next representable double-precision floating-point value following x in the direction of y. For example, if y is greater than x, nextafter() returns the smallest representable number greater than x




Returns:


 - __nv_nextafterf(  ± ∞  , y) returns  ± ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes