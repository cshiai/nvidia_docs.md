# libdevice User's Guide

Prototype:


```
float @__nv_scalbnf(float %x, i32 %y)
```


Description:


Scale x by   2 n   by efficient manipulation of the floating-point exponent.




Returns:

 Returns x *   2 n   .
 - __nv_scalbnf(  ± 0  , n) returns  ± 0  .
 - __nv_scalbnf(x, 0) returns x.
 - __nv_scalbnf(  ± ∞  , n) returns  ± ∞  .




Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes