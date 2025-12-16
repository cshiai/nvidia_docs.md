# libdevice User's Guide

Prototype:


```
i32 @__nv_ilogb(double %x)
```


Description:


Calculates the unbiased integer exponent of the input argument x.




Returns:


 - If successful, returns the unbiased exponent of the argument.
 - __nv_ilogb(0) returns INT_MIN.
 - __nv_ilogb(NaN) returns INT_MIN.
 - __nv_ilogb(x) returns INT_MAX if x is  ∞  or the correct value is greater than INT_MAX.
 - __nv_ilogb(x) return INT_MIN if the correct value is less than INT_MIN.

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes