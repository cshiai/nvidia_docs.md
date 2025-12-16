# libdevice User's Guide

Prototype:


```
float @__nv_asinf(float %x)
```


Description:


Calculate the principal value of the arc sine of the input argument x.




Returns:

 Result will be in radians, in the interval [-  π  /2, +  π  /2] for x inside [-1, +1].
 - __nv_asinf(0) returns +0.
 - __nv_asinf(x) returns NaN for x outside [-1, +1].

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes