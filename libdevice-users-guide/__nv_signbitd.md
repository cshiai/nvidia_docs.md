# libdevice User's Guide

Prototype:


```
i32 @__nv_signbitd(double %x)
```


Description:


Determine whether the floating-point value x is negative.




Returns:


Returns a nonzero value if and only if x is negative. Reports the sign bit of all values including infinities, zeros, and NaNs.




Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes