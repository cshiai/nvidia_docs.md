# libdevice User's Guide

Prototype:


```
double @__nv_normcdf(double %x)
```


Description:


Calculate the cumulative distribution function of the standard normal distribution for input argument y,  Φ ( y )  .




Returns:


 - __nv_normcdf(  + ∞  ) returns 1
 - __nv_normcdf(  − ∞  ) returns +0

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes