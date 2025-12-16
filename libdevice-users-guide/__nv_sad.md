# libdevice User's Guide

Prototype:


```
i32 @__nv_sad(i32 %x, i32 %y, i32 %z)
```


Description:


Calculate   |  x − y  |  + z  , the 32-bit sum of the third argument z plus and the absolute value of the difference between the first argument, x, and second argument, y.


Inputs x and y are signed 32-bit integers, input z is a 32-bit unsigned integer.




Returns:


Returns   |  x − y  |  + z  .




Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes