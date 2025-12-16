# libdevice User's Guide

Prototype:


```
float @__nv_fsub_ru(float %x, float %y)
```


Description:


Compute the difference of x and y in round-up (to positive infinity) mode.




Returns:


Returns x - y.

   Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


This operation will never be merged into a single multiply-add instruction.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes