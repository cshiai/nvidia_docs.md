# Debugger API

[< Previous](group__BP.html) | [Next >](group__WRITE.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 3.5. Device State Inspection




### Variables


CUDBGResult
                            ( *CUDBGAPI_st::consumeCudaLogs )(  CUDBGCudaLogMessage* logMessages, uint32_t numMessages, uint32_t* numConsumed )
Get CUDA error log entries. This consumes the log entries, so they will not be available in subsequent calls.

CUDBGResult
                            ( *CUDBGAPI_st::generateCoredump )(  const char* filename, CUDBGCoredumpGenerationFlags flags )
Generates a coredump for the current GPU state.

CUDBGResult
                            ( *CUDBGAPI_st::getCbuWarpState )(  uint32_t dev, uint32_t sm, uint64_t warpMask, CUDBGCbuWarpState* warpStates, uint32_t numWarpStates )
Gets CBU state of a given warp.

CUDBGResult
                            ( *CUDBGAPI_st::getClusterExceptionTargetBlock )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* blockIdx, bool* blockIdxValid )
Retrieves the target block index and validity status for a given device, streaming multiprocessor, and warp for cluster exceptions.

CUDBGResult
                            ( *CUDBGAPI_st::getConstBankAddress )(  uint32_t dev, uint64_t gridId64, uint32_t bank, uint64_t* address, uint32_t* size )
Get constant bank GPU VA and size.

CUDBGResult
                            ( *CUDBGAPI_st::getConstBankAddress123 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t bank, uint32_t offset, uint64_t* address )
Convert constant bank number and offset into GPU VA.

CUDBGResult
                            ( *CUDBGAPI_st::getCudaExceptionString )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, char* buf, uint32_t bufSz, uint32_t* msgSz )
Get error string for CUDA Exceptions.

CUDBGResult
                            ( *CUDBGAPI_st::getHardwareBarrierInfo )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, CUDBGBarrierScope* scope, char* buf, uint32_t bufSz, uint32_t* msgSz )
Get hardware barrier information.

CUDBGResult
                            ( *CUDBGAPI_st::getLoadedFunctionInfo )(  uint32_t devId, uint64_t handle, CUDBGLoadedFunctionInfo* info, uint32_t startIndex, uint32_t numEntries )
Get the section number and address of loaded functions for a given module.

CUDBGResult
                            ( *CUDBGAPI_st::getLoadedFunctionInfo118 )(  uint32_t devId, uint64_t handle, CUDBGLoadedFunctionInfo* info, uint32_t numEntries )
Get the section number and address of loaded functions for a given module.

CUDBGResult
                            ( *CUDBGAPI_st::getManagedMemoryRegionInfo )(  uint64_t startAddress, CUDBGMemoryInfo* memoryInfo, uint32_t memoryInfo_size, uint32_t* numEntries )
Returns a sorted list of managed memory regions The sorted list of memory regions starts from a region containing the specified
                           starting address. If the starting address is set to 0, a sorted list of managed memory regions is returned which starts from
                           the managed memory region with the lowest start address.

CUDBGResult
                            ( *CUDBGAPI_st::memcheckReadErrorAddress )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t* address, ptxStorageKind* storage )
Get the address that memcheck detected an error on.

CUDBGResult
                            ( *CUDBGAPI_st::readActiveLanes )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* activeLanesMask )
Reads the bitmask of active lanes on a valid warp.

CUDBGResult
                            ( *CUDBGAPI_st::readAllVirtualReturnAddresses )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t* addrs, uint32_t numAddrs, uint32_t* callDepth, uint32_t* syscallCallDepth )
Reads all the virtual return addresses.

CUDBGResult
                            ( *CUDBGAPI_st::readBlockIdx )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* blockIdx )
Reads the CUDA block index running on a valid warp.

CUDBGResult
                            ( *CUDBGAPI_st::readBlockIdx32 )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim2* blockIdx )
Reads the two-dimensional CUDA block index running on a valid warp.

CUDBGResult
                            ( *CUDBGAPI_st::readBrokenWarps )(  uint32_t dev, uint32_t sm, uint64_t* brokenWarpsMask )
Reads the bitmask of warps that are at a breakpoint on a given SM.

CUDBGResult
                            ( *CUDBGAPI_st::readCCRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t* val )
Reads the hardware CC register.

CUDBGResult
                            ( *CUDBGAPI_st::readCPUCallStack )(  uint32_t dev, uint64_t gridId64, uint64_t* addrs, uint32_t numAddrs, uint32_t* totalNumAddrs )
Read CPU call stack captured at the time of kernel launch.

CUDBGResult
                            ( *CUDBGAPI_st::readCallDepth )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t* depth )
Reads the call depth (number of calls) for a given lane.

CUDBGResult
                            ( *CUDBGAPI_st::readCallDepth32 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* depth )
Reads the call depth (number of calls) for a given warp.

CUDBGResult
                            ( *CUDBGAPI_st::readClusterIdx )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* clusterIdx )
Reads the CUDA cluster index running on a valid warp.

CUDBGResult
                            ( *CUDBGAPI_st::readCodeMemory )(  uint32_t dev, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the code memory segment.

CUDBGResult
                            ( *CUDBGAPI_st::readConstMemory129 )(  uint32_t dev, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the constant memory segment.

CUDBGResult
                            ( *CUDBGAPI_st::readErrorPC )(  uint32_t devId, uint32_t sm, uint32_t wp, uint64_t* errorPC, bool* errorPCValid )
Get the hardware reported error PC if it exists.

CUDBGResult
                            ( *CUDBGAPI_st::readGenericMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, void* buf, uint32_t sz )
Reads content at an address in the generic address space. This function determines if the given address falls into the local,
                           shared, or global memory window. It then accesses memory taking into account the hardware co-ordinates provided as inputs.

CUDBGResult
                            ( *CUDBGAPI_st::readGlobalMemory )(  uint64_t addr, void* buf, uint32_t sz )
Reads content at an address in the global address space. If the address is valid on more than one device and one of those
                           devices does not support UVA, an error is returned.

CUDBGResult
                            ( *CUDBGAPI_st::readGlobalMemory31 )(  uint32_t dev, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the global memory segment.

CUDBGResult
                            ( *CUDBGAPI_st::readGlobalMemory55 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the global memory segment (entire 40-bit VA on Fermi+).

CUDBGResult
                            ( *CUDBGAPI_st::readGridId )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t* gridId64 )
Reads the 64-bit CUDA grid index running on a valid warp.

CUDBGResult
                            ( *CUDBGAPI_st::readGridId50 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* gridId )
Reads the CUDA grid index running on a valid warp.

CUDBGResult
                            ( *CUDBGAPI_st::readLaneException )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, CUDBGException_t* exception )
Reads the exception type for a given lane.

CUDBGResult
                            ( *CUDBGAPI_st::readLaneStatus )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, bool* error )
Reads the status of the given lane. For specific error values, use readLaneException.

CUDBGResult
                            ( *CUDBGAPI_st::readLocalMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the local memory segment.

CUDBGResult
                            ( *CUDBGAPI_st::readPC )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t* pc )
Reads the PC on the given active lane.

CUDBGResult
                            ( *CUDBGAPI_st::readParamMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the param memory segment.

CUDBGResult
                            ( *CUDBGAPI_st::readPinnedMemory )(  uint64_t addr, void* buf, uint32_t sz )
Reads content at pinned address in system memory.

CUDBGResult
                            ( *CUDBGAPI_st::readPredicates )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t predicates_size, uint32_t* predicates )
Reads content of hardware predicate registers.

CUDBGResult
                            ( *CUDBGAPI_st::readRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t regno, uint32_t* val )
Reads content of a hardware register.

CUDBGResult
                            ( *CUDBGAPI_st::readRegisterRange )(  uint32_t devId, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t index, uint32_t registers_size, uint32_t* registers )
Reads content of a hardware range of hardware registers.

CUDBGResult
                            ( *CUDBGAPI_st::readReturnAddress )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t level, uint64_t* ra )
Reads the physical return address for a call level.

CUDBGResult
                            ( *CUDBGAPI_st::readReturnAddress32 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t level, uint64_t* ra )
Reads the physical return address for a call level.

CUDBGResult
                            ( *CUDBGAPI_st::readSharedMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the shared memory segment.

CUDBGResult
                            ( *CUDBGAPI_st::readSmException )(  uint32_t dev, uint32_t sm, CUDBGException_t* exception, uint64_t* errorPC, bool* errorPCValid )
Get the SM exception status if it exists.

CUDBGResult
                            ( *CUDBGAPI_st::readSyscallCallDepth )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t* depth )
Reads the call depth of syscalls for a given lane.

CUDBGResult
                            ( *CUDBGAPI_st::readTextureMemory )(  uint32_t devId, uint32_t vsm, uint32_t wp, uint32_t id, uint32_t dim, uint32_t* coords, void* buf, uint32_t sz )
This method is no longer supported since CUDA 12.0.

CUDBGResult
                            ( *CUDBGAPI_st::readTextureMemoryBindless )(  uint32_t devId, uint32_t vsm, uint32_t wp, uint32_t texSymtabIndex, uint32_t dim, uint32_t* coords, void* buf, uint32_t sz )
This method is no longer supported since CUDA 12.0.

CUDBGResult
                            ( *CUDBGAPI_st::readThreadIdx )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, CuDim3* threadIdx )
Reads the CUDA thread index running on valid lane.

CUDBGResult
                            ( *CUDBGAPI_st::readUniformPredicates )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t predicates_size, uint32_t* predicates )
Reads contents of uniform predicate registers.

CUDBGResult
                            ( *CUDBGAPI_st::readUniformRegisterRange )(  uint32_t devId, uint32_t sm, uint32_t wp, uint32_t regno, uint32_t registers_size, uint32_t* registers )
Reads a range of uniform registers.

CUDBGResult
                            ( *CUDBGAPI_st::readValidLanes )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* validLanesMask )
Reads the bitmask of valid lanes on a given warp.

CUDBGResult
                            ( *CUDBGAPI_st::readValidWarps )(  uint32_t dev, uint32_t sm, uint64_t* validWarpsMask )
Reads the bitmask of valid warps on a given SM.

CUDBGResult
                            ( *CUDBGAPI_st::readVirtualPC )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t* pc )
Reads the virtual PC on the given active lane.

CUDBGResult
                            ( *CUDBGAPI_st::readVirtualReturnAddress )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t level, uint64_t* ra )
Reads the virtual return address for a call level.

CUDBGResult
                            ( *CUDBGAPI_st::readVirtualReturnAddress32 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t level, uint64_t* ra )
Reads the virtual return address for a call level.

CUDBGResult
                            ( *CUDBGAPI_st::readWarpResources )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGWarpResources* resources )
Get the resources assigned to a given warp.

CUDBGResult
                            ( *CUDBGAPI_st::readWarpState )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGWarpState* state )
Get state of a given warp.

CUDBGResult
                            ( *CUDBGAPI_st::readWarpState120 )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGWarpState120* state )
Get state of a given warp.

CUDBGResult
                            ( *CUDBGAPI_st::readWarpState127 )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGWarpState127* state )
Get state of a given warp.

CUDBGResult
                            ( *CUDBGAPI_st::readWarpState60 )(  uint32_t devId, uint32_t sm, uint32_t wp, CUDBGWarpState60* state )
Get state of a given warp.

CUDBGResult
                            ( *CUDBGAPI_st::writePinnedMemory )(  uint64_t addr, const void* buf, uint32_t sz )
Writes content to pinned address in system memory.

CUDBGResult
                            ( *CUDBGAPI_st::writePredicates )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t predicates_size, const uint32_t* predicates )
Writes content to hardware predicate registers.

CUDBGResult
                            ( *CUDBGAPI_st::writeUniformPredicates )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t predicates_size, const uint32_t* predicates )
Writes to uniform predicate registers.


### Variables


CUDBGResult
                              ( *CUDBGAPI_st::consumeCudaLogs )(  CUDBGCudaLogMessage* logMessages, uint32_t numMessages, uint32_t* numConsumed )
Get CUDA error log entries. This consumes the log entries, so they will not be available in subsequent calls.  Since CUDA
                                 12.9.


                                 Parameters



logMessages
- client-allocated array to store log entries
numMessages
- capacity of the logMessages array, in number of elements
numConsumed
- returned number of entries written to logMessages

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_NOT_SUPPORTED,

CUDBGResult
                              ( *CUDBGAPI_st::generateCoredump )(  const char* filename, CUDBGCoredumpGenerationFlags flags )
Generates a coredump for the current GPU state.  Since CUDA 12.3

                                 Parameters



filename
- target coredump file name
flags
- coredump generation flags/options

Returns
CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_NOT_SUPPORTED

CUDBGResult
                              ( *CUDBGAPI_st::getCbuWarpState )(  uint32_t dev, uint32_t sm, uint64_t warpMask, CUDBGCbuWarpState* warpStates, uint32_t numWarpStates )
Gets CBU state of a given warp.  Since CUDA 12.9.

                                 Parameters



dev
- device index
sm
- SM index
warpMask
- bitmask of the warps which states should be returned in warpStates
warpStates
- pointer to the array of CUDBGCbuWarpState structures
numWarpStates
- number of elements in warpStates array

Returns
CUDBG_ERROR_NOT_SUPPORTED,

CUDBGResult
                              ( *CUDBGAPI_st::getClusterExceptionTargetBlock )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* blockIdx, bool* blockIdxValid )
Retrieves the target block index and validity status for a given device, streaming multiprocessor, and warp for cluster exceptions.
                                 Since CUDA 12.7.


                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
blockIdx
- pointer to a `CuDim3` structure that will be populated with the target block index
blockIdxValid
- pointer to a boolean variable that will be set to `true` if the target block index is valid, and `false` otherwise. Value
                                    will be set to false if the warp is not stopped on a cluster exception


Returns
CUDBG_SUCCESS, CUDBG_ERROR_NOT_SUPPORTED, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_INVALID_ARGS,

CUDBGResult
                              ( *CUDBGAPI_st::getConstBankAddress )(  uint32_t dev, uint64_t gridId64, uint32_t bank, uint64_t* address, uint32_t* size )
Get constant bank GPU VA and size.  Since CUDA 12.4

                                 Parameters



dev
- device index
gridId64
- grid ID of the grid containing the constant bank
bank
- constant bank number
address
- (output) GPU VA of the bank memory
size
- (output) bank size

Returns
CUDBG_ERROR_NOT_SUPPORTED

CUDBGResult
                              ( *CUDBGAPI_st::getConstBankAddress123 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t bank, uint32_t offset, uint64_t* address )
Convert constant bank number and offset into GPU VA.  Since CUDA 12.3

Note:Deprecated in CUDA 12.4.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
bank
- constant bank number
offset
- offset within the bank
address
- (output) GPU VA

Returns
CUDBG_ERROR_NOT_SUPPORTED

CUDBGResult
                              ( *CUDBGAPI_st::getCudaExceptionString )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, char* buf, uint32_t bufSz, uint32_t* msgSz )
Get error string for CUDA Exceptions.  Since CUDA 13.0.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
buf
- buffer for the error string
bufSz
- buffer size
msgSz
- error message size with null character, can be null

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_ARGS,
                                 CUDBG_ERROR_BUFFER_TOO_SMALL, CUDBG_ERROR_NOT_SUPPORTED

CUDBGResult
                              ( *CUDBGAPI_st::getHardwareBarrierInfo )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, CUDBGBarrierScope* scope, char* buf, uint32_t bufSz, uint32_t* msgSz )
Get hardware barrier information.  Since CUDA 13.1.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
scope
- barrier scope
buf
- buffer for the barrier information
bufSz
- buffer size
msgSz
- error message size with null character, can be null

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_ARGS,
                                 CUDBG_ERROR_BUFFER_TOO_SMALL, CUDBG_ERROR_NOT_SUPPORTED

CUDBGResult
                              ( *CUDBGAPI_st::getLoadedFunctionInfo )(  uint32_t devId, uint64_t handle, CUDBGLoadedFunctionInfo* info, uint32_t startIndex, uint32_t numEntries )
Get the section number and address of loaded functions for a given module.  Since CUDA 11.8

                                 Parameters



devId

handle
- ELF/cubin image handle
info

startIndex

numEntries
- number of function load entries to read

Returns
CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_NOT_SUPPORTED

CUDBGResult
                              ( *CUDBGAPI_st::getLoadedFunctionInfo118 )(  uint32_t devId, uint64_t handle, CUDBGLoadedFunctionInfo* info, uint32_t numEntries )
Get the section number and address of loaded functions for a given module.  Since CUDA 11.8

Note:Deprecated in CUDA 12.3.

                                 Parameters



devId

handle
- ELF/cubin image handle
info

numEntries
- number of function load entries to read

Returns
CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_NOT_SUPPORTED

CUDBGResult
                              ( *CUDBGAPI_st::getManagedMemoryRegionInfo )(  uint64_t startAddress, CUDBGMemoryInfo* memoryInfo, uint32_t memoryInfo_size, uint32_t* numEntries )
Returns a sorted list of managed memory regions The sorted list of memory regions starts from a region containing the specified
                                 starting address. If the starting address is set to 0, a sorted list of managed memory regions is returned which starts from
                                 the managed memory region with the lowest start address.  Since CUDA 6.0.


                                 Parameters



startAddress
- The address that the first region in the list must contain. If the starting address is set to 0, the list of managed memory
                                    regions returned starts from the managed memory region with the lowest start address.

memoryInfo
- Client-allocated array of memory region records of type CUDBGMemoryInfo.
memoryInfo_size
- Number of records of type CUDBGMemoryInfo that memoryInfo can hold.
numEntries
- Pointer to a client-allocated variable holding the number of valid entries retured in memoryInfo. Valid entries are continguous
                                    and start from memoryInfo[0].


Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_ADDRESS, CUDBG_ERROR_INTERNAL

CUDBGResult
                              ( *CUDBGAPI_st::memcheckReadErrorAddress )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t* address, ptxStorageKind* storage )
Get the address that memcheck detected an error on.  Since CUDA 5.0.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
address
- returned address detected by memcheck
storage
- returned address class of address

Returns
CUDBG_ERROR_NOT_SUPPORTED,

CUDBGResult
                              ( *CUDBGAPI_st::readActiveLanes )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* activeLanesMask )
Reads the bitmask of active lanes on a valid warp.  Since CUDA 3.0.

See also:
readGridId
readBlockIdx
readThreadIdx
readBrokenWarps
readValidWarps
readValidLanes

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
activeLanesMask
- the returned bitmask of active lanes

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readAllVirtualReturnAddresses )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t* addrs, uint32_t numAddrs, uint32_t* callDepth, uint32_t* syscallCallDepth )
Reads all the virtual return addresses.  Since CUDA 12.5.

See also:
readCallDepth
readReturnAddress

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
addrs
- the returned addresses array
numAddrs
- number of elements in addrs array
callDepth
- the returned call depth
syscallCallDepth
- the returned syscall call depth

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_INVALID_LANE,
                                 CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_UNKNOWN_FUNCTION, CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_INTERNAL

CUDBGResult
                              ( *CUDBGAPI_st::readBlockIdx )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* blockIdx )
Reads the CUDA block index running on a valid warp.  Since CUDA 4.0.

See also:
readGridId
readThreadIdx
readBrokenWarps
readValidWarps
readValidLanes
readActiveLanes

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
blockIdx
- the returned CUDA block index

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readBlockIdx32 )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim2* blockIdx )
Reads the two-dimensional CUDA block index running on a valid warp.  Since CUDA 3.0.

Note:Deprecated in CUDA 4.0.

See also:
readGridId
readThreadIdx
readBrokenWarps
readValidWarps
readValidLanes
readActiveLanes

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
blockIdx
- the returned CUDA block index

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readBrokenWarps )(  uint32_t dev, uint32_t sm, uint64_t* brokenWarpsMask )
Reads the bitmask of warps that are at a breakpoint on a given SM.  Since CUDA 3.0.

See also:
readGridId
readBlockIdx
readThreadIdx
readValidWarps
readValidLanes
readActiveLanes

                                 Parameters



dev
- device index
sm
- SM index
brokenWarpsMask
- the returned bitmask of broken warps

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readCCRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t* val )
Reads the hardware CC register.  Since CUDA 6.5.

See also:
readCodeMemory
readConstMemory129
readGenericMemory
readGlobalMemory
readParamMemory
readSharedMemory
readTextureMemory
readLocalMemory
readRegister
readPC
readPredicates

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
- buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readCPUCallStack )(  uint32_t dev, uint64_t gridId64, uint64_t* addrs, uint32_t numAddrs, uint32_t* totalNumAddrs )
Read CPU call stack captured at the time of kernel launch.  Since CUDA 12.9.
This method is only supported when the CUDBG_DEBUGGER_CAPABILITY_COLLECT_CPU_CALL_STACK_FOR_KERNEL_LAUNCHES capability has
                                 been enabled.


                                 Parameters



dev
- device index
gridId64
- 64-bit grid ID
addrs
- the returned addresses array, can be NULL
numAddrs
- capacity of addrs (possibly 0)
totalNumAddrs
- the actual size of the stack (number of frames) is written here; the value written can be greater than numAddrs

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_UNINITIALIZED,
                                 CUDBG_ERROR_INTERNAL, CUDBG_ERROR_NOT_SUPPORTED

CUDBGResult
                              ( *CUDBGAPI_st::readCallDepth )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t* depth )
Reads the call depth (number of calls) for a given lane.  Since CUDA 4.0.

See also:
readReturnAddress
readVirtualReturnAddress

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
depth
- the returned call depth

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_INVALID_LANE,
                                 CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readCallDepth32 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* depth )
Reads the call depth (number of calls) for a given warp.  Since CUDA 3.1.

Note:Deprecated in CUDA 4.0.

See also:
readReturnAddress32
readVirtualReturnAddress32

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
depth
- the returned call depth

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readClusterIdx )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* clusterIdx )
Reads the CUDA cluster index running on a valid warp.  Since CUDA 12.0.

Note:Deprecated in CUDA 12.7.

See also:
readGridId
readThreadIdx
readBlockIdx
readBrokenWarps
readValidWarps
readValidLanes
readActiveLanes

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
clusterIdx
- the returned CUDA cluster index

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readCodeMemory )(  uint32_t dev, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the code memory segment.  Since CUDA 3.0.

See also:
readConstMemory129
readGenericMemory
readParamMemory
readSharedMemory
readTextureMemory
readLocalMemory
readRegister
readPC

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
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_MEMORY_MAPPING_FAILED

CUDBGResult
                              ( *CUDBGAPI_st::readConstMemory129 )(  uint32_t dev, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the constant memory segment.  Since CUDA 3.0.

Note:Deprecated in CUDA 13.0.

See also:
readCodeMemory
readGenericMemory
readParamMemory
readSharedMemory
readTextureMemory
readLocalMemory
readRegister
readPC

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
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_MEMORY_MAPPING_FAILED

CUDBGResult
                              ( *CUDBGAPI_st::readErrorPC )(  uint32_t devId, uint32_t sm, uint32_t wp, uint64_t* errorPC, bool* errorPCValid )
Get the hardware reported error PC if it exists.  Since CUDA 6.0

                                 Parameters



devId
- the device index
sm
- the SM index
wp

errorPC
- PC ofthe exception
errorPCValid
- boolean to indicate that the returned error PC is valid

Returns
CUDBG_SUCCESS CUDBG_ERROR_UNINITIALIZED CUDBG_ERROR_INVALID_DEVICE CUDBG_ERROR_INVALID_SM CUDBG_ERROR_INVALID_WARP CUDBG_ERROR_INVALID_ARGS
                                 CUDBG_ERROR_UNKNOWN_FUNCTION

CUDBGResult
                              ( *CUDBGAPI_st::readGenericMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, void* buf, uint32_t sz )
Reads content at an address in the generic address space. This function determines if the given address falls into the local,
                                 shared, or global memory window. It then accesses memory taking into account the hardware co-ordinates provided as inputs.
                                 Since CUDA 6.0.


See also:
readCodeMemory
readConstMemory129
readParamMemory
readSharedMemory
readTextureMemory
readLocalMemory
readRegister
readPC

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
                              ( *CUDBGAPI_st::readGlobalMemory )(  uint64_t addr, void* buf, uint32_t sz )
Reads content at an address in the global address space. If the address is valid on more than one device and one of those
                                 devices does not support UVA, an error is returned.  Since CUDA 6.0.


See also:
readCodeMemory
readConstMemory129
readParamMemory
readSharedMemory
readTextureMemory
readLocalMemory
readRegister
readPC

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
                              ( *CUDBGAPI_st::readGlobalMemory31 )(  uint32_t dev, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the global memory segment.  Since CUDA 3.0.

Note:Deprecated in CUDA 3.2.

See also:
readCodeMemory
readConstMemory129
readParamMemory
readSharedMemory
readTextureMemory
readLocalMemory
readRegister
readPC

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
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_MEMORY_MAPPING_FAILED

CUDBGResult
                              ( *CUDBGAPI_st::readGlobalMemory55 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the global memory segment (entire 40-bit VA on Fermi+).  Since CUDA 3.2.

Note:Deprecated in CUDA 6.0.

See also:
readCodeMemory
readConstMemory129
readParamMemory
readSharedMemory
readTextureMemory
readLocalMemory
readRegister
readPC

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
                              ( *CUDBGAPI_st::readGridId )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t* gridId64 )
Reads the 64-bit CUDA grid index running on a valid warp.  Since CUDA 5.5.

See also:
readBlockIdx
readThreadIdx
readBrokenWarps
readValidWarps
readValidLanes
readActiveLanes

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
gridId64

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readGridId50 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* gridId )
Reads the CUDA grid index running on a valid warp.  Since CUDA 3.0.

Note:Deprecated in CUDA 5.5.

See also:
readBlockIdx
readThreadIdx
readBrokenWarps
readValidWarps
readValidLanes
readActiveLanes

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
gridId
- the returned CUDA grid index

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readLaneException )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, CUDBGException_t* exception )
Reads the exception type for a given lane.  Since CUDA 3.1.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
exception
- the returned exception type

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readLaneStatus )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, bool* error )
Reads the status of the given lane. For specific error values, use readLaneException.  Since CUDA 3.0.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
error
- true if there is an error

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readLocalMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the local memory segment.  Since CUDA 3.0.

See also:
readCodeMemory
readConstMemory129
readGenericMemory
readParamMemory
readSharedMemory
readTextureMemory
readRegister
readPC

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
                              ( *CUDBGAPI_st::readPC )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t* pc )
Reads the PC on the given active lane.  Since CUDA 3.0.

See also:
readCodeMemory
readConstMemory129
readGenericMemory
readParamMemory
readSharedMemory
readTextureMemory
readLocalMemory
readRegister
readVirtualPC

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
pc
- the returned PC

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNKNOWN_FUNCTION, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readParamMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the param memory segment.  Since CUDA 3.0.

See also:
readCodeMemory
readConstMemory129
readGenericMemory
readSharedMemory
readTextureMemory
readLocalMemory
readRegister
readPC

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
                              ( *CUDBGAPI_st::readPinnedMemory )(  uint64_t addr, void* buf, uint32_t sz )
Reads content at pinned address in system memory.  Since CUDA 3.2.

See also:
readCodeMemory
readConstMemory129
readGenericMemory
readParamMemory
readSharedMemory
readTextureMemory
readLocalMemory
readRegister
readPC

                                 Parameters



addr
- system memory address
buf
- buffer
sz
- size of the buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_MEMORY_MAPPING_FAILED, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readPredicates )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t predicates_size, uint32_t* predicates )
Reads content of hardware predicate registers.  Since CUDA 6.5.

See also:
readCodeMemory
readConstMemory129
readGenericMemory
readGlobalMemory
readParamMemory
readSharedMemory
readTextureMemory
readLocalMemory
readRegister
readPC

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
predicates_size
- number of predicate registers to read
predicates
- buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t regno, uint32_t* val )
Reads content of a hardware register.  Since CUDA 3.0.

See also:
readCodeMemory
readConstMemory129
readGenericMemory
readParamMemory
readSharedMemory
readTextureMemory
readLocalMemory
readPC

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
                              ( *CUDBGAPI_st::readRegisterRange )(  uint32_t devId, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t index, uint32_t registers_size, uint32_t* registers )
Reads content of a hardware range of hardware registers.  Since CUDA 6.0.

See also:
readCodeMemory
readConstMemory129
readGenericMemory
readParamMemory
readSharedMemory
readTextureMemory
readLocalMemory
readPC
readRegister

                                 Parameters



devId

sm
- SM index
wp
- warp index
ln
- lane index
index
- index of the first register to read
registers_size
- number of registers to read
registers
- buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readReturnAddress )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t level, uint64_t* ra )
Reads the physical return address for a call level.  Since CUDA 4.0.

See also:
readCallDepth
readVirtualReturnAddress

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
level
- the specified call level
ra
- the returned return address for level

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_INVALID_LANE,
                                 CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_INVALID_CALL_LEVEL, CUDBG_ERROR_ZERO_CALL_DEPTH, CUDBG_ERROR_UNKNOWN_FUNCTION, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readReturnAddress32 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t level, uint64_t* ra )
Reads the physical return address for a call level.  Since CUDA 3.1.

Note:Deprecated in CUDA 4.0.

See also:
readCallDepth32
readVirtualReturnAddress32

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
level
- the specified call level
ra
- the returned return address for level

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_INVALID_GRID,
                                 CUDBG_ERROR_INVALID_CALL_LEVEL, CUDBG_ERROR_ZERO_CALL_DEPTH, CUDBG_ERROR_UNKNOWN_FUNCTION, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readSharedMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the shared memory segment.  Since CUDA 3.0.

See also:
readCodeMemory
readConstMemory129
readGenericMemory
readParamMemory
readLocalMemory
readTextureMemory
readRegister
readPC

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
                              ( *CUDBGAPI_st::readSmException )(  uint32_t dev, uint32_t sm, CUDBGException_t* exception, uint64_t* errorPC, bool* errorPCValid )
Get the SM exception status if it exists.  Since CUDA 12.5.

                                 Parameters



dev
- the device index
sm
- the SM index
exception
- returned exception
errorPC
- returned PC of the exception
errorPCValid
- boolean to indicate that the returned error PC is valid

Returns
CUDBG_SUCCESS CUDBG_ERROR_UNINITIALIZED CUDBG_ERROR_INVALID_DEVICE CUDBG_ERROR_INVALID_SM CUDBG_ERROR_INVALID_ARGS CUDBG_ERROR_UNKNOWN_FUNCTION

CUDBGResult
                              ( *CUDBGAPI_st::readSyscallCallDepth )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t* depth )
Reads the call depth of syscalls for a given lane.  Since CUDA 4.1.

See also:
readReturnAddress
readVirtualReturnAddress

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
depth
- the returned call depth

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_INVALID_LANE,
                                 CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readTextureMemory )(  uint32_t devId, uint32_t vsm, uint32_t wp, uint32_t id, uint32_t dim, uint32_t* coords, void* buf, uint32_t sz )
This method is no longer supported since CUDA 12.0.



See also:
readCodeMemory
readConstMemory129
readGenericMemory
readParamMemory
readSharedMemory
readLocalMemory
readRegister
readPC

                                 Parameters



devId
- device index
vsm
- SM index
wp
- warp index
id
- texture id (the value of DW_AT_location attribute in the relocated ELF image)
dim
- texture dimension (1 to 4)
coords
- array of coordinates of size dim
buf
- result buffer
sz
- size of the buffer

Returns
CUDBG_ERROR_NOT_SUPPORTED,

CUDBGResult
                              ( *CUDBGAPI_st::readTextureMemoryBindless )(  uint32_t devId, uint32_t vsm, uint32_t wp, uint32_t texSymtabIndex, uint32_t dim, uint32_t* coords, void* buf, uint32_t sz )
This method is no longer supported since CUDA 12.0.



See also:
readCodeMemory
readConstMemory129
readGenericMemory
readParamMemory
readSharedMemory
readLocalMemory
readRegister
readPC

                                 Parameters



devId
- device index
vsm
- SM index
wp
- warp index
texSymtabIndex
- global symbol table index of the texture symbol
dim
- texture dimension (1 to 4)
coords
- array of coordinates of size dim
buf
- result buffer
sz
- size of the buffer

Returns
CUDBG_ERROR_NOT_SUPPORTED

CUDBGResult
                              ( *CUDBGAPI_st::readThreadIdx )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, CuDim3* threadIdx )
Reads the CUDA thread index running on valid lane.  Since CUDA 3.0.

See also:
readGridId
readBlockIdx
readBrokenWarps
readValidWarps
readValidLanes
readActiveLanes

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
threadIdx
- the returned CUDA thread index

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readUniformPredicates )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t predicates_size, uint32_t* predicates )
Reads contents of uniform predicate registers.  Since CUDA 10.0.

See also:
readPredicates

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
predicates_size
- number of predicate registers to read
predicates
- buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readUniformRegisterRange )(  uint32_t devId, uint32_t sm, uint32_t wp, uint32_t regno, uint32_t registers_size, uint32_t* registers )
Reads a range of uniform registers.  Since CUDA 10.0.

See also:
readRegister

                                 Parameters



devId

sm
- SM index
wp
- warp index
regno
- starting index into uniform register file
registers_size
- number of bytes to read
registers
- pointer to buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readValidLanes )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* validLanesMask )
Reads the bitmask of valid lanes on a given warp.  Since CUDA 3.0.

See also:
readGridId
readBlockIdx
readThreadIdx
readBrokenWarps
readValidWarps
readActiveLanes

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
validLanesMask
- the returned bitmask of valid lanes

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readValidWarps )(  uint32_t dev, uint32_t sm, uint64_t* validWarpsMask )
Reads the bitmask of valid warps on a given SM.  Since CUDA 3.0.

See also:
readGridId
readBlockIdx
readThreadIdx
readBrokenWarps
readValidLanes
readActiveLanes

                                 Parameters



dev
- device index
sm
- SM index
validWarpsMask
- the returned bitmask of valid warps

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::readVirtualPC )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t* pc )
Reads the virtual PC on the given active lane.  Since CUDA 3.0.

See also:
readPC

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
pc
- the returned PC

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_UNKNOWN_FUNCTION

CUDBGResult
                              ( *CUDBGAPI_st::readVirtualReturnAddress )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t level, uint64_t* ra )
Reads the virtual return address for a call level.  Since CUDA 4.0.

See also:
readCallDepth
readReturnAddress

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
ln
- lane index
level
- the specified call level
ra
- the returned virtual return address for level

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_INVALID_LANE,
                                 CUDBG_ERROR_INVALID_GRID, CUDBG_ERROR_INVALID_CALL_LEVEL, CUDBG_ERROR_ZERO_CALL_DEPTH, CUDBG_ERROR_UNKNOWN_FUNCTION, CUDBG_ERROR_UNINITIALIZED,
                                 CUDBG_ERROR_INTERNAL

CUDBGResult
                              ( *CUDBGAPI_st::readVirtualReturnAddress32 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t level, uint64_t* ra )
Reads the virtual return address for a call level.  Since CUDA 3.1.

Note:Deprecated in CUDA 4.0.

See also:
readCallDepth32
readReturnAddress32

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
level
- the specified call level
ra
- the returned virtual return address for level

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_INVALID_GRID,
                                 CUDBG_ERROR_INVALID_CALL_LEVEL, CUDBG_ERROR_ZERO_CALL_DEPTH, CUDBG_ERROR_UNKNOWN_FUNCTION, CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_INTERNAL

CUDBGResult
                              ( *CUDBGAPI_st::readWarpResources )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGWarpResources* resources )
Get the resources assigned to a given warp.  Since CUDA 12.8.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
resources
- pointer to structure that contains warp resources

Returns
CUDBG_ERROR_NOT_SUPPORTED,

CUDBGResult
                              ( *CUDBGAPI_st::readWarpState )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGWarpState* state )
Get state of a given warp.  Since CUDA 12.9.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
state
- pointer to structure that contains warp state

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED,

CUDBGResult
                              ( *CUDBGAPI_st::readWarpState120 )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGWarpState120* state )
Get state of a given warp.  Since CUDA 12.0.

Note:Deprecated in CUDA 12.7.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
state
- pointer to structure that contains warp status

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED,

CUDBGResult
                              ( *CUDBGAPI_st::readWarpState127 )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGWarpState127* state )
Get state of a given warp.  Since CUDA 12.7.

Note:Deprecated in CUDA 12.9.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
state
- pointer to structure that contains warp status

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED,

CUDBGResult
                              ( *CUDBGAPI_st::readWarpState60 )(  uint32_t devId, uint32_t sm, uint32_t wp, CUDBGWarpState60* state )
Get state of a given warp.  Since CUDA 6.0.

Note:Deprecated in CUDA 12.0.

                                 Parameters



devId

sm
- SM index
wp
- warp index
state
- pointer to structure that contains warp status

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED,

CUDBGResult
                              ( *CUDBGAPI_st::writePinnedMemory )(  uint64_t addr, const void* buf, uint32_t sz )
Writes content to pinned address in system memory.  Since CUDA 3.2.

See also:
readCodeMemory
readConstMemory129
readGenericMemory
readParamMemory
readSharedMemory
readLocalMemory
readRegister
readPC

                                 Parameters



addr
- system memory address
buf
- buffer
sz
- size of the buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_MEMORY_MAPPING_FAILED, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::writePredicates )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t predicates_size, const uint32_t* predicates )
Writes content to hardware predicate registers.  Since CUDA 6.5.

See also:
writeConstMemory
writeGenericMemory
writeGlobalMemory
writeParamMemory
writeSharedMemory
writeTextureMemory
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
predicates_size
- number of predicate registers to write
predicates
- buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_LANE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP,
                                 CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::writeUniformPredicates )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t predicates_size, const uint32_t* predicates )
Writes to uniform predicate registers.  Since CUDA 10.0.

See also:
readUniformPredicate
writeRegister

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp index
predicates_size
- number of predicate registers to write
predicates
- buffer

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_SM, CUDBG_ERROR_INVALID_WARP, CUDBG_ERROR_UNINITIALIZED


---