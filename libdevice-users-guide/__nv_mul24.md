# libdevice User's Guide

Prototype:


```
i32 @__nv_mul24(i32 %x, i32 %y)
```


Description:


Calculate the least significant 32 bits of the product of the least significant 24 bits of x and y. The high order 8 bits of x and y are ignored.




Returns:


Returns the least significant 32 bits of the product x * y.




Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes