# libdevice User's Guide

Prototype:


```
i32 @__nv_byte_perm(i32 %x, i32 %y, i32 %z)
```


Description:


__nv_byte_perm(x,y,s) returns a 32-bit integer consisting of four bytes from eight input bytes provided in the two input integers x and y, as specified by a selector, s.


The input bytes are indexed as follows:


```
input[0] = x<7:0>   input[1] = x<15:8>
 input[2] = x<23:16> input[3] = x<31:24>
 input[4] = y<7:0>   input[5] = y<15:8>
 input[6] = y<23:16> input[7] = y<31:24>
```


The selector indices are as follows (the upper 16-bits of the selector are not used):


```
selector[0] = s<2:0>  selector[1] = s<6:4>
 selector[2] = s<10:8> selector[3] = s<14:12>
```




Returns:


The returned value r is computed to be: result[n] := input[selector[n]] where result[n] is the nth byte of r.




Library Availability:


Compute 2.0: Yes


Compute 3.0: Yes


Compute 3.5: Yes