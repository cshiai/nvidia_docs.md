# libdevice User's Guide

Prototype:


```
void @__nv_fast_sincosf(float %x, float* %sptr, float* %cptr)
```


Description:


Calculate the fast approximate of sine and cosine of the first input argument x (measured in radians). The results for sine and cosine are written into the second argument, sptr, and, respectively, third argument, zptr.




Returns:


 - none

    Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Intrinsic Functions section.


Denorm input/output is flushed to sign preserving 0.0.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes