# CUDA Driver API

[< Previous](group__CUDA__MODULE.html) | [Next >](group__CUDA__LIBRARY.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.11. Module Management [DEPRECATED]


This section describes the deprecated module management functions of the low-level CUDA driver application programming interface.


### Functions


CUresult cuModuleGetSurfRef (  CUsurfref* pSurfRef, CUmodule hmod, const char* name )
Returns a handle to a surface reference.

CUresult cuModuleGetTexRef (  CUtexref* pTexRef, CUmodule hmod, const char* name )
Returns a handle to a texture reference.


### Functions


CUresult cuModuleGetSurfRef (  CUsurfref* pSurfRef, CUmodule hmod, const char* name )
Returns a handle to a surface reference.

                                 Parameters



pSurfRef
- Returned surface reference
hmod
- Module to retrieve surface reference from
name
- Name of surface reference to retrieve

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_NOT_FOUND

Deprecated

DescriptionReturns in *pSurfRef the handle of the surface reference of name name in the module hmod. If no surface reference of that name exists, cuModuleGetSurfRef() returns CUDA_ERROR_NOT_FOUND.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuModuleGetFunction, cuModuleGetGlobal, cuModuleGetTexRef, cuModuleLoad, cuModuleLoadData, cuModuleLoadDataEx, cuModuleLoadFatBinary, cuModuleUnload

CUresult cuModuleGetTexRef (  CUtexref* pTexRef, CUmodule hmod, const char* name )
Returns a handle to a texture reference.

                                 Parameters



pTexRef
- Returned texture reference
hmod
- Module to retrieve texture reference from
name
- Name of texture reference to retrieve

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE, CUDA_ERROR_NOT_FOUND

Deprecated

DescriptionReturns in *pTexRef the handle of the texture reference of name name in the module hmod. If no texture reference of that name exists, cuModuleGetTexRef() returns CUDA_ERROR_NOT_FOUND. This texture reference handle should not be destroyed, since it will be destroyed when the module is unloaded.


Note:Note that this function may also return error codes from previous, asynchronous launches.

See also:
cuModuleGetFunction, cuModuleGetGlobal, cuModuleGetSurfRef, cuModuleLoad, cuModuleLoadData, cuModuleLoadDataEx, cuModuleLoadFatBinary, cuModuleUnload


---