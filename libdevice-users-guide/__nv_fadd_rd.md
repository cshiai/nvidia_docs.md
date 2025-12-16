# libdevice User's Guide

Prototype:


```
float @__nv_fadd_rd(float %x, float %y)
```


Description:


Compute the sum of x and y in round-down (to negative infinity) mode.




Returns:


Returns x + y.

   Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


This operation will never be merged into a single multiply-add instruction.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes