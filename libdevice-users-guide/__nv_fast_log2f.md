# libdevice User's Guide

Prototype:


```
float @__nv_fast_log2f(float %x)
```


Description:


Calculate the fast approximate base 2 logarithm of the input argument x.




Returns:


Returns an approximation to   log 2  ⁡ ( x )  .

   Note:
For accuracy information see the CUDA C++ Programming Guide, Mathematical Functions Appendix, Intrinsic Functions section.


Input and output in the denormal range is flushed to sign preserving 0.0.


Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes