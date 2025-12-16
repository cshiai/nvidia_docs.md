# libdevice User's Guide

Prototype:


```
double @__nv_modf(double %x, double* %b)
```


Description:


Break down the argument x into fractional and integral parts. The integral part is stored in the argument iptr. Fractional and integral parts are given the same sign as the argument x.




Returns:


 - __nv_modf(  ± x  , iptr) returns a result with the same sign as x.
 - __nv_modf(  ± ∞  , iptr) returns  ± 0  and stores  ± ∞  in the object pointed to by iptr.
 - __nv_modf(NaN, iptr) stores a NaN in the object pointed to by iptr and returns a NaN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes