# libdevice User's Guide

Prototype:


```
i32 @__nv_ffsll(i64 %x)
```


Description:


Find the position of the first (least significant) bit set to 1 in x, where the least significant bit position is 1.




Returns:

 Returns a value between 0 and 64 inclusive representing the position of the first bit set.
 - __nv_ffsll(0) returns 0.




Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes