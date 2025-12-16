# libdevice User's Guide

Prototype:


```
double @__nv_dadd_rn(double %x, double %y)
```


Description:


Adds two floating point values x and y in round-to-nearest-even mode.




Returns:


Returns x + y.

   Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


This operation will never be merged into a single multiply-add instruction.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes