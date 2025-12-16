# Debugger API

[< Previous](group__WRITE.html) | [Next >](group__DEV.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 3.7. Grid Properties




### Classes


struct
CUDBGGridInfo
Grid info.


### Enumerations


enum CUDBGGridStatus
Grid status.


### Variables


CUDBGResult
                            ( *CUDBGAPI_st::getBlockDim )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* blockDim )
Get the number of threads in the given block.

CUDBGResult
                            ( *CUDBGAPI_st::getClusterDim )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* clusterDim )
Get the number of blocks in the given cluster.

CUDBGResult
                            ( *CUDBGAPI_st::getClusterDim120 )(  uint32_t dev, uint64_t gridId64, CuDim3* clusterDim )
Get the number of blocks in the given cluster.

CUDBGResult
                            ( *CUDBGAPI_st::getElfImage )(  uint32_t dev, uint32_t sm, uint32_t wp, bool  relocated, voidelfImage, uint64_t* size )
Get the relocated or non-relocated ELF image and size for the grid on the given device.

CUDBGResult
                            ( *CUDBGAPI_st::getElfImage32 )(  uint32_t dev, uint32_t sm, uint32_t wp, bool  relocated, voidelfImage, uint32_t* size )
Get the relocated or non-relocated ELF image and size for the grid on the given device.

CUDBGResult
                            ( *CUDBGAPI_st::getGridAttribute )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGAttribute attr, uint64_t* value )
Get the value of a grid attribute.

CUDBGResult
                            ( *CUDBGAPI_st::getGridAttributes )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGAttributeValuePair* pairs, uint32_t numPairs )
Get several grid attribute values in a single API call.

CUDBGResult
                            ( *CUDBGAPI_st::getGridDim )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* gridDim )
Get the number of blocks in the given grid.

CUDBGResult
                            ( *CUDBGAPI_st::getGridDim32 )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim2* gridDim )
Get the number of blocks in the given grid.

CUDBGResult
                            ( *CUDBGAPI_st::getGridInfo )(  uint32_t dev, uint64_t gridId64, CUDBGGridInfo* gridInfo )
Get information about the specified grid. If the context of the grid has already been destroyed, the function will return
                           CUDBG_ERROR_INVALID_GRID, although the grid id is correct.

CUDBGResult
                            ( *CUDBGAPI_st::getGridInfo120 )(  uint32_t dev, uint64_t gridId64, CUDBGGridInfo120* gridInfo )
Get information about the specified grid. If the context of the grid has already been destroyed, the function will return
                           CUDBG_ERROR_INVALID_GRID, although the grid id is correct.

CUDBGResult
                            ( *CUDBGAPI_st::getGridInfo55 )(  uint32_t dev, uint64_t gridId64, CUDBGGridInfo55* gridInfo )
Get information about the specified grid. If the context of the grid has already been destroyed, the function will return
                           CUDBG_ERROR_INVALID_GRID, although the grid id is correct.

CUDBGResult
                            ( *CUDBGAPI_st::getGridStatus )(  uint32_t dev, uint64_t gridId64, CUDBGGridStatus* status )
Check whether the grid corresponding to the given gridId is still present on the device.

CUDBGResult
                            ( *CUDBGAPI_st::getGridStatus50 )(  uint32_t dev, uint32_t gridId, CUDBGGridStatus* status )
Check whether the grid corresponding to the given gridId is still present on the device.

CUDBGResult
                            ( *CUDBGAPI_st::getTID )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* tid )
Get the ID of the Linux thread hosting the context of the grid.


### Enumerations


enum CUDBGGridStatus
Values



CUDBG_GRID_STATUS_INVALID
An invalid grid ID was passed, or an error occurred during status lookup.
CUDBG_GRID_STATUS_PENDING
The grid was launched but is not running on the HW yet.
CUDBG_GRID_STATUS_ACTIVE
The grid is currently running on the HW.
CUDBG_GRID_STATUS_SLEEPING
The grid is on the device, doing a join.
CUDBG_GRID_STATUS_TERMINATED
The grid has finished executing.
CUDBG_GRID_STATUS_UNDETERMINED
The grid is either QUEUED or TERMINATED.


### Variables


CUDBGResult
                              ( *CUDBGAPI_st::getBlockDim )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* blockDim )
Get the number of threads in the given block.  Since CUDA 3.0.

See also:
getGridDim

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
blockDim
- the returned number of threads in the block

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getClusterDim )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* clusterDim )
Get the number of blocks in the given cluster.  Since CUDA 12.7.

See also:
getBlockDim
getGridDim

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
clusterDim
- the returned number of blocks in the cluster

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getClusterDim120 )(  uint32_t dev, uint64_t gridId64, CuDim3* clusterDim )
Get the number of blocks in the given cluster.  Since CUDA 12.0.

Note:Deprecated in CUDA 12.7.

See also:
getBlockDim
getGridDim

                                 Parameters



dev
- device index
gridId64
- grid ID
clusterDim
- the returned number of blocks in the cluster

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getElfImage )(  uint32_t dev, uint32_t sm, uint32_t wp, bool  relocated, voidelfImage, uint64_t* size )
Get the relocated or non-relocated ELF image and size for the grid on the given device.  Since CUDA 4.0.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
relocated
- set to true to specify the relocated ELF image, false otherwise
*elfImage
- pointer to the ELF image
size
- size of the ELF image (64 bits)

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getElfImage32 )(  uint32_t dev, uint32_t sm, uint32_t wp, bool  relocated, voidelfImage, uint32_t* size )
Get the relocated or non-relocated ELF image and size for the grid on the given device.  Since CUDA 3.0.

Note:Deprecated in CUDA 4.0.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
relocated
- set to true to specify the relocated ELF image, false otherwise
*elfImage
- pointer to the ELF image
size
- size of the ELF image (32 bits)

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getGridAttribute )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGAttribute attr, uint64_t* value )
Get the value of a grid attribute.  Since CUDA 3.1.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
attr
- the attribute
value
- the returned value of the attribute

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_INVALID_ATTRIBUTE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getGridAttributes )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGAttributeValuePair* pairs, uint32_t numPairs )
Get several grid attribute values in a single API call.  Since CUDA 3.1.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
pairs
- array of attribute/value pairs
numPairs
- the number of attribute/values pairs in the array

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_INVALID_ATTRIBUTE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getGridDim )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* gridDim )
Get the number of blocks in the given grid.  Since CUDA 4.0.

See also:
getBlockDim

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
gridDim
- the returned number of blocks in the grid

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getGridDim32 )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim2* gridDim )
Get the number of blocks in the given grid.  Since CUDA 3.0.

Note:Deprecated in CUDA 4.0.

See also:
getBlockDim

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
gridDim
- the returned number of blocks in the grid

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getGridInfo )(  uint32_t dev, uint64_t gridId64, CUDBGGridInfo* gridInfo )
Get information about the specified grid. If the context of the grid has already been destroyed, the function will return
                                 CUDBG_ERROR_INVALID_GRID, although the grid id is correct.  Since CUDA 12.7.


                                 Parameters



dev

gridId64

gridInfo
- pointer to a client allocated structure in which grid info will be returned.

Returns
CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::getGridInfo120 )(  uint32_t dev, uint64_t gridId64, CUDBGGridInfo120* gridInfo )
Get information about the specified grid. If the context of the grid has already been destroyed, the function will return
                                 CUDBG_ERROR_INVALID_GRID, although the grid id is correct.  Since CUDA 12.0.


Note:Deprecated in CUDA 12.3.

                                 Parameters



dev

gridId64

gridInfo
- pointer to a client allocated structure in which grid info will be returned.

Returns
CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::getGridInfo55 )(  uint32_t dev, uint64_t gridId64, CUDBGGridInfo55* gridInfo )
Get information about the specified grid. If the context of the grid has already been destroyed, the function will return
                                 CUDBG_ERROR_INVALID_GRID, although the grid id is correct.  Since CUDA 5.5.


Note:Deprecated in CUDA 12.0.

                                 Parameters



dev

gridId64

gridInfo
- pointer to a client allocated structure in which grid info will be returned.

Returns
CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::getGridStatus )(  uint32_t dev, uint64_t gridId64, CUDBGGridStatus* status )
Check whether the grid corresponding to the given gridId is still present on the device.  Since CUDA 5.5.

                                 Parameters



dev

gridId64
- 64-bit grid ID
status
- enum indicating whether the grid status is INVALID, PENDING, ACTIVE, SLEEPING, TERMINATED or UNDETERMINED

Returns
CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_INTERNAL

CUDBGResult
                              ( *CUDBGAPI_st::getGridStatus50 )(  uint32_t dev, uint32_t gridId, CUDBGGridStatus* status )
Check whether the grid corresponding to the given gridId is still present on the device.  Since CUDA 5.0.

Note:Deprecated in CUDA 5.5.

                                 Parameters



dev

gridId
- grid ID
status
- enum indicating whether the grid status is INVALID, PENDING, ACTIVE, SLEEPING, TERMINATED or UNDETERMINED

Returns
CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_INTERNAL

CUDBGResult
                              ( *CUDBGAPI_st::getTID )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* tid )
Get the ID of the Linux thread hosting the context of the grid.  Since CUDA 3.0.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
tid
- the returned thread id

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_UNINITIALIZED


---