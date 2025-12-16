# CUDA Driver API

[< Previous](structCUaccessPolicyWindow__v1.html) | [Next >](structCUasyncNotificationInfo.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.3. CUarrayMapInfo_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Specifies the CUDA array or CUDA mipmapped array memory mapping information


### Public Variables


unsigned int  deviceBitMaskunsigned int  extentDepthunsigned int  extentHeightunsigned int  extentWidthunsigned int  flagsunsigned int  layerunsigned int  levelCUmemHandleType memHandleTypeCUmemOperationType memOperationTypeunsigned long long  offsetunsigned int  offsetXunsigned int  offsetYunsigned int  offsetZunsigned int  reserved[2]CUresourcetype resourceTypeunsigned long long  sizeCUarraySparseSubresourceType subresourceType

### Variables


unsigned int  CUarrayMapInfo_v1::deviceBitMask [inherited]
Device ordinal bit mask

unsigned int  CUarrayMapInfo_v1::extentDepth [inherited]
Depth in elements

unsigned int  CUarrayMapInfo_v1::extentHeight [inherited]
Height in elements

unsigned int  CUarrayMapInfo_v1::extentWidth [inherited]
Width in elements

unsigned int  CUarrayMapInfo_v1::flags [inherited]
flags for future use, must be zero now.

unsigned int  CUarrayMapInfo_v1::layer [inherited]
For CUDA layered arrays must be a valid layer index. Otherwise, must be zero

unsigned int  CUarrayMapInfo_v1::level [inherited]
For CUDA mipmapped arrays must a valid mipmap level. For CUDA arrays must be zero

CUmemHandleTypeCUarrayMapInfo_v1::memHandleType [inherited]
Memory handle type

CUmemOperationTypeCUarrayMapInfo_v1::memOperationType [inherited]
Memory operation type

unsigned long long  CUarrayMapInfo_v1::offset [inherited]
Offset within mip tail
Offset within the memory

unsigned int  CUarrayMapInfo_v1::offsetX [inherited]
Starting X offset in elements

unsigned int  CUarrayMapInfo_v1::offsetY [inherited]
Starting Y offset in elements

unsigned int  CUarrayMapInfo_v1::offsetZ [inherited]
Starting Z offset in elements

unsigned int  CUarrayMapInfo_v1::reserved[2] [inherited]
Reserved for future use, must be zero now.

CUresourcetypeCUarrayMapInfo_v1::resourceType [inherited]
Resource type

unsigned long long  CUarrayMapInfo_v1::size [inherited]
Extent in bytes

CUarraySparseSubresourceTypeCUarrayMapInfo_v1::subresourceType [inherited]
Sparse subresource type


---