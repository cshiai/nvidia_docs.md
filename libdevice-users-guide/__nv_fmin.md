# libdevice User's Guide

Prototype:


```
double @__nv_fmin(double %x, double %y)
```


Description:


Determines the minimum numeric value of the arguments x and y. Treats NaN arguments as missing data. If one argument is a NaN and the other is legitimate numeric value, the numeric value is chosen.




Returns:

 Returns the minimum numeric values of the arguments x and y.
 - If both arguments are NaN, returns NaN.
 - If one argument is NaN, returns the numeric argument.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes