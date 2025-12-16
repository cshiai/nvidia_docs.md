# Debugger API

[< Previous](group__INIT.html) | [Next >](group__BP.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 3.3. Device Execution Control




### Variables


CUDBGResult
                            ( *CUDBGAPI_st::resumeDevice )(  uint32_t dev )
Resume a suspended CUDA device.

CUDBGResult
                            ( *CUDBGAPI_st::resumeWarpsUntilPC )(  uint32_t devId, uint32_t sm, uint64_t warpMask, uint64_t virtPC )
Inserts a temporary breakpoint at the specified virtual PC, and resumes all warps in the specified bitmask on a given SM.
                           As compared to CUDBGAPI_st::resumeDevice, CUDBGAPI_st::resumeWarpsUntilPC provides finer-grain control by resuming a selected
                           set of warps on the same SM. The main intended usage is to accelerate the single-stepping process when the target PC is known
                           in advance. Instead of single-stepping each warp individually until the target PC is hit, the client can issue this API. When
                           this API is used, errors within CUDA kernels will no longer be reported precisely. In the situation where resuming warps is
                           not possible, this API will return CUDBG_ERROR_WARP_RESUME_NOT_POSSIBLE. The client should then fall back to using CUDBGAPI_st::singleStepWarp
                           or CUDBGAPI_st::resumeDevice.

CUDBGResult
                            ( *CUDBGAPI_st::singleStepWarp )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t laneHint, uint32_t nsteps, uint32_t flags, uint64_t* warpMask )
Single step an individual warp nsteps times on a suspended CUDA device. Only the last instruction in a range should be a control
                           flow instruction.

CUDBGResult
                            ( *CUDBGAPI_st::singleStepWarp40 )(  uint32_t dev, uint32_t sm, uint32_t wp )
Single step an individual warp on a suspended CUDA device.

CUDBGResult
                            ( *CUDBGAPI_st::singleStepWarp41 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t* warpMask )
Single step an individual warp on a suspended CUDA device.

CUDBGResult
                            ( *CUDBGAPI_st::suspendDevice )(  uint32_t dev )
Suspends a running CUDA device.


### Variables


CUDBGResult
                              ( *CUDBGAPI_st::resumeDevice )(  uint32_t dev )
Resume a suspended CUDA device.  Since CUDA 3.0.

See also:
suspendDevice
singleStepWarp

                                 Parameters



dev
- device index

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_RUNNING_DEVICE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::resumeWarpsUntilPC )(  uint32_t devId, uint32_t sm, uint64_t warpMask, uint64_t virtPC )
Inserts a temporary breakpoint at the specified virtual PC, and resumes all warps in the specified bitmask on a given SM.
                                 As compared to CUDBGAPI_st::resumeDevice, CUDBGAPI_st::resumeWarpsUntilPC provides finer-grain control by resuming a selected
                                 set of warps on the same SM. The main intended usage is to accelerate the single-stepping process when the target PC is known
                                 in advance. Instead of single-stepping each warp individually until the target PC is hit, the client can issue this API. When
                                 this API is used, errors within CUDA kernels will no longer be reported precisely. In the situation where resuming warps is
                                 not possible, this API will return CUDBG_ERROR_WARP_RESUME_NOT_POSSIBLE. The client should then fall back to using CUDBGAPI_st::singleStepWarp
                                 or CUDBGAPI_st::resumeDevice.  Since CUDA 6.0.


See also:
resumeDevice

                                 Parameters



devId
- device index
sm
- the SM index
warpMask
- the bitmask of warps to resume (1 = resume, 0 = do not resume)
virtPC
- the virtual PC where the temporary breakpoint will be inserted

Returns
CUDBG_SUCCESS CUDBG_ERROR_INVALID_ARGS CUDBG_ERROR_INVALID_DEVICE CUDBG_ERROR_INVALID_SM CUDBG_ERROR_INVALID_WARP_MASK CUDBG_ERROR_WARP_RESUME_NOT_POSSIBLE
                                 CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::singleStepWarp )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t laneHint, uint32_t nsteps, uint32_t flags, uint64_t* warpMask )
Single step an individual warp nsteps times on a suspended CUDA device. Only the last instruction in a range should be a control
                                 flow instruction.  Since CUDA 7.5.


See also:
resumeDevice
suspendDevice

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
laneHint

nsteps
- number of single steps
flags

warpMask
- the warps that have been single-stepped

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_RUNNING_DEVICE, CUDBG_ERROR_UNINITIALIZED,
                                 CUDBG_ERROR_UNKNOWN

CUDBGResult
                              ( *CUDBGAPI_st::singleStepWarp40 )(  uint32_t dev, uint32_t sm, uint32_t wp )
Single step an individual warp on a suspended CUDA device.  Since CUDA 3.0.

Note:Deprecated in CUDA 4.1.

See also:
resumeDevice
suspendDevice
singleStepWarp

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_RUNNING_DEVICE, CUDBG_ERROR_UNINITIALIZED,
                                 CUDBG_ERROR_UNKNOWN, CUDBG_ERROR_WARP_RESUME_NOT_POSSIBLE

CUDBGResult
                              ( *CUDBGAPI_st::singleStepWarp41 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t* warpMask )
Single step an individual warp on a suspended CUDA device.  Since CUDA 4.1.

Note:Deprecated in CUDA 7.5.

See also:
resumeDevice
suspendDevice

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
warpMask
- the warps that have been single-stepped

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_RUNNING_DEVICE, CUDBG_ERROR_UNINITIALIZED,
                                 CUDBG_ERROR_UNKNOWN

CUDBGResult
                              ( *CUDBGAPI_st::suspendDevice )(  uint32_t dev )
Suspends a running CUDA device.  Since CUDA 3.0.

See also:
resumeDevice
singleStepWarp

                                 Parameters



dev
- device index

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_RUNNING_DEVICE, CUDBG_ERROR_UNINITIALIZED


---