# libdevice User's Guide

Prototype:


```
float @__nv_nanf(i8* %tagp)
```


Description:


Return a representation of a quiet NaN. Argument tagp selects one of the possible representations.




Returns:


 - __nv_nanf(tagp) returns NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes