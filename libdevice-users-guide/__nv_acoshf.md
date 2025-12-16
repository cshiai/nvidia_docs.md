# libdevice User's Guide

Prototype:


```
float @__nv_acoshf(float %x)
```


Description:


Calculate the nonnegative arc hyperbolic cosine of the input argument x.




Returns:

 Result will be in the interval [0,  + ∞  ].
 - __nv_acoshf(1) returns 0.
 - __nv_acoshf(x) returns NaN for x in the interval [  − ∞  , 1).

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes