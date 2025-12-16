# CUDA Driver API

[< Previous](group__CUDA__TEXREF__DEPRECATED.html) | [Next >](group__CUDA__TEXOBJECT.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.27. Surface Reference Management [DEPRECATED]


This section describes the surface reference management functions of the low-level CUDA driver application programming interface.


### Functions


CUresult cuSurfRefGetArray (  CUarray* phArray, CUsurfref hSurfRef )
Passes back the CUDA array bound to a surface reference.

CUresult cuSurfRefSetArray (  CUsurfref hSurfRef, CUarray hArray, unsigned int  Flags )
Sets the CUDA array for a surface reference.


### Functions


CUresult cuSurfRefGetArray (  CUarray* phArray, CUsurfref hSurfRef )
Passes back the CUDA array bound to a surface reference.

                                 Parameters



phArray
- Surface reference handle
hSurfRef
- Surface reference handle

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE

Deprecated

DescriptionReturns in *phArray the CUDA array bound to the surface reference hSurfRef, or returns CUDA_ERROR_INVALID_VALUE if the surface reference is not bound to any CUDA array.


See also:
cuModuleGetSurfRef, cuSurfRefSetArray

CUresult cuSurfRefSetArray (  CUsurfref hSurfRef, CUarray hArray, unsigned int  Flags )
Sets the CUDA array for a surface reference.

                                 Parameters



hSurfRef
- Surface reference handle
hArray
- CUDA array handle
Flags
- set to 0

Returns
CUDA_SUCCESS, CUDA_ERROR_DEINITIALIZED, CUDA_ERROR_NOT_INITIALIZED, CUDA_ERROR_INVALID_CONTEXT, CUDA_ERROR_INVALID_VALUE

Deprecated

DescriptionSets the CUDA array hArray to be read and written by the surface reference hSurfRef. Any previous CUDA array state associated with the surface reference is superseded by this function. Flags must be set to 0. The CUDA_ARRAY3D_SURFACE_LDST flag must have been set for the CUDA array. Any CUDA array previously bound to hSurfRef is unbound.


See also:
cuModuleGetSurfRef, cuSurfRefGetArray


---