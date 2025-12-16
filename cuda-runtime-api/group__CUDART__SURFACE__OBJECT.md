# CUDA Runtime API

[< Previous](group__CUDART__TEXTURE__OBJECT.html) | [Next >](group__CUDART____VERSION.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 6.27. Surface Object Management


This section describes the low level texture object management functions of the CUDA runtime application programming interface. The surface object API is only supported on devices of compute capability 3.0 or higher.


### Functions


__host__
                           ​cudaError_t cudaCreateSurfaceObject (  cudaSurfaceObject_t* pSurfObject, const cudaResourceDesc* pResDesc )
Creates a surface object.

__host__
                           ​cudaError_t cudaDestroySurfaceObject (  cudaSurfaceObject_t surfObject )
Destroys a surface object.

__host__
                           ​cudaError_t cudaGetSurfaceObjectResourceDesc (  cudaResourceDesc* pResDesc, cudaSurfaceObject_t surfObject )
Returns a surface object's resource descriptor Returns the resource descriptor for the surface object specified by surfObject.


### Functions


__host__
                              ​cudaError_t cudaCreateSurfaceObject (  cudaSurfaceObject_t* pSurfObject, const cudaResourceDesc* pResDesc )
Creates a surface object.

                                 Parameters



pSurfObject
- Surface object to create
pResDesc
- Resource descriptor

Returns
cudaSuccess, cudaErrorInvalidValue, cudaErrorInvalidChannelDescriptor, cudaErrorInvalidResourceHandle

Description
Creates a surface object and returns it in pSurfObject. pResDesc describes the data to perform surface load/stores on. cudaResourceDesc::resType must be cudaResourceTypeArray and cudaResourceDesc::res::array::array must be set to a valid CUDA array handle.

Surface objects are only supported on devices of compute capability 3.0 or higher. Additionally, a surface object is an opaque
                                 value, and, as such, should only be accessed through CUDA API calls.


Note:

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


See also:
cudaDestroySurfaceObject, cuSurfObjectCreate

__host__
                              ​cudaError_t cudaDestroySurfaceObject (  cudaSurfaceObject_t surfObject )
Destroys a surface object.

                                 Parameters



surfObject
- Surface object to destroy

Returns
cudaSuccess, cudaErrorInvalidValue

Description
Destroys the surface object specified by surfObject.


Note:

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


Use of the handle after this call is undefined behavior.

See also:
cudaCreateSurfaceObject, cuSurfObjectDestroy

__host__
                              ​cudaError_t cudaGetSurfaceObjectResourceDesc (  cudaResourceDesc* pResDesc, cudaSurfaceObject_t surfObject )
Returns a surface object's resource descriptor Returns the resource descriptor for the surface object specified by surfObject.


                                 Parameters



pResDesc
- Resource descriptor
surfObject
- Surface object

Returns
cudaSuccess, cudaErrorInvalidValue

Description

Note:

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


See also:
cudaCreateSurfaceObject, cuSurfObjectGetResourceDesc


---