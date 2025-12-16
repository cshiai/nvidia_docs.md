# libdevice User's Guide

Prototype:


```
float @__nv_saturatef(float %x)
```


Description:


Clamp the input argument x to be within the interval [+0.0, 1.0].


Returns:


 - __nv_saturatef(x) returns 0 if x < 0.
 - __nv_saturatef(x) returns 1 if x > 1.
 - __nv_saturatef(x) returns x if  0 ≤ x ≤ 1  .
 - __nv_saturatef(NaN) returns 0.




Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes