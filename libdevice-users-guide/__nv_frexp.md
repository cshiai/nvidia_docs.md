# libdevice User's Guide

Prototype:


```
double @__nv_frexp(double %x, i32* %b)
```


Description:


Decompose the floating-point value x into a component m for the normalized fraction element and another term n for the exponent. The absolute value of m will be greater than or equal to 0.5 and less than 1.0 or it will be equal to 0;  x = m ⋅  2 n   . The integer exponent n will be stored in the location to which nptr points.




Returns:

 Returns the fractional component m.
 - __nv_frexp(0, nptr) returns 0 for the fractional component and zero for the integer component.
 - __nv_frexp(  ± 0  , nptr) returns  ± 0  and stores zero in the location pointed to by nptr.
 - __nv_frexp(  ± ∞  , nptr) returns  ± ∞  and stores an unspecified value in the location to which nptr points.
 - __nv_frexp(NaN, y) returns a NaN and stores an unspecified value in the location to which nptr points.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes