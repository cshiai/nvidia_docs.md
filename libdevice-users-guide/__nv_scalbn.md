# libdevice User's Guide

Prototype:


```
double @__nv_scalbn(double %x, i32 %y)
```


Description:


Scale x by   2 n   by efficient manipulation of the floating-point exponent.




Returns:

 Returns x *   2 n   .
 - __nv_scalbn(  ± 0  , n) returns  ± 0  .
 - __nv_scalbn(x, 0) returns x.
 - __nv_scalbn(  ± ∞  , n) returns  ± ∞  .




Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes