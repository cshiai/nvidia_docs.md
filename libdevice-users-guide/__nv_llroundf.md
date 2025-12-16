# libdevice User's Guide

Prototype:


```
i64 @__nv_llroundf(float %x)
```


Description:


Round x to the nearest integer value, with halfway cases rounded away from zero. If the result is outside the range of the return type, the result is undefined.




Returns:


Returns rounded integer value.

   Note:
This function may be slower than alternate rounding methods. See llrint().


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes