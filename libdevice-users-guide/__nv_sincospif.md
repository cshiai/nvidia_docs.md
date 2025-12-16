# libdevice User's Guide

Prototype:


```
void @__nv_sincospif(float %x, float* %sptr, float* %cptr)
```


Description:


Calculate the sine and cosine of the first input argument, x (measured in radians),  × π  . The results for sine and cosine are written into the second argument, sptr, and, respectively, third argument, zptr.




Returns:


 - none

   See __nv_sinpif() and __nv_cospif().  Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Single-Precision Floating-Point Functions section.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes