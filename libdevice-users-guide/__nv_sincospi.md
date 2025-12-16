# libdevice User's Guide

Prototype:


```
void @__nv_sincospi(double %x, double* %sptr, double* %cptr)
```


Description:


Calculate the sine and cosine of the first input argument, x (measured in radians),  × π  . The results for sine and cosine are written into the second argument, sptr, and, respectively, third argument, zptr.




Returns:


 - none

   See __nv_sinpi() and __nv_cospi().  Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Double-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes