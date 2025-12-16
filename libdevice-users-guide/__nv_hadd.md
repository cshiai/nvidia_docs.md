# libdevice User's Guide

Prototype:


```
i32 @__nv_hadd(i32 %x, i32 %y)
```


Description:


Compute average of signed input arguments x and y as ( x + y ) >> 1, avoiding overflow in the intermediate sum.




Returns:


Returns a signed integer value representing the signed average value of the two inputs.




Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes