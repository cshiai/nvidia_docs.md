# libdevice User's Guide

Prototype:


```
double @__nv_drcp_rd(double %x)
```


Description:


Compute the reciprocal of x in round-down (to negative infinity) mode.




Returns:


Returns   1 x   .

   Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Requires compute capability >= 2.0.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes