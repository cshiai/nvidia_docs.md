# libdevice User's Guide

Prototype:


```
float @__nv_acosf(float %x)
```


Description:


Calculate the principal value of the arc cosine of the input argument x.




Returns:

 Result will be in radians, in the interval [0,  π  ] for x inside [-1, +1].
 - __nv_acosf(1) returns +0.
 - __nv_acosf(x) returns NaN for x outside [-1, +1].

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes