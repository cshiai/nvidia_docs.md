# Debugger API

[< Previous](group__GRID.html) | [Next >](group__DWARF.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 3.8. Device Properties




### Variables


CUDBGResult
                            ( *CUDBGAPI_st::getDeviceName )(  uint32_t dev, char* buf, uint32_t sz )
Get the device name string.

CUDBGResult
                            ( *CUDBGAPI_st::getDeviceType )(  uint32_t dev, char* buf, uint32_t sz )
Get the string description of the device.

CUDBGResult
                            ( *CUDBGAPI_st::getNumDevices )(  uint32_t* numDev )
Get the number of installed CUDA devices.

CUDBGResult
                            ( *CUDBGAPI_st::getNumLanes )(  uint32_t dev, uint32_t* numLanes )
Get the number of lanes per warp on the device.

CUDBGResult
                            ( *CUDBGAPI_st::getNumPredicates )(  uint32_t dev, uint32_t* numPredicates )
Get the number of predicate registers per lane on the device.

CUDBGResult
                            ( *CUDBGAPI_st::getNumRegisters )(  uint32_t dev, uint32_t* numRegs )
Get the number of registers per lane on the device.

CUDBGResult
                            ( *CUDBGAPI_st::getNumSMs )(  uint32_t dev, uint32_t* numSMs )
Get the total number of SMs on the device.

CUDBGResult
                            ( *CUDBGAPI_st::getNumUniformPredicates )(  uint32_t dev, uint32_t* numPredicates )
Get the number of uniform predicate registers per warp on the device.

CUDBGResult
                            ( *CUDBGAPI_st::getNumUniformRegisters )(  uint32_t dev, uint32_t* numRegs )
Get the number of uniform registers per warp on the device.

CUDBGResult
                            ( *CUDBGAPI_st::getNumWarps )(  uint32_t dev, uint32_t* numWarps )
Get the number of warps per SM on the device.

CUDBGResult
                            ( *CUDBGAPI_st::getSmType )(  uint32_t dev, char* buf, uint32_t sz )
Get the SM type of the device.


### Variables


CUDBGResult
                              ( *CUDBGAPI_st::getDeviceName )(  uint32_t dev, char* buf, uint32_t sz )
Get the device name string.  Since CUDA 6.5.

See also:
getSMType
getDeviceType

                                 Parameters



dev
- device index
buf
- the destination buffer
sz
- the size of the buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_BUFFER_TOO_SMALL, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getDeviceType )(  uint32_t dev, char* buf, uint32_t sz )
Get the string description of the device.  Since CUDA 3.0.

See also:
getSMType

                                 Parameters



dev
- device index
buf
- the destination buffer
sz
- the size of the buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_BUFFER_TOO_SMALL, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getNumDevices )(  uint32_t* numDev )
Get the number of installed CUDA devices.  Since CUDA 3.0.

See also:
getNumSMs
getNumWarps
getNumLanes
getNumRegisters

                                 Parameters



numDev
- the returned number of devices

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getNumLanes )(  uint32_t dev, uint32_t* numLanes )
Get the number of lanes per warp on the device.  Since CUDA 3.0.

See also:
getNumDevices
getNumSMs
getNumWarps
getNumRegisters

                                 Parameters



dev
- device index
numLanes
- the returned number of lanes

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getNumPredicates )(  uint32_t dev, uint32_t* numPredicates )
Get the number of predicate registers per lane on the device.  Since CUDA 6.5.

See also:
getNumDevices
getNumSMs
getNumWarps
getNumLanes
getNumRegisters

                                 Parameters



dev
- device index
numPredicates
- the returned number of predicate registers

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getNumRegisters )(  uint32_t dev, uint32_t* numRegs )
Get the number of registers per lane on the device.  Since CUDA 3.0.

See also:
getNumDevices
getNumSMs
getNumWarps
getNumLanes

                                 Parameters



dev
- device index
numRegs
- the returned number of registers

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getNumSMs )(  uint32_t dev, uint32_t* numSMs )
Get the total number of SMs on the device.  Since CUDA 3.0.

See also:
getNumDevices
getNumWarps
getNumLanes
getNumRegisters

                                 Parameters



dev
- device index
numSMs
- the returned number of SMs

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getNumUniformPredicates )(  uint32_t dev, uint32_t* numPredicates )
Get the number of uniform predicate registers per warp on the device.  Since CUDA 10.0.

See also:
getNumUniformPredicates

                                 Parameters



dev
- device index
numPredicates
- the returned number of uniform predicate registers

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getNumUniformRegisters )(  uint32_t dev, uint32_t* numRegs )
Get the number of uniform registers per warp on the device.  Since CUDA 10.0.

See also:
getNumRegisters

                                 Parameters



dev
- device index
numRegs
- the returned number of uniform registers

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getNumWarps )(  uint32_t dev, uint32_t* numWarps )
Get the number of warps per SM on the device.  Since CUDA 3.0.

See also:
getNumDevices
getNumSMs
getNumLanes
getNumRegisters

                                 Parameters



dev
- device index
numWarps
- the returned number of warps

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getSmType )(  uint32_t dev, char* buf, uint32_t sz )
Get the SM type of the device.  Since CUDA 3.0.

See also:
getDeviceType

                                 Parameters



dev
- device index
buf
- the destination buffer
sz
- the size of the buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_BUFFER_TOO_SMALL, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED


---