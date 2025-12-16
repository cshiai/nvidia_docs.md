# libdevice User's Guide

Prototype:


```
float @__nv_atan2f(float %x, float %y)
```


Description:


Calculate the principal value of the arc tangent of the ratio of first and second input arguments x / y. The quadrant of the result is determined by the signs of inputs x and y.




Returns:

 Result will be in radians, in the interval [-  π  /, +  π  ].
 - __nv_atan2f(0, 1) returns +0.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes