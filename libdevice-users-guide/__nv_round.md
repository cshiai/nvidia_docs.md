# libdevice User's Guide

Prototype:


```
double @__nv_round(double %x)
```


Description:


Round x to the nearest integer value in floating-point format, with halfway cases rounded away from zero.




Returns:


Returns rounded integer value.

   Note:
This function may be slower than alternate rounding methods. See rint().


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes