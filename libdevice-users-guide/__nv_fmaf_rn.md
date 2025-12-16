# libdevice User's Guide

Prototype:


```
float @__nv_fmaf_rn(float %x, float %y, float %z)
```


Description:


Computes the value of  x × y + z  as a single ternary operation, rounding the result once in round-to-nearest-even mode.




Returns:

 Returns the rounded value of  x × y + z  as a single operation.
 - __nv_fmaf_rn(  ± ∞  ,  ± 0  , z) returns NaN.
 - __nv_fmaf_rn(  ± 0  ,  ± ∞  , z) returns NaN.
 - __nv_fmaf_rn(x, y,  − ∞  ) returns NaN if  x × y  is an exact  + ∞  .
 - __nv_fmaf_rn(x, y,  + ∞  ) returns NaN if  x × y  is an exact  − ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes