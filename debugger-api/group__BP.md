# Debugger API

[< Previous](group__EXEC.html) | [Next >](group__READ.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 3.4. Breakpoints




### Variables


CUDBGResult
                            ( *CUDBGAPI_st::getAdjustedCodeAddress )(  uint32_t devId, uint64_t address, uint64_t* adjustedAddress, CUDBGAdjAddrAction adjAction )
The client must call this function before inserting a breakpoint, or when the previous or next code address is needed. Returns
                           the adjusted code address for a given code address for a given device.

CUDBGResult
                            ( *CUDBGAPI_st::setBreakpoint )(  uint32_t dev, uint64_t addr )
Sets a breakpoint at the given instruction address for the given device. Before setting a breakpoint, CUDBGAPI_st::getAdjustedCodeAddress
                           should be called to get the adjusted breakpoint address.

CUDBGResult
                            ( *CUDBGAPI_st::setBreakpoint31 )(  uint64_t addr )
Sets a breakpoint at the given instruction address.

CUDBGResult
                            ( *CUDBGAPI_st::unsetBreakpoint )(  uint32_t dev, uint64_t addr )
Unsets a breakpoint at the given instruction address for the given device.

CUDBGResult
                            ( *CUDBGAPI_st::unsetBreakpoint31 )(  uint64_t addr )
Unsets a breakpoint at the given instruction address.


### Variables


CUDBGResult
                              ( *CUDBGAPI_st::getAdjustedCodeAddress )(  uint32_t devId, uint64_t address, uint64_t* adjustedAddress, CUDBGAdjAddrAction adjAction )
The client must call this function before inserting a breakpoint, or when the previous or next code address is needed. Returns
                                 the adjusted code address for a given code address for a given device.  Since CUDA 5.5.


See also:
unsetBreakpoint

                                 Parameters



devId
- the device index
address

adjustedAddress
- adjusted address
adjAction
- whether the adjusted next, previous or current address is needed

Returns
CUDBG_SUCCESS, CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_INVALID_ADDRESS, CUDBG_ERROR_INVALID_DEVICE

CUDBGResult
                              ( *CUDBGAPI_st::setBreakpoint )(  uint32_t dev, uint64_t addr )
Sets a breakpoint at the given instruction address for the given device. Before setting a breakpoint, CUDBGAPI_st::getAdjustedCodeAddress
                                 should be called to get the adjusted breakpoint address.  Since CUDA 3.2.


See also:
unsetBreakpoint

                                 Parameters



dev
- the device index
addr
- instruction address

Returns
CUDBG_SUCCESS, CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_INVALID_ADDRESS, CUDBG_ERROR_INVALID_DEVICE

CUDBGResult
                              ( *CUDBGAPI_st::setBreakpoint31 )(  uint64_t addr )
Sets a breakpoint at the given instruction address.  Since CUDA 3.0.

Note:Deprecated in CUDA 3.2.

See also:
unsetBreakpoint31

                                 Parameters



addr
- instruction address

Returns
CUDBG_SUCCESS, CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_INVALID_ADDRESS

CUDBGResult
                              ( *CUDBGAPI_st::unsetBreakpoint )(  uint32_t dev, uint64_t addr )
Unsets a breakpoint at the given instruction address for the given device.  Since CUDA 3.2.

See also:
setBreakpoint

                                 Parameters



dev
- the device index
addr
- instruction address

Returns
CUDBG_SUCCESS, CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_INVALID_ADDRESS, CUDBG_ERROR_INVALID_DEVICE

CUDBGResult
                              ( *CUDBGAPI_st::unsetBreakpoint31 )(  uint64_t addr )
Unsets a breakpoint at the given instruction address.  Since CUDA 3.0.

Note:Deprecated in CUDA 3.2.

See also:
setBreakpoint31

                                 Parameters



addr
- instruction address

Returns
CUDBG_SUCCESS, CUDBG_ERROR_UNINITIALIZED


---