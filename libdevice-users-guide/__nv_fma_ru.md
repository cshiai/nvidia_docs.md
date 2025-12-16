# libdevice User's Guide

Prototype:


```
double @__nv_fma_ru(double %x, double %y, double %z)
```


Description:


Computes the value of  x × y + z  as a single ternary operation, rounding the result once in round-up (to positive infinity) mode.




Returns:

 Returns the rounded value of  x × y + z  as a single operation.
 - __nv_fma_ru(  ± ∞  ,  ± 0  , z) returns NaN.
 - __nv_fma_ru(  ± 0  ,  ± ∞  , z) returns NaN.
 - __nv_fma_ru(x, y,  − ∞  ) returns NaN if  x × y  is an exact  + ∞


 - __nv_fma_ru(x, y,  + ∞  ) returns NaN if  x × y  is an exact  − ∞

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes