# CUDA Driver API

[< Previous](group__CUDA__DEVICE.html) | [Next >](group__CUDA__PRIMARY__CTX.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.6. Device Management [DEPRECATED]


This section describes the device management functions of the low-level CUDA driver application programming interface.


### Functions


CUresult cuDeviceComputeCapability (  int* major, int* minor, CUdevice dev )
Returns the compute capability of the device.

CUresult cuDeviceGetProperties (  CUdevprop* prop, CUdevice dev )
Returns properties for a selected device.


### Functions


CUresult cuDeviceComputeCapability (  int* major, int* minor, CUdevice dev )
Returns the compute capability of the device.

                                 Parameters



major
- Major revision number
minor
- Minor revision number
dev
- Device handle

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_INVALID_DEVICE

Deprecated
This function was deprecated as of CUDA 5.0 and its functionality superseded by cuDeviceGetAttribute().

Description
Returns in *major and *minor the major and minor revision numbers that define the compute capability of the device dev.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuDeviceGetAttribute, cuDeviceGetCount, cuDeviceGetName, cuDeviceGetUuid, cuDeviceGet, cuDeviceTotalMem

CUresult cuDeviceGetProperties (  CUdevprop* prop, CUdevice dev )
Returns properties for a selected device.

                                 Parameters



prop
- Returned properties of device
dev
- Device to get properties for

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_INVALID_DEVICE

Deprecated
This function was deprecated as of CUDA 5.0 and replaced by cuDeviceGetAttribute().

Description
Returns in *prop the properties of device dev. The CUdevprop structure is defined as:


‎     typedef struct CUdevprop_st {
           int maxThreadsPerBlock;
           int maxThreadsDim[3];
           int maxGridSize[3];
           int sharedMemPerBlock;
           int totalConstantMemory;
           int SIMDWidth;
           int memPitch;
           int regsPerBlock;
           int clockRate;
           int textureAlign
        } CUdevprop; where:


maxThreadsPerBlock is the maximum number of threads per block;

maxThreadsDim[3] is the maximum sizes of each dimension of a block;

maxGridSize[3] is the maximum sizes of each dimension of a grid;

sharedMemPerBlock is the total amount of shared memory available per block in bytes;

totalConstantMemory is the total amount of constant memory available on the device in bytes;

SIMDWidth is the warp size;

memPitch is the maximum pitch allowed by the memory copy functions that involve memory regions allocated through cuMemAllocPitch();


regsPerBlock is the total number of registers available per block;

clockRate is the clock frequency in kilohertz;

textureAlign is the alignment requirement; texture base addresses that are aligned to textureAlign bytes do not need an offset
                                          applied to texture fetches.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuDeviceGetAttribute, cuDeviceGetCount, cuDeviceGetName, cuDeviceGetUuid, cuDeviceGet, cuDeviceTotalMem


---