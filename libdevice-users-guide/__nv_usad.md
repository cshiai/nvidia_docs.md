# libdevice User's Guide

Prototype:


```
i32 @__nv_usad(i32 %x, i32 %y, i32 %z)
```


Description:


Calculate   |  x − y  |  + z  , the 32-bit sum of the third argument z plus and the absolute value of the difference between the first argument, x, and second argument, y.


Inputs x, y, and z are unsigned 32-bit integers.




Returns:


Returns   |  x − y  |  + z  .




Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes