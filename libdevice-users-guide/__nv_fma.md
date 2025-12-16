# libdevice User's Guide

Prototype:


```
double @__nv_fma(double %x, double %y, double %z)
```


Description:


Compute the value of  x × y + z  as a single ternary operation. After computing the value to infinite precision, the value is rounded once.




Returns:

 Returns the rounded value of  x × y + z  as a single operation.
 - __nv_fma(  ± ∞  ,  ± 0  , z) returns NaN.
 - __nv_fma(  ± 0  ,  ± ∞  , z) returns NaN.
 - __nv_fma(x, y,  − ∞  ) returns NaN if  x × y  is an exact  + ∞  .
 - __nv_fma(x, y,  + ∞  ) returns NaN if  x × y  is an exact  − ∞  .

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes