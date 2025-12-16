# libdevice User's Guide

Prototype:


```
double @__nv_hypot(double %x, double %y)
```


Description:


Calculate the length of the hypotenuse of a right triangle whose two sides have lengths x and y without undue overflow or underflow.




Returns:


Returns the length of the hypotenuse    x 2  +  y 2    . If the correct value would overflow, returns  + ∞  . If the correct value would underflow, returns 0. If one of the input arguments is 0, returns the other argument

   Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes