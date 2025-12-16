# Debugger API

[< Previous](annotated.html) | [Next >](structCUDBGCudaLogMessage.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 4.1. CUDBGAPI_st Struct Reference


Get the API associated with the major/minor/revision version numbers.






See also:


cudbgGetAPIVersion




### Public Variables


CUDBGResult
                            ( *acknowledgeEvent30 )(  CUDBGEvent30* event )
Inform the debugger API that the event has been processed.

CUDBGResult
                            ( *acknowledgeEvents42 )(   )
Inform the debugger API that synchronous events have been processed.

CUDBGResult
                            ( *acknowledgeSyncEvents )(   )
Inform the debugger API that synchronous events have been processed.

CUDBGResult
                            ( *clearAttachState )(   )
Clear attach-specific state prior to detach.

CUDBGResult
                            ( *consumeCudaLogs )(  CUDBGCudaLogMessage* logMessages, uint32_t numMessages, uint32_t* numConsumed )
Get CUDA error log entries. This consumes the log entries, so they will not be available in subsequent calls.

CUDBGResult
                            ( *disassemble )(  uint32_t dev, uint64_t addr, uint32_t* instSize, char* buf, uint32_t sz )
Disassemble instruction at instruction address.

CUDBGResult
                            ( *finalize )(   )
Finalize the API and free all memory.

CUDBGResult
                            ( *generateCoredump )(  const char* filename, CUDBGCoredumpGenerationFlags flags )
Generates a coredump for the current GPU state.

CUDBGResult
                            ( *getAdjustedCodeAddress )(  uint32_t devId, uint64_t address, uint64_t* adjustedAddress, CUDBGAdjAddrAction adjAction )
The client must call this function before inserting a breakpoint, or when the previous or next code address is needed. Returns
                           the adjusted code address for a given code address for a given device.

CUDBGResult
                            ( *getBlockDim )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* blockDim )
Get the number of threads in the given block.

CUDBGResult
                            ( *getCbuWarpState )(  uint32_t dev, uint32_t sm, uint64_t warpMask, CUDBGCbuWarpState* warpStates, uint32_t numWarpStates )
Gets CBU state of a given warp.

CUDBGResult
                            ( *getClusterDim )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* clusterDim )
Get the number of blocks in the given cluster.

CUDBGResult
                            ( *getClusterDim120 )(  uint32_t dev, uint64_t gridId64, CuDim3* clusterDim )
Get the number of blocks in the given cluster.

CUDBGResult
                            ( *getClusterExceptionTargetBlock )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* blockIdx, bool* blockIdxValid )
Retrieves the target block index and validity status for a given device, streaming multiprocessor, and warp for cluster exceptions.

CUDBGResult
                            ( *getConstBankAddress )(  uint32_t dev, uint64_t gridId64, uint32_t bank, uint64_t* address, uint32_t* size )
Get constant bank GPU VA and size.

CUDBGResult
                            ( *getConstBankAddress123 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t bank, uint32_t offset, uint64_t* address )
Convert constant bank number and offset into GPU VA.

CUDBGResult
                            ( *getCudaExceptionString )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, char* buf, uint32_t bufSz, uint32_t* msgSz )
Get error string for CUDA Exceptions.

CUDBGResult
                            ( *getDeviceName )(  uint32_t dev, char* buf, uint32_t sz )
Get the device name string.

CUDBGResult
                            ( *getDevicePCIBusInfo )(  uint32_t devId, uint32_t* pciBusId, uint32_t* pciDevId )
Get PCI bus and device ids associated with device devId.

CUDBGResult
                            ( *getDeviceType )(  uint32_t dev, char* buf, uint32_t sz )
Get the string description of the device.

CUDBGResult
                            ( *getElfImage )(  uint32_t dev, uint32_t sm, uint32_t wp, bool  relocated, voidelfImage, uint64_t* size )
Get the relocated or non-relocated ELF image and size for the grid on the given device.

CUDBGResult
                            ( *getElfImage32 )(  uint32_t dev, uint32_t sm, uint32_t wp, bool  relocated, voidelfImage, uint32_t* size )
Get the relocated or non-relocated ELF image and size for the grid on the given device.

CUDBGResult
                            ( *getElfImageByHandle )(  uint32_t devId, uint64_t handle, CUDBGElfImageType type, void* elfImage, uint64_t size )
Get the relocated or non-relocated ELF image for the given handle on the given device.

CUDBGResult
                            ( *getErrorStringEx )(  char* buf, uint32_t bufSz, uint32_t* msgSz )
Fills a user-provided buffer with an error message encoded as a null-terminated ASCII string. The error message is specific
                           to the last failed API call and is invalidated after every API call.

CUDBGResult
                            ( *getGridAttribute )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGAttribute attr, uint64_t* value )
Get the value of a grid attribute.

CUDBGResult
                            ( *getGridAttributes )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGAttributeValuePair* pairs, uint32_t numPairs )
Get several grid attribute values in a single API call.

CUDBGResult
                            ( *getGridDim )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* gridDim )
Get the number of blocks in the given grid.

CUDBGResult
                            ( *getGridDim32 )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim2* gridDim )
Get the number of blocks in the given grid.

CUDBGResult
                            ( *getGridInfo )(  uint32_t dev, uint64_t gridId64, CUDBGGridInfo* gridInfo )
Get information about the specified grid. If the context of the grid has already been destroyed, the function will return
                           CUDBG_ERROR_INVALID_GRID, although the grid id is correct.

CUDBGResult
                            ( *getGridInfo120 )(  uint32_t dev, uint64_t gridId64, CUDBGGridInfo120* gridInfo )
Get information about the specified grid. If the context of the grid has already been destroyed, the function will return
                           CUDBG_ERROR_INVALID_GRID, although the grid id is correct.

CUDBGResult
                            ( *getGridInfo55 )(  uint32_t dev, uint64_t gridId64, CUDBGGridInfo55* gridInfo )
Get information about the specified grid. If the context of the grid has already been destroyed, the function will return
                           CUDBG_ERROR_INVALID_GRID, although the grid id is correct.

CUDBGResult
                            ( *getGridStatus )(  uint32_t dev, uint64_t gridId64, CUDBGGridStatus* status )
Check whether the grid corresponding to the given gridId is still present on the device.

CUDBGResult
                            ( *getGridStatus50 )(  uint32_t dev, uint32_t gridId, CUDBGGridStatus* status )
Check whether the grid corresponding to the given gridId is still present on the device.

CUDBGResult
                            ( *getHardwareBarrierInfo )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, CUDBGBarrierScope* scope, char* buf, uint32_t bufSz, uint32_t* msgSz )
Get hardware barrier information.

CUDBGResult
                            ( *getHostAddrFromDeviceAddr )(  uint32_t dev, uint64_t device_addr, uint64_t* host_addr )
given a device virtual address, return a corresponding system memory virtual address.

CUDBGResult
                            ( *getLoadedFunctionInfo )(  uint32_t devId, uint64_t handle, CUDBGLoadedFunctionInfo* info, uint32_t startIndex, uint32_t numEntries )
Get the section number and address of loaded functions for a given module.

CUDBGResult
                            ( *getLoadedFunctionInfo118 )(  uint32_t devId, uint64_t handle, CUDBGLoadedFunctionInfo* info, uint32_t numEntries )
Get the section number and address of loaded functions for a given module.

CUDBGResult
                            ( *getManagedMemoryRegionInfo )(  uint64_t startAddress, CUDBGMemoryInfo* memoryInfo, uint32_t memoryInfo_size, uint32_t* numEntries )
Returns a sorted list of managed memory regions The sorted list of memory regions starts from a region containing the specified
                           starting address. If the starting address is set to 0, a sorted list of managed memory regions is returned which starts from
                           the managed memory region with the lowest start address.

CUDBGResult
                            ( *getNextAsyncEvent50 )(  CUDBGEvent50* event )
Copies the next available event in the asynchronous event queue into 'event' and removes it from the queue. The asynchronous
                           event queue is held separate from the normal event queue, and does not require acknowledgement from the debug client.

CUDBGResult
                            ( *getNextAsyncEvent55 )(  CUDBGEvent55* event )
Copies the next available event in the asynchronous event queue into 'event' and removes it from the queue. The asynchronous
                           event queue is held separate from the normal event queue, and does not require acknowledgement from the debug client.

CUDBGResult
                            ( *getNextEvent )(  CUDBGEventQueueType type, CUDBGEvent* event )
Copies the next available event into 'event' and removes it from the queue.

CUDBGResult
                            ( *getNextEvent30 )(  CUDBGEvent30* event )
Copies the next available event in the event queue into 'event' and removes it from the queue.

CUDBGResult
                            ( *getNextEvent32 )(  CUDBGEvent32* event )
Copies the next available event in the event queue into 'event' and removes it from the queue.

CUDBGResult
                            ( *getNextEvent42 )(  CUDBGEvent42* event )
Copies the next available event in the event queue into 'event' and removes it from the queue.

CUDBGResult
                            ( *getNextSyncEvent50 )(  CUDBGEvent50* event )CUDBGResult
                            ( *getNextSyncEvent55 )(  CUDBGEvent55* event )
Copies the next available event in the synchronous event queue into 'event' and removes it from the queue.

CUDBGResult
                            ( *getNumDevices )(  uint32_t* numDev )
Get the number of installed CUDA devices.

CUDBGResult
                            ( *getNumLanes )(  uint32_t dev, uint32_t* numLanes )
Get the number of lanes per warp on the device.

CUDBGResult
                            ( *getNumPredicates )(  uint32_t dev, uint32_t* numPredicates )
Get the number of predicate registers per lane on the device.

CUDBGResult
                            ( *getNumRegisters )(  uint32_t dev, uint32_t* numRegs )
Get the number of registers per lane on the device.

CUDBGResult
                            ( *getNumSMs )(  uint32_t dev, uint32_t* numSMs )
Get the total number of SMs on the device.

CUDBGResult
                            ( *getNumUniformPredicates )(  uint32_t dev, uint32_t* numPredicates )
Get the number of uniform predicate registers per warp on the device.

CUDBGResult
                            ( *getNumUniformRegisters )(  uint32_t dev, uint32_t* numRegs )
Get the number of uniform registers per warp on the device.

CUDBGResult
                            ( *getNumWarps )(  uint32_t dev, uint32_t* numWarps )
Get the number of warps per SM on the device.

CUDBGResult
                            ( *getPhysicalRegister30 )(  uint64_t pc, char* reg, uint32_t* buf, uint32_t sz, uint32_t* numPhysRegs, CUDBGRegClass* regClass )
Get the physical register number(s) assigned to a virtual register name 'reg' at a given PC, if 'reg' is live at that PC.

CUDBGResult
                            ( *getPhysicalRegister40 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t pc, char* reg, uint32_t* buf, uint32_t sz, uint32_t* numPhysRegs, CUDBGRegClass* regClass )
Get the physical register number(s) assigned to a virtual register name 'reg' at a given PC, if 'reg' is live at that PC.

CUDBGResult
                            ( *getSmType )(  uint32_t dev, char* buf, uint32_t sz )
Get the SM type of the device.

CUDBGResult
                            ( *getSupportedDebuggerCapabilities )(  CUDBGCapabilityFlags* capabilities )
Returns debugger capabilities that are supported by this version of the API.

CUDBGResult
                            ( *getTID )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* tid )
Get the ID of the Linux thread hosting the context of the grid.

CUDBGResult
                            ( *initialize )(   )
Initialize the API.

CUDBGResult
                            ( *initializeAttachStub )(   )
Initialize the attach stub.

CUDBGResult
                            ( *isDeviceCodeAddress )(  uintptr_t addr, bool* isDeviceAddress )
Determines whether a virtual address resides within device code.

CUDBGResult
                            ( *isDeviceCodeAddress55 )(  uintptr_t addr, bool* isDeviceAddress )
Determines whether a virtual address resides within device code. This API is strongly deprecated. Use CUDBGAPI_st::isDeviceCodeAddress
                           instead.

CUDBGResult
                            ( *lookupDeviceCodeSymbol )(  char* symName, bool* symFound, uintptr_t* symAddr )
Determines whether a symbol represents a function in device code and returns its virtual address.

CUDBGResult
                            ( *memcheckReadErrorAddress )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t* address, ptxStorageKind* storage )
Get the address that memcheck detected an error on.

CUDBGResult
                            ( *readActiveLanes )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* activeLanesMask )
Reads the bitmask of active lanes on a valid warp.

CUDBGResult
                            ( *readAllVirtualReturnAddresses )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t* addrs, uint32_t numAddrs, uint32_t* callDepth, uint32_t* syscallCallDepth )
Reads all the virtual return addresses.

CUDBGResult
                            ( *readBlockIdx )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* blockIdx )
Reads the CUDA block index running on a valid warp.

CUDBGResult
                            ( *readBlockIdx32 )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim2* blockIdx )
Reads the two-dimensional CUDA block index running on a valid warp.

CUDBGResult
                            ( *readBrokenWarps )(  uint32_t dev, uint32_t sm, uint64_t* brokenWarpsMask )
Reads the bitmask of warps that are at a breakpoint on a given SM.

CUDBGResult
                            ( *readCCRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t* val )
Reads the hardware CC register.

CUDBGResult
                            ( *readCPUCallStack )(  uint32_t dev, uint64_t gridId64, uint64_t* addrs, uint32_t numAddrs, uint32_t* totalNumAddrs )
Read CPU call stack captured at the time of kernel launch.

CUDBGResult
                            ( *readCallDepth )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t* depth )
Reads the call depth (number of calls) for a given lane.

CUDBGResult
                            ( *readCallDepth32 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* depth )
Reads the call depth (number of calls) for a given warp.

CUDBGResult
                            ( *readClusterIdx )(  uint32_t dev, uint32_t sm, uint32_t wp, CuDim3* clusterIdx )
Reads the CUDA cluster index running on a valid warp.

CUDBGResult
                            ( *readCodeMemory )(  uint32_t dev, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the code memory segment.

CUDBGResult
                            ( *readConstMemory129 )(  uint32_t dev, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the constant memory segment.

CUDBGResult
                            ( *readDeviceExceptionState )(  uint32_t devId, uint64_t* mask, uint32_t numWords )
Get the exception state of the SMs on the device.

CUDBGResult
                            ( *readDeviceExceptionState80 )(  uint32_t devId, uint64_t* exceptionSMMask )
Get the exception state of the SMs on the device.

CUDBGResult
                            ( *readErrorPC )(  uint32_t devId, uint32_t sm, uint32_t wp, uint64_t* errorPC, bool* errorPCValid )
Get the hardware reported error PC if it exists.

CUDBGResult
                            ( *readGenericMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, void* buf, uint32_t sz )
Reads content at an address in the generic address space. This function determines if the given address falls into the local,
                           shared, or global memory window. It then accesses memory taking into account the hardware co-ordinates provided as inputs.

CUDBGResult
                            ( *readGlobalMemory )(  uint64_t addr, void* buf, uint32_t sz )
Reads content at an address in the global address space. If the address is valid on more than one device and one of those
                           devices does not support UVA, an error is returned.

CUDBGResult
                            ( *readGlobalMemory31 )(  uint32_t dev, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the global memory segment.

CUDBGResult
                            ( *readGlobalMemory55 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the global memory segment (entire 40-bit VA on Fermi+).

CUDBGResult
                            ( *readGridId )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t* gridId64 )
Reads the 64-bit CUDA grid index running on a valid warp.

CUDBGResult
                            ( *readGridId50 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* gridId )
Reads the CUDA grid index running on a valid warp.

CUDBGResult
                            ( *readLaneException )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, CUDBGException_t* exception )
Reads the exception type for a given lane.

CUDBGResult
                            ( *readLaneStatus )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, bool* error )
Reads the status of the given lane. For specific error values, use readLaneException.

CUDBGResult
                            ( *readLocalMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the local memory segment.

CUDBGResult
                            ( *readPC )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t* pc )
Reads the PC on the given active lane.

CUDBGResult
                            ( *readParamMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the param memory segment.

CUDBGResult
                            ( *readPinnedMemory )(  uint64_t addr, void* buf, uint32_t sz )
Reads content at pinned address in system memory.

CUDBGResult
                            ( *readPredicates )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t predicates_size, uint32_t* predicates )
Reads content of hardware predicate registers.

CUDBGResult
                            ( *readRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t regno, uint32_t* val )
Reads content of a hardware register.

CUDBGResult
                            ( *readRegisterRange )(  uint32_t devId, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t index, uint32_t registers_size, uint32_t* registers )
Reads content of a hardware range of hardware registers.

CUDBGResult
                            ( *readReturnAddress )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t level, uint64_t* ra )
Reads the physical return address for a call level.

CUDBGResult
                            ( *readReturnAddress32 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t level, uint64_t* ra )
Reads the physical return address for a call level.

CUDBGResult
                            ( *readSharedMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t addr, void* buf, uint32_t sz )
Reads content at address in the shared memory segment.

CUDBGResult
                            ( *readSmException )(  uint32_t dev, uint32_t sm, CUDBGException_t* exception, uint64_t* errorPC, bool* errorPCValid )
Get the SM exception status if it exists.

CUDBGResult
                            ( *readSyscallCallDepth )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t* depth )
Reads the call depth of syscalls for a given lane.

CUDBGResult
                            ( *readTextureMemory )(  uint32_t devId, uint32_t vsm, uint32_t wp, uint32_t id, uint32_t dim, uint32_t* coords, void* buf, uint32_t sz )
This method is no longer supported since CUDA 12.0.

CUDBGResult
                            ( *readTextureMemoryBindless )(  uint32_t devId, uint32_t vsm, uint32_t wp, uint32_t texSymtabIndex, uint32_t dim, uint32_t* coords, void* buf, uint32_t sz )
This method is no longer supported since CUDA 12.0.

CUDBGResult
                            ( *readThreadIdx )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, CuDim3* threadIdx )
Reads the CUDA thread index running on valid lane.

CUDBGResult
                            ( *readUniformPredicates )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t predicates_size, uint32_t* predicates )
Reads contents of uniform predicate registers.

CUDBGResult
                            ( *readUniformRegisterRange )(  uint32_t devId, uint32_t sm, uint32_t wp, uint32_t regno, uint32_t registers_size, uint32_t* registers )
Reads a range of uniform registers.

CUDBGResult
                            ( *readValidLanes )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t* validLanesMask )
Reads the bitmask of valid lanes on a given warp.

CUDBGResult
                            ( *readValidWarps )(  uint32_t dev, uint32_t sm, uint64_t* validWarpsMask )
Reads the bitmask of valid warps on a given SM.

CUDBGResult
                            ( *readVirtualPC )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t* pc )
Reads the virtual PC on the given active lane.

CUDBGResult
                            ( *readVirtualReturnAddress )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t level, uint64_t* ra )
Reads the virtual return address for a call level.

CUDBGResult
                            ( *readVirtualReturnAddress32 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t level, uint64_t* ra )
Reads the virtual return address for a call level.

CUDBGResult
                            ( *readWarpResources )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGWarpResources* resources )
Get the resources assigned to a given warp.

CUDBGResult
                            ( *readWarpState )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGWarpState* state )
Get state of a given warp.

CUDBGResult
                            ( *readWarpState120 )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGWarpState120* state )
Get state of a given warp.

CUDBGResult
                            ( *readWarpState127 )(  uint32_t dev, uint32_t sm, uint32_t wp, CUDBGWarpState127* state )
Get state of a given warp.

CUDBGResult
                            ( *readWarpState60 )(  uint32_t devId, uint32_t sm, uint32_t wp, CUDBGWarpState60* state )
Get state of a given warp.

CUDBGResult
                            ( *requestCleanupOnDetach )(  uint32_t appResumeFlag )
Request for cleanup of driver state when detaching.

CUDBGResult
                            ( *requestCleanupOnDetach55 )(   )
Request for cleanup of driver state when detaching.

CUDBGResult
                            ( *resumeDevice )(  uint32_t dev )
Resume a suspended CUDA device.

CUDBGResult
                            ( *resumeWarpsUntilPC )(  uint32_t devId, uint32_t sm, uint64_t warpMask, uint64_t virtPC )
Inserts a temporary breakpoint at the specified virtual PC, and resumes all warps in the specified bitmask on a given SM.
                           As compared to CUDBGAPI_st::resumeDevice, CUDBGAPI_st::resumeWarpsUntilPC provides finer-grain control by resuming a selected
                           set of warps on the same SM. The main intended usage is to accelerate the single-stepping process when the target PC is known
                           in advance. Instead of single-stepping each warp individually until the target PC is hit, the client can issue this API. When
                           this API is used, errors within CUDA kernels will no longer be reported precisely. In the situation where resuming warps is
                           not possible, this API will return CUDBG_ERROR_WARP_RESUME_NOT_POSSIBLE. The client should then fall back to using CUDBGAPI_st::singleStepWarp
                           or CUDBGAPI_st::resumeDevice.

CUDBGResult
                            ( *setBreakpoint )(  uint32_t dev, uint64_t addr )
Sets a breakpoint at the given instruction address for the given device. Before setting a breakpoint, CUDBGAPI_st::getAdjustedCodeAddress
                           should be called to get the adjusted breakpoint address.

CUDBGResult
                            ( *setBreakpoint31 )(  uint64_t addr )
Sets a breakpoint at the given instruction address.

CUDBGResult
                            ( *setKernelLaunchNotificationMode )(  CUDBGKernelLaunchNotifyMode mode )
Set the launch notification policy.

CUDBGResult
                            ( *setNotifyNewEventCallback )(  CUDBGNotifyNewEventCallback callback, void* userData )
Provides the API with the function to call to notify the debugger of a new application or device event.

CUDBGResult
                            ( *setNotifyNewEventCallback31 )(  CUDBGNotifyNewEventCallback31 callback, void* data )
Provides the API with the function to call to notify the debugger of a new application or device event.

CUDBGResult
                            ( *setNotifyNewEventCallback40 )(  CUDBGNotifyNewEventCallback40 callback )
Provides the API with the function to call to notify the debugger of a new application or device event.

CUDBGResult
                            ( *setNotifyNewEventCallback41 )(  CUDBGNotifyNewEventCallback41 callback )
Provides the API with the function to call to notify the debugger of a new application or device event.

CUDBGResult
                            ( *singleStepWarp )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t laneHint, uint32_t nsteps, uint32_t flags, uint64_t* warpMask )
Single step an individual warp nsteps times on a suspended CUDA device. Only the last instruction in a range should be a control
                           flow instruction.

CUDBGResult
                            ( *singleStepWarp40 )(  uint32_t dev, uint32_t sm, uint32_t wp )
Single step an individual warp on a suspended CUDA device.

CUDBGResult
                            ( *singleStepWarp41 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t* warpMask )
Single step an individual warp on a suspended CUDA device.

CUDBGResult
                            ( *suspendDevice )(  uint32_t dev )
Suspends a running CUDA device.

CUDBGResult
                            ( *unsetBreakpoint )(  uint32_t dev, uint64_t addr )
Unsets a breakpoint at the given instruction address for the given device.

CUDBGResult
                            ( *unsetBreakpoint31 )(  uint64_t addr )
Unsets a breakpoint at the given instruction address.

CUDBGResult
                            ( *writeCCRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t val )
Writes the hardware CC register.

CUDBGResult
                            ( *writeGenericMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, const void* buf, uint32_t sz )
Writes content to an address in the generic address space. This function determines if the given address falls into the local,
                           shared, or global memory window. It then accesses memory taking into account the hardware co-ordinates provided as inputs.

CUDBGResult
                            ( *writeGlobalMemory )(  uint64_t addr, const void* buf, uint32_t sz )
Writes content to an address in the global address space. If the address is valid on more than one device and one of those
                           devices does not support UVA, an error is returned.

CUDBGResult
                            ( *writeGlobalMemory31 )(  uint32_t dev, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the global memory segment.

CUDBGResult
                            ( *writeGlobalMemory55 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the global memory segment (entire 40-bit VA on Fermi+).

CUDBGResult
                            ( *writeLocalMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the local memory segment.

CUDBGResult
                            ( *writeParamMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the param memory segment.

CUDBGResult
                            ( *writePinnedMemory )(  uint64_t addr, const void* buf, uint32_t sz )
Writes content to pinned address in system memory.

CUDBGResult
                            ( *writePredicates )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t predicates_size, const uint32_t* predicates )
Writes content to hardware predicate registers.

CUDBGResult
                            ( *writeRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t ln, uint32_t regno, uint32_t val )
Writes content to a hardware register.

CUDBGResult
                            ( *writeSharedMemory )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t addr, const void* buf, uint32_t sz )
Writes content to address in the shared memory segment.

CUDBGResult
                            ( *writeUniformPredicates )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t predicates_size, const uint32_t* predicates )
Writes to uniform predicate registers.

CUDBGResult
                            ( *writeUniformRegister )(  uint32_t dev, uint32_t sm, uint32_t wp, uint32_t regno, uint32_t val )
Writes content to a uniform register.


### Variables


CUDBGResult
                              ( *CUDBGAPI_st::acknowledgeEvent30 )(  CUDBGEvent30* event )
Inform the debugger API that the event has been processed.  Since CUDA 3.0.

Note:Deprecated in CUDA 3.1.

                                 Parameters



event
- pointer to the event that has been processed

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::acknowledgeEvents42 )(   )
Inform the debugger API that synchronous events have been processed.  Since CUDA 3.1.

Note:Deprecated in CUDA 5.0.

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::acknowledgeSyncEvents )(   )
Inform the debugger API that synchronous events have been processed.  Since CUDA 5.0.

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::clearAttachState )(   )
Clear attach-specific state prior to detach.  Since CUDA 5.0.

Returns
CUDBG_SUCCESS

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
                              ( *CUDBGAPI_st::disassemble )(  uint32_t dev, uint64_t addr, uint32_t* instSize, char* buf, uint32_t sz )
Disassemble instruction at instruction address.  Since CUDA 3.0.

                                 Parameters



dev
- device index
addr
- instruction address
instSize
- instruction size (32 or 64 bits)
buf
- disassembled instruction buffer
sz
- disassembled instruction buffer size

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNKNOWN

CUDBGResult
                              ( *CUDBGAPI_st::finalize )(   )
Finalize the API and free all memory.  Since CUDA 3.0.

See also:
initialize

Returns
CUDBG_SUCCESS, CUDBG_ERROR_UNINITIALIZED, CUDBG_ERROR_COMMUNICATION_FAILURE, CUDBG_ERROR_UNKNOWN

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
                              ( *CUDBGAPI_st::getDevicePCIBusInfo )(  uint32_t devId, uint32_t* pciBusId, uint32_t* pciDevId )
Get PCI bus and device ids associated with device devId.



                                 Parameters



devId
- the cuda device id
pciBusId
- pointer where corresponding PCI BUS ID would be stored
pciDevId
- pointer where corresponding PCI DEVICE ID would be stored

Returns
CUDBG_ERROR_INVALID_ARGS, CUDBG_SUCCESS, CUDBG_ERROR_INVALID_DEVICE

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
                              ( *CUDBGAPI_st::getElfImageByHandle )(  uint32_t devId, uint64_t handle, CUDBGElfImageType type, void* elfImage, uint64_t size )
Get the relocated or non-relocated ELF image for the given handle on the given device.  The handle is provided in the ELF
                                 Image Loaded notification event.

Since CUDA 6.0.

                                 Parameters



devId
- device index
handle
- elf image handle
type
- type of the requested ELF image
elfImage
- pointer to the ELF image
size

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getErrorStringEx )(  char* buf, uint32_t bufSz, uint32_t* msgSz )
Fills a user-provided buffer with an error message encoded as a null-terminated ASCII string. The error message is specific
                                 to the last failed API call and is invalidated after every API call.  Since CUDA 12.2.


See also:
getErrorString

                                 Parameters



buf
- the destination buffer
bufSz
- the size of the destination buffer in bytes
msgSz
- the size of an error message including the terminating null character.

Returns
CUDBG_SUCCESS, CUDBG_ERROR_BUFFER_TOO_SMALL CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_UNINITIALIZED

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
                              ( *CUDBGAPI_st::getHostAddrFromDeviceAddr )(  uint32_t dev, uint64_t device_addr, uint64_t* host_addr )
given a device virtual address, return a corresponding system memory virtual address.  Since CUDA 4.1.

See also:
readGenericMemory
writeGenericMemory

                                 Parameters



dev
- device index
device_addr
- device memory address
host_addr
- returned system memory address

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_INVALID_DEVICE, CUDBG_ERROR_INVALID_CONTEXT, CUDBG_ERROR_INVALID_MEMORY_SEGMENT

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
                              ( *CUDBGAPI_st::getNextAsyncEvent50 )(  CUDBGEvent50* event )
Copies the next available event in the asynchronous event queue into 'event' and removes it from the queue. The asynchronous
                                 event queue is held separate from the normal event queue, and does not require acknowledgement from the debug client.  Since
                                 CUDA 5.0.


Note:Deprecated in CUDA 5.5.

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextAsyncEvent55 )(  CUDBGEvent55* event )
Copies the next available event in the asynchronous event queue into 'event' and removes it from the queue. The asynchronous
                                 event queue is held separate from the normal event queue, and does not require acknowledgement from the debug client.  Since
                                 CUDA 5.5.


Note:Deprecated in CUDA 6.0.

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextEvent )(  CUDBGEventQueueType type, CUDBGEvent* event )
Copies the next available event into 'event' and removes it from the queue.  Since CUDA 6.0.

                                 Parameters



type
- application event queue type
event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextEvent30 )(  CUDBGEvent30* event )
Copies the next available event in the event queue into 'event' and removes it from the queue.  Since CUDA 3.0.

Note:Deprecated in CUDA 3.1.

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextEvent32 )(  CUDBGEvent32* event )
Copies the next available event in the event queue into 'event' and removes it from the queue.  Since CUDA 3.1.

Note:Deprecated in CUDA 4.0

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextEvent42 )(  CUDBGEvent42* event )
Copies the next available event in the event queue into 'event' and removes it from the queue.  Since CUDA 4.0.

Note:Deprecated in CUDA 5.0

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextSyncEvent50 )(  CUDBGEvent50* event )
Since CUDA 5.0.

Note:Deprecated in CUDA 5.5.

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextSyncEvent55 )(  CUDBGEvent55* event )
Copies the next available event in the synchronous event queue into 'event' and removes it from the queue.  Since CUDA 5.5.

Note:Deprecated in CUDA 6.0.

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

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
                              ( *CUDBGAPI_st::getPhysicalRegister30 )(  uint64_t pc, char* reg, uint32_t* buf, uint32_t sz, uint32_t* numPhysRegs, CUDBGRegClass* regClass )
Get the physical register number(s) assigned to a virtual register name 'reg' at a given PC, if 'reg' is live at that PC.
                                 Since CUDA 3.0.


Note:Deprecated in CUDA 3.1.

                                 Parameters



pc
- Program counter
reg
- virtual register index
buf
- physical register name(s)
sz
- the physical register name buffer size
numPhysRegs
- number of physical register names returned
regClass
- the class of the physical registers

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_UKNOWN_FUNCTION, CUDBG_ERROR_UNKNOWN

CUDBGResult
                              ( *CUDBGAPI_st::getPhysicalRegister40 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t pc, char* reg, uint32_t* buf, uint32_t sz, uint32_t* numPhysRegs, CUDBGRegClass* regClass )
Get the physical register number(s) assigned to a virtual register name 'reg' at a given PC, if 'reg' is live at that PC.
                                 Get the physical register number(s) assigned to a virtual register name 'reg' at a given PC, if 'reg' is live at that PC.
                                 If a virtual register name is mapped to more than one physical register, the physical register with the lowest physical register
                                 index will contain the highest bits of the virtual register, and the physical register with the highest physical register
                                 index will contain the lowest bits.

Since CUDA 3.1.

Note:Deprecated in CUDA 4.1.

                                 Parameters



dev
- device index
sm
- SM index
wp
- warp indx
pc
- Program counter
reg
- virtual register index
buf
- physical register name(s)
sz
- the physical register name buffer size
numPhysRegs
- number of physical register names returned
regClass
- the class of the physical registers

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_UKNOWN_FUNCTION, CUDBG_ERROR_UNKNOWN

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

CUDBGResult
                              ( *CUDBGAPI_st::getSupportedDebuggerCapabilities )(  CUDBGCapabilityFlags* capabilities )
Returns debugger capabilities that are supported by this version of the API.  Since CUDA 12.5.
This API method can be called without initializing the API.

                                 Parameters



capabilities
- returned debugger capabilities

Returns
CUDBG_SUCCESS, CUDBG_ERROR_INVALID_ARGS,

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

CUDBGResult
                              ( *CUDBGAPI_st::initialize )(   )
Initialize the API.  Since CUDA 3.0.

See also:
finalize

Returns
CUDBG_SUCCESS, CUDBG_ERROR_UNKNOWN

CUDBGResult
                              ( *CUDBGAPI_st::initializeAttachStub )(   )
Initialize the attach stub.  Since CUDA 5.0.

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::isDeviceCodeAddress )(  uintptr_t addr, bool* isDeviceAddress )
Determines whether a virtual address resides within device code.  Since CUDA 3.0.

                                 Parameters



addr
- virtual address
isDeviceAddress
- true if address resides within device code

Returns
CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_UNINITIALIZED, CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::isDeviceCodeAddress55 )(  uintptr_t addr, bool* isDeviceAddress )
Determines whether a virtual address resides within device code. This API is strongly deprecated. Use CUDBGAPI_st::isDeviceCodeAddress
                                 instead.  Since CUDA 3.0.


Note:Deprecated in CUDA 6.0

                                 Parameters



addr
- virtual address
isDeviceAddress
- true if address resides within device code

Returns
CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_UNINITIALIZED, CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::lookupDeviceCodeSymbol )(  char* symName, bool* symFound, uintptr_t* symAddr )
Determines whether a symbol represents a function in device code and returns its virtual address.  Since CUDA 3.0.

                                 Parameters



symName
- symbol name
symFound
- set to true if the symbol is found
symAddr
- the symbol virtual address if found

Returns
CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_UNINITIALIZED, CUDBG_SUCCESS

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
                              ( *CUDBGAPI_st::readDeviceExceptionState )(  uint32_t devId, uint64_t* mask, uint32_t numWords )
Get the exception state of the SMs on the device.  Since CUDA 9.0

See also:
getNumSMs

                                 Parameters



devId
- the cuda device id
mask
- Arbitrarily sized bit field containing a 1 at (1 << i) if SM i hit an exception
numWords

Returns
CUDBG_ERROR_INVALID_ARGS, CUDBG_SUCCESS, CUDBG_ERROR_INVALID_DEVICE

CUDBGResult
                              ( *CUDBGAPI_st::readDeviceExceptionState80 )(  uint32_t devId, uint64_t* exceptionSMMask )
Get the exception state of the SMs on the device.  Since CUDA 5.5

Note:Deprecated in CUDA 9.0.

                                 Parameters



devId
- the cuda device id
exceptionSMMask
- Bit field containing a 1 at (1 << i) if SM i hit an exception

Returns
CUDBG_ERROR_INVALID_ARGS, CUDBG_SUCCESS, CUDBG_ERROR_INVALID_DEVICE

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
                              ( *CUDBGAPI_st::requestCleanupOnDetach )(  uint32_t appResumeFlag )
Request for cleanup of driver state when detaching.  Since CUDA 6.0.

                                 Parameters



appResumeFlag
- value of CUDBG_RESUME_FOR_ATTACH_DETACH as read from the application's process space.

Returns
CUDBG_SUCCESS CUDBG_ERROR_COMMUNICATION_FAILURE CUDBG_ERROR_INVALID_ARGS CUDBG_ERROR_INTERNAL

CUDBGResult
                              ( *CUDBGAPI_st::requestCleanupOnDetach55 )(   )
Request for cleanup of driver state when detaching.  Since CUDA 5.0.

Note:Deprecated in CUDA 6.0

Returns
CUDBG_SUCCESS CUDBG_ERROR_COMMUNICATION_FAILURE CUDBG_ERROR_INVALID_ARGS CUDBG_ERROR_INTERNAL

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
                              ( *CUDBGAPI_st::setKernelLaunchNotificationMode )(  CUDBGKernelLaunchNotifyMode mode )
Set the launch notification policy.  Since CUDA 5.5.

                                 Parameters



mode
- mode to deliver kernel launch notifications in

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::setNotifyNewEventCallback )(  CUDBGNotifyNewEventCallback callback, void* userData )
Provides the API with the function to call to notify the debugger of a new application or device event.  Since CUDA 13.0.

                                 Parameters



callback
- the callback function
userData
- user data to be passed to the callback

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::setNotifyNewEventCallback31 )(  CUDBGNotifyNewEventCallback31 callback, void* data )
Provides the API with the function to call to notify the debugger of a new application or device event.  Since CUDA 3.0.

Note:Deprecated in CUDA 3.2.

                                 Parameters



callback
- the callback function
data
- a pointer to be passed to the callback when called

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::setNotifyNewEventCallback40 )(  CUDBGNotifyNewEventCallback40 callback )
Provides the API with the function to call to notify the debugger of a new application or device event.  Since CUDA 3.2.

Note:Deprecated in CUDA 4.1.

                                 Parameters



callback
- the callback function

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::setNotifyNewEventCallback41 )(  CUDBGNotifyNewEventCallback41 callback )
Provides the API with the function to call to notify the debugger of a new application or device event.  Since CUDA 4.1.

Note:Deprecated in CUDA 13.0.

                                 Parameters



callback
- the callback function

Returns
CUDBG_SUCCESS

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