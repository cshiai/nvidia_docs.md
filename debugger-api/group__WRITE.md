# Debugger API

[< Previous](group__READ.html) | [Next >](group__GRID.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 3.6. Device State Alteration




### Variables


CUDBGResult
                            ( *CUDBGAPI_st::writeCCRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t val )
Writes the hardware CC register.

CUDBGResult
                            ( *CUDBGAPI_st::writeGenericMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, const void* buf, uint32_t sz )
Writes content to an address in the generic address space. This function determines if the given address falls into the local,
                           shared, or global memory window. It then accesses memory taking into account the hardware co-ordinates provided as inputs.

CUDBGResult
                            ( *CUDBGAPI_st::writeGlobalMemory )(  uint64_t addr, const void* buf, uint32_t sz )
Writes content to an address in the global address space. If the address is valid on more than one device and one of those
                           devices does not support UVA, an error is returned.

CUDBGResult
                            ( *CUDBGAPI_st::writeGlobalMemory31 )(  uint32_t dev, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the global memory segment.

CUDBGResult
                            ( *CUDBGAPI_st::writeGlobalMemory55 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the global memory segment (entire 40-bit VA on Fermi+).

CUDBGResult
                            ( *CUDBGAPI_st::writeLocalMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the local memory segment.

CUDBGResult
                            ( *CUDBGAPI_st::writeParamMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the param memory segment.

CUDBGResult
                            ( *CUDBGAPI_st::writeRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t regno, uint32_t val )
Writes content to a hardware register.

CUDBGResult
                            ( *CUDBGAPI_st::writeSharedMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the shared memory segment.

CUDBGResult
                            ( *CUDBGAPI_st::writeUniformRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t regno, uint32_t val )
Writes content to a uniform register.


### Variables


CUDBGResult
                              ( *CUDBGAPI_st::writeCCRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t val )
Writes the hardware CC register.  Since CUDA 6.5.

See also:
writeConstMemory
writeGenericMemory
writeGlobalMemory
writeParamMemory
writeSharedMemory
writeTextureMemory
writeLocalMemory
writeRegister
writePredicates

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
val
- value to write to the CC register

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::writeGenericMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, const void* buf, uint32_t sz )
Writes content to an address in the generic address space. This function determines if the given address falls into the local,
                                 shared, or global memory window. It then accesses memory taking into account the hardware co-ordinates provided as inputs.
                                 Since CUDA 6.0.


See also:
writeParamMemory
writeSharedMemory
writeLocalMemory
writeRegister

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
addr
- memory address
buf
- buffer
sz

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_MEMORY_MAPPING_FAILED, CUDBG_ERROR_ADDRESS_NOT_IN_DEVICE_MEM

CUDBGResult
                              ( *CUDBGAPI_st::writeGlobalMemory )(  uint64_t addr, const void* buf, uint32_t sz )
Writes content to an address in the global address space. If the address is valid on more than one device and one of those
                                 devices does not support UVA, an error is returned.  Since CUDA 6.0.


See also:
writeParamMemory
writeSharedMemory
writeLocalMemory
writeRegister

                                 Parameters



addr
- memory address
buf
- buffer
sz

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_MEMORY_MAPPING_FAILED,
                                 CUDBG_ERROR_INVALID_MEMORY_ACCESS, CUDBG_ERROR_ADDRESS_NOT_IN_DEVICE_MEM CUDBG_ERROR_AMBIGUOUS_MEMORY_ADDRESS_

CUDBGResult
                              ( *CUDBGAPI_st::writeGlobalMemory31 )(  uint32_t dev, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the global memory segment.  Since CUDA 3.0.

Note:Deprecated in CUDA 3.2.

See also:
writeParamMemory
writeSharedMemory
writeLocalMemory
writeRegister

                                 Parameters



dev
- device index
addr
- memory address
buf
- buffer
sz
- size of the buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_MEMORY_MAPPING_FAILED

CUDBGResult
                              ( *CUDBGAPI_st::writeGlobalMemory55 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the global memory segment (entire 40-bit VA on Fermi+).  Since CUDA 3.2.

Note:Deprecated in CUDA 6.0.

See also:
writeParamMemory
writeSharedMemory
writeLocalMemory
writeRegister

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
addr
- memory address
buf
- buffer
sz
- size of the buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_MEMORY_MAPPING_FAILED, CUDBG_ERROR_ADDRESS_NOT_IN_DEVICE_MEM

CUDBGResult
                              ( *CUDBGAPI_st::writeLocalMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the local memory segment.  Since CUDA 3.0.

See also:
writeGenericMemory
writeParamMemory
writeSharedMemory
writeRegister

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
addr
- memory address
buf
- buffer
sz
- size of the buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_MEMORY_MAPPING_FAILED

CUDBGResult
                              ( *CUDBGAPI_st::writeParamMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the param memory segment.  Since CUDA 3.0.

See also:
writeGenericMemory
writeSharedMemory
writeLocalMemory
writeRegister

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
addr
- memory address
buf
- buffer
sz
- size of the buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED,
                                 CUDBG_ERROR_MEMORY_MAPPING_FAILED

CUDBGResult
                              ( *CUDBGAPI_st::writeRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t regno, uint32_t val )
Writes content to a hardware register.  Since CUDA 3.0.

See also:
writeGenericMemory
writeParamMemory
writeSharedMemory
writeLocalMemory

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
regno
- register index
val
- buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::writeSharedMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the shared memory segment.  Since CUDA 3.0.

See also:
writeGenericMemory
writeParamMemory
writeLocalMemory
writeRegister

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
addr
- memory address
buf
- buffer
sz
- size of the buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED,
                                 CUDBG_ERROR_MEMORY_MAPPING_FAILED

CUDBGResult
                              ( *CUDBGAPI_st::writeUniformRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t regno, uint32_t val )
Writes content to a uniform register.  Since CUDA 10.0.

See also:
writeRegister
readUniformRegisterRange

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
regno
- register index
val
- buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED


---