# Debugger API

[< Previous](group__DEV.html) | [Next >](group__EVENT.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 3.9. DWARF Utilities




### Variables


CUDBGResult
                            ( *CUDBGAPI_st::disassemble )(  uint32_t dev, uint64_t addr, uint32_t* instSize, char* buf, uint32_t sz )
Disassemble instruction at instruction address.

CUDBGResult
                            ( *CUDBGAPI_st::getElfImageByHandle )(  uint32_t devId, uint64_t handle, CUDBGElfImageType type, void* elfImage, uint64_t size )
Get the relocated or non-relocated ELF image for the given handle on the given device.

CUDBGResult
                            ( *CUDBGAPI_st::getHostAddrFromDeviceAddr )(  uint32_t dev, uint64_t device_addr, uint64_t* host_addr )
given a device virtual address, return a corresponding system memory virtual address.

CUDBGResult
                            ( *CUDBGAPI_st::getPhysicalRegister30 )(  uint64_t pc, char* reg, uint32_t* buf, uint32_t sz, uint32_t* numPhysRegs, CUDBGRegClass* regClass )
Get the physical register number(s) assigned to a virtual register name 'reg' at a given PC, if 'reg' is live at that PC.

CUDBGResult
                            ( *CUDBGAPI_st::getPhysicalRegister40 )(  uint32_t dev, uint32_t sm, uint32_t wp, uint64_t pc, char* reg, uint32_t* buf, uint32_t sz, uint32_t* numPhysRegs, CUDBGRegClass* regClass )
Get the physical register number(s) assigned to a virtual register name 'reg' at a given PC, if 'reg' is live at that PC.

CUDBGResult
                            ( *CUDBGAPI_st::isDeviceCodeAddress )(  uintptr_t addr, bool* isDeviceAddress )
Determines whether a virtual address resides within device code.

CUDBGResult
                            ( *CUDBGAPI_st::isDeviceCodeAddress55 )(  uintptr_t addr, bool* isDeviceAddress )
Determines whether a virtual address resides within device code. This API is strongly deprecated. Use CUDBGAPI_st::isDeviceCodeAddress
                           instead.

CUDBGResult
                            ( *CUDBGAPI_st::lookupDeviceCodeSymbol )(  char* symName, bool* symFound, uintptr_t* symAddr )
Determines whether a symbol represents a function in device code and returns its virtual address.


### Variables


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


---