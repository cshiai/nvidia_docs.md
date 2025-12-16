# CUDA Driver API

[< Previous](group__CUDA__TYPES.html) | [Next >](group__CUDA__INITIALIZE.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.2. Error Handling


This section describes the error handling functions of the low-level CUDA driver application programming interface.


### Functions


CUresult cuGetErrorName (  CUresult error, const char pStr )
Gets the string representation of an error code enum name.

CUresult cuGetErrorString (  CUresult error, const char pStr )
Gets the string description of an error code.


### Functions


CUresult cuGetErrorName (  CUresult error, const char pStr )
Gets the string representation of an error code enum name.

                                 Parameters



error
- Error code to convert to string
pStr
- Address of the string pointer.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE

Description
Sets *pStr to the address of a NULL-terminated string representation of the name of the enum error code error. If the error code is not recognized, CUDA_ERROR_INVALID_VALUE will be returned and *pStr will be set to the NULL address.


See also:
CUresult, cudaGetErrorName

CUresult cuGetErrorString (  CUresult error, const char pStr )
Gets the string description of an error code.

                                 Parameters



error
- Error code to convert to string
pStr
- Address of the string pointer.

Returns
CUDA_SUCCESS, CUDA_ERROR_INVALID_VALUE

Description
Sets *pStr to the address of a NULL-terminated string description of the error code error. If the error code is not recognized, CUDA_ERROR_INVALID_VALUE will be returned and *pStr will be set to the NULL address.


See also:
CUresult, cudaGetErrorString


---