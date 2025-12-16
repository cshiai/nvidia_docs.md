# libdevice User's Guide

Prototype:


```
double @__nv_ddiv_rz(double %x, double %y)
```


Description:


Divides two floating point values x by y in round-towards-zero mode.




Returns:


Returns x / y.

   Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Requires compute capability >= 2.0.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes