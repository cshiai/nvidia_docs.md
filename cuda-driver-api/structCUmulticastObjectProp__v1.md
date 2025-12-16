# CUDA Driver API

[< Previous](structCUmemPoolPtrExportData__v1.html) | [Next >](structCUoffset3D__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.79. CUmulticastObjectProp_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Specifies the properties for a multicast object.


### Public Variables


unsigned long long  flagsunsigned long long  handleTypesunsigned int  numDevicessize_t  size

### Variables


unsigned long long  CUmulticastObjectProp_v1::flags [inherited]
Flags for future use, must be zero now

unsigned long long  CUmulticastObjectProp_v1::handleTypes [inherited]
Bitmask of exportable handle types (see CUmemAllocationHandleType) for this object

unsigned int  CUmulticastObjectProp_v1::numDevices [inherited]
The number of devices in the multicast team that will bind memory to this object

size_t  CUmulticastObjectProp_v1::size [inherited]
The maximum amount of memory that can be bound to this multicast object per device


---