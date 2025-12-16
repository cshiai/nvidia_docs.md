# libdevice User's Guide

Prototype:


```
double @__nv_nan(i8* %tagp)
```


Description:


Return a representation of a quiet NaN. Argument tagp selects one of the possible representations.




Returns:


 - __nv_nan(tagp) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes