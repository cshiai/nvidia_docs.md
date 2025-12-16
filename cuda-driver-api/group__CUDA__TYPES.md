# CUDA Driver API

[< Previous](modules.html) | [Next >](group__CUDA__ERROR.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.1. Data types used by CUDA driver




### Classes


struct
CUDA_ARRAY3D_DESCRIPTOR_v2struct
CUDA_ARRAY_DESCRIPTOR_v2struct
CUDA_ARRAY_MEMORY_REQUIREMENTS_v1struct
CUDA_ARRAY_SPARSE_PROPERTIES_v1struct
CUDA_BATCH_MEM_OP_NODE_PARAMS_v1struct
CUDA_BATCH_MEM_OP_NODE_PARAMS_v2struct
CUDA_CHILD_GRAPH_NODE_PARAMSstruct
CUDA_CONDITIONAL_NODE_PARAMSstruct
CUDA_EVENT_RECORD_NODE_PARAMSstruct
CUDA_EVENT_WAIT_NODE_PARAMSstruct
CUDA_EXTERNAL_MEMORY_BUFFER_DESC_v1struct
CUDA_EXTERNAL_MEMORY_HANDLE_DESC_v1struct
CUDA_EXTERNAL_MEMORY_MIPMAPPED_ARRAY_DESC_v1struct
CUDA_EXTERNAL_SEMAPHORE_HANDLE_DESC_v1struct
CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS_v1struct
CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS_v1struct
CUDA_EXT_SEM_SIGNAL_NODE_PARAMS_v1struct
CUDA_EXT_SEM_SIGNAL_NODE_PARAMS_v2struct
CUDA_EXT_SEM_WAIT_NODE_PARAMS_v1struct
CUDA_EXT_SEM_WAIT_NODE_PARAMS_v2struct
CUDA_GRAPH_INSTANTIATE_PARAMSstruct
CUDA_HOST_NODE_PARAMS_v1struct
CUDA_HOST_NODE_PARAMS_v2struct
CUDA_KERNEL_NODE_PARAMS_v1struct
CUDA_KERNEL_NODE_PARAMS_v2struct
CUDA_KERNEL_NODE_PARAMS_v3struct
CUDA_LAUNCH_PARAMS_v1struct
CUDA_MEMCPY2D_v2struct
CUDA_MEMCPY3D_PEER_v1struct
CUDA_MEMCPY3D_v2struct
CUDA_MEMCPY_NODE_PARAMSstruct
CUDA_MEMSET_NODE_PARAMS_v1struct
CUDA_MEMSET_NODE_PARAMS_v2struct
CUDA_MEM_ALLOC_NODE_PARAMS_v1struct
CUDA_MEM_ALLOC_NODE_PARAMS_v2struct
CUDA_MEM_FREE_NODE_PARAMSstruct
CUDA_POINTER_ATTRIBUTE_P2P_TOKENS_v1struct
CUDA_RESOURCE_DESC_v1struct
CUDA_RESOURCE_VIEW_DESC_v1struct
CUDA_TEXTURE_DESC_v1struct
CUaccessPolicyWindow_v1struct
CUarrayMapInfo_v1struct
CUasyncNotificationInfostruct
CUcheckpointCheckpointArgsstruct
CUcheckpointGpuPairstruct
CUcheckpointLockArgsstruct
CUcheckpointRestoreArgsstruct
CUcheckpointUnlockArgsstruct
CUctxCigParamstruct
CUctxCreateParamsstruct
CUdevprop_v1struct
CUeglFrame_v1struct
CUexecAffinityParam_v1struct
CUexecAffinitySmCount_v1struct
CUextent3D_v1struct
CUgraphEdgeDatastruct
CUgraphExecUpdateResultInfo_v1struct
CUgraphNodeParamsstruct
CUipcEventHandle_v1struct
CUipcMemHandle_v1struct
CUlaunchAttributeunion
CUlaunchAttributeValuestruct
CUlaunchConfigstruct
CUlaunchMemSyncDomainMapstruct
CUmemAccessDesc_v1struct
CUmemAllocationProp_v1struct
CUmemFabricHandle_v1struct
CUmemLocation_v1struct
CUmemPoolProps_v1struct
CUmemPoolPtrExportData_v1struct
CUmemcpy3DOperand_v1struct
CUmemcpyAttributes_v1struct
CUmulticastObjectProp_v1struct
CUoffset3D_v1union
CUstreamBatchMemOpParams_v1struct
CUtensorMap

### Defines


#define CUDA_ARRAY3D_2DARRAY 0x01#define CUDA_ARRAY3D_COLOR_ATTACHMENT 0x20#define CUDA_ARRAY3D_CUBEMAP 0x04#define CUDA_ARRAY3D_DEFERRED_MAPPING 0x80#define CUDA_ARRAY3D_DEPTH_TEXTURE 0x10#define CUDA_ARRAY3D_LAYERED 0x01#define CUDA_ARRAY3D_SPARSE 0x40#define CUDA_ARRAY3D_SURFACE_LDST 0x02#define CUDA_ARRAY3D_TEXTURE_GATHER 0x08#define CUDA_ARRAY3D_VIDEO_ENCODE_DECODE 0x100#define CUDA_COOPERATIVE_LAUNCH_MULTI_DEVICE_NO_POST_LAUNCH_SYNC 0x02#define CUDA_COOPERATIVE_LAUNCH_MULTI_DEVICE_NO_PRE_LAUNCH_SYNC 0x01#define CUDA_EGL_INFINITE_TIMEOUT 0xFFFFFFFF#define CUDA_EXTERNAL_MEMORY_DEDICATED 0x1#define CUDA_EXTERNAL_SEMAPHORE_SIGNAL_SKIP_NVSCIBUF_MEMSYNC 0x01#define CUDA_EXTERNAL_SEMAPHORE_WAIT_SKIP_NVSCIBUF_MEMSYNC 0x02#define CUDA_NVSCISYNC_ATTR_SIGNAL 0x1#define CUDA_NVSCISYNC_ATTR_WAIT 0x2#define CUDA_VERSION 13010#define CU_ARRAY_SPARSE_PROPERTIES_SINGLE_MIPTAIL 0x1#define CU_DEVICE_CPU ((CUdevice)-1)#define CU_DEVICE_INVALID ((CUdevice)-2)#define CU_GRAPH_COND_ASSIGN_DEFAULT 0x1#define CU_GRAPH_KERNEL_NODE_PORT_DEFAULT 0#define CU_GRAPH_KERNEL_NODE_PORT_LAUNCH_ORDER 2#define CU_GRAPH_KERNEL_NODE_PORT_PROGRAMMATIC 1#define CU_IPC_HANDLE_SIZE 64#define CU_LAUNCH_KERNEL_REQUIRED_BLOCK_DIM 1#define CU_LAUNCH_PARAM_BUFFER_POINTER#define CU_LAUNCH_PARAM_BUFFER_POINTER_AS_INT 0x01#define CU_LAUNCH_PARAM_BUFFER_SIZE#define CU_LAUNCH_PARAM_BUFFER_SIZE_AS_INT 0x02#define CU_LAUNCH_PARAM_END#define CU_LAUNCH_PARAM_END_AS_INT 0x00#define CU_MEMHOSTALLOC_DEVICEMAP 0x02#define CU_MEMHOSTALLOC_PORTABLE 0x01#define CU_MEMHOSTALLOC_WRITECOMBINED 0x04#define CU_MEMHOSTREGISTER_DEVICEMAP 0x02#define CU_MEMHOSTREGISTER_IOMEMORY 0x04#define CU_MEMHOSTREGISTER_PORTABLE 0x01#define CU_MEMHOSTREGISTER_READ_ONLY 0x08#define CU_MEM_CREATE_USAGE_HW_DECOMPRESS 0x2#define CU_MEM_CREATE_USAGE_TILE_POOL 0x1#define CU_MEM_POOL_CREATE_USAGE_HW_DECOMPRESS 0x2#define CU_PARAM_TR_DEFAULT -1#define CU_STREAM_LEGACY ((CUstream)0x1)#define CU_STREAM_PER_THREAD ((CUstream)0x2)#define CU_TENSOR_MAP_NUM_QWORDS 16#define CU_TRSA_OVERRIDE_FORMAT 0x01#define CU_TRSF_DISABLE_TRILINEAR_OPTIMIZATION 0x20#define CU_TRSF_NORMALIZED_COORDINATES 0x02#define CU_TRSF_READ_AS_INTEGER 0x01#define CU_TRSF_SEAMLESS_CUBEMAP 0x40#define CU_TRSF_SRGB 0x10#define MAX_PLANES 3

### Typedefs


typedef struct CUaccessPolicyWindow_v1 CUaccessPolicyWindowtypedef CUarray_st *  CUarraytypedef
                           void
                            ( *CUasyncCallback )(  CUasyncNotificationInfo*
                            info,  void*
                            userData,  CUasyncCallbackHandle callback )typedef CUasyncCallbackEntry_st *  CUasyncCallbackHandletypedef CUctx_st *  CUcontexttypedef CUdevice_v1 CUdevicetypedef int  CUdevice_v1typedef CUdeviceptr_v2 CUdeviceptrtypedef unsigned int  CUdeviceptr_v2typedef CUeglStreamConnection_st *  CUeglStreamConnectiontypedef CUevent_st *  CUeventtypedef struct CUexecAffinityParam_v1 CUexecAffinityParamtypedef CUextMemory_st *  CUexternalMemorytypedef CUextSemaphore_st *  CUexternalSemaphoretypedef CUfunc_st *  CUfunctiontypedef CUgraph_st *  CUgraphtypedef cuuint64_t  CUgraphConditionalHandletypedef CUgraphDeviceUpdatableNode_st *  CUgraphDeviceNodetypedef CUgraphExec_st *  CUgraphExectypedef CUgraphNode_st *  CUgraphNodetypedef CUgraphicsResource_st *  CUgraphicsResourcetypedef CUgreenCtx_st *  CUgreenCtxtypedef
                           void(CUDA_CB*
                            CUhostFn )(  void*
                            userData )typedef CUkern_st *  CUkerneltypedef CUlib_st *  CUlibrarytypedef CUmemPoolHandle_st *  CUmemoryPooltypedef CUmipmappedArray_st *  CUmipmappedArraytypedef CUmod_st *  CUmoduletypedef
                           size_t(CUDA_CB*
                            CUoccupancyB2DSize )(  int  blockSize )typedef CUstream_st *  CUstreamtypedef
                           void(CUDA_CB*
                            CUstreamCallback )(  CUstream hStream,  CUresult status,  void*
                            userData )typedef CUsurfObject_v1 CUsurfObjecttypedef unsigned long long  CUsurfObject_v1typedef CUsurfref_st *  CUsurfreftypedef CUtexObject_v1 CUtexObjecttypedef unsigned long long  CUtexObject_v1typedef CUtexref_st *  CUtexreftypedef CUuserObject_st *  CUuserObject

### Enumerations


enum CUDA_POINTER_ATTRIBUTE_ACCESS_FLAGSenum CUGPUDirectRDMAWritesOrderingenum CUaccessPropertyenum CUaddress_modeenum CUarraySparseSubresourceTypeenum CUarray_cubemap_faceenum CUarray_formatenum CUasyncNotificationTypeenum CUatomicOperationenum CUatomicOperationCapabilityenum CUclusterSchedulingPolicyenum CUcomputemodeenum CUctx_flagsenum CUdeviceNumaConfigenum CUdevice_P2PAttributeenum CUdevice_attributeenum CUdriverProcAddressQueryResultenum CUdriverProcAddress_flagsenum CUeglColorFormatenum CUeglFrameTypeenum CUeglResourceLocationFlagsenum CUevent_flagsenum CUevent_record_flagsenum CUevent_sched_flagsenum CUevent_wait_flagsenum CUexecAffinityTypeenum CUexternalMemoryHandleTypeenum CUexternalSemaphoreHandleTypeenum CUfilter_modeenum CUflushGPUDirectRDMAWritesOptionsenum CUflushGPUDirectRDMAWritesScopeenum CUflushGPUDirectRDMAWritesTargetenum CUfunc_cacheenum CUfunction_attributeenum CUgraphChildGraphNodeOwnershipenum CUgraphConditionalNodeTypeenum CUgraphDebugDot_flagsenum CUgraphDependencyTypeenum CUgraphExecUpdateResultenum CUgraphInstantiateResultenum CUgraphInstantiate_flagsenum CUgraphNodeTypeenum CUgraphicsMapResourceFlagsenum CUgraphicsRegisterFlagsenum CUipcMem_flagsenum CUjitInputTypeenum CUjit_cacheModeenum CUjit_fallbackenum CUjit_optionenum CUjit_targetenum CUlaunchAttributeIDenum CUlaunchMemSyncDomainenum CUlibraryOptionenum CUlimitenum CUmemAccess_flagsenum CUmemAllocationCompTypeenum CUmemAllocationGranularity_flagsenum CUmemAllocationHandleTypeenum CUmemAllocationTypeenum CUmemAttach_flagsenum CUmemHandleTypeenum CUmemLocationTypeenum CUmemOperationTypeenum CUmemPool_attributeenum CUmemRangeFlagsenum CUmemRangeHandleTypeenum CUmem_adviseenum CUmemcpy3DOperandTypeenum CUmemcpyFlagsenum CUmemcpySrcAccessOrderenum CUmemorytypeenum CUmulticastGranularity_flagsenum CUoccupancy_flagsenum CUpointer_attributeenum CUprocessStateenum CUresourceViewFormatenum CUresourcetypeenum CUresultenum CUshared_carveoutenum CUsharedconfigenum CUstreamAtomicReductionDataTypeenum CUstreamAtomicReductionOpTypeenum CUstreamBatchMemOpTypeenum CUstreamCaptureModeenum CUstreamCaptureStatusenum CUstreamMemoryBarrier_flagsenum CUstreamUpdateCaptureDependencies_flagsenum CUstreamWaitValue_flagsenum CUstreamWriteValue_flagsenum CUstream_flagsenum CUtensorMapDataTypeenum CUtensorMapFloatOOBfillenum CUtensorMapIm2ColWideModeenum CUtensorMapInterleaveenum CUtensorMapL2promotionenum CUtensorMapSwizzleenum CUuserObjectRetain_flagsenum CUuserObject_flagsenum cl_context_flagsenum cl_event_flags

### Defines


#define CUDA_ARRAY3D_2DARRAY 0x01
Deprecated, use CUDA_ARRAY3D_LAYERED

#define CUDA_ARRAY3D_COLOR_ATTACHMENT 0x20
This flag indicates that the CUDA array may be bound as a color target in an external graphics API

#define CUDA_ARRAY3D_CUBEMAP 0x04
If set, the CUDA array is a collection of six 2D arrays, representing faces of a cube. The width of such a CUDA array must
                                 be equal to its height, and Depth must be six. If CUDA_ARRAY3D_LAYERED flag is also set, then the CUDA array is a collection of cubemaps and Depth must be a multiple of six.

#define CUDA_ARRAY3D_DEFERRED_MAPPING 0x80
This flag if set indicates that the CUDA array or CUDA mipmapped array will allow deferred memory mapping

#define CUDA_ARRAY3D_DEPTH_TEXTURE 0x10
This flag if set indicates that the CUDA array is a DEPTH_TEXTURE.

#define CUDA_ARRAY3D_LAYERED 0x01
If set, the CUDA array is a collection of layers, where each layer is either a 1D or a 2D array and the Depth member of CUDA_ARRAY3D_DESCRIPTOR
                                 specifies the number of layers, not the depth of a 3D array.

#define CUDA_ARRAY3D_SPARSE 0x40
This flag if set indicates that the CUDA array or CUDA mipmapped array is a sparse CUDA array or CUDA mipmapped array respectively

#define CUDA_ARRAY3D_SURFACE_LDST 0x02
This flag must be set in order to bind a surface reference to the CUDA array

#define CUDA_ARRAY3D_TEXTURE_GATHER 0x08
This flag must be set in order to perform texture gather operations on a CUDA array.

#define CUDA_ARRAY3D_VIDEO_ENCODE_DECODE 0x100
This flag indicates that the CUDA array will be used for hardware accelerated video encode/decode operations.

#define CUDA_COOPERATIVE_LAUNCH_MULTI_DEVICE_NO_POST_LAUNCH_SYNC 0x02
If set, any subsequent work pushed in a stream that participated in a call to cuLaunchCooperativeKernelMultiDevice will only wait for the kernel launched on the GPU corresponding to that stream to complete before it begins execution.

#define CUDA_COOPERATIVE_LAUNCH_MULTI_DEVICE_NO_PRE_LAUNCH_SYNC 0x01
If set, each kernel launched as part of cuLaunchCooperativeKernelMultiDevice only waits for prior work in the stream corresponding to that GPU to complete before the kernel begins execution.

#define CUDA_EGL_INFINITE_TIMEOUT 0xFFFFFFFF
Indicates that timeout for cuEGLStreamConsumerAcquireFrame is infinite.

#define CUDA_EXTERNAL_MEMORY_DEDICATED 0x1
Indicates that the external memory object is a dedicated resource

#define CUDA_EXTERNAL_SEMAPHORE_SIGNAL_SKIP_NVSCIBUF_MEMSYNC 0x01
When the flags parameter of CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS contains this flag, it indicates that signaling an external semaphore
                                 object should skip performing appropriate memory synchronization operations over all the external memory objects that are
                                 imported as CU_EXTERNAL_MEMORY_HANDLE_TYPE_NVSCIBUF, which otherwise are performed by default to ensure data coherency with other importers of the same NvSciBuf memory objects.

#define CUDA_EXTERNAL_SEMAPHORE_WAIT_SKIP_NVSCIBUF_MEMSYNC 0x02
When the flags parameter of CUDA_EXTERNAL_SEMAPHORE_WAIT_PARAMS contains this flag, it indicates that waiting on an external semaphore object
                                 should skip performing appropriate memory synchronization operations over all the external memory objects that are imported
                                 as CU_EXTERNAL_MEMORY_HANDLE_TYPE_NVSCIBUF, which otherwise are performed by default to ensure data coherency with other importers of the same NvSciBuf memory objects.

#define CUDA_NVSCISYNC_ATTR_SIGNAL 0x1
When flags of cuDeviceGetNvSciSyncAttributes is set to this, it indicates that application needs signaler specific NvSciSyncAttr to be filled by cuDeviceGetNvSciSyncAttributes.

#define CUDA_NVSCISYNC_ATTR_WAIT 0x2
When flags of cuDeviceGetNvSciSyncAttributes is set to this, it indicates that application needs waiter specific NvSciSyncAttr to be filled by cuDeviceGetNvSciSyncAttributes.

#define CUDA_VERSION 13010
CUDA API version number

#define CU_ARRAY_SPARSE_PROPERTIES_SINGLE_MIPTAIL 0x1
Indicates that the layered sparse CUDA array or CUDA mipmapped array has a single mip tail region for all layers

#define CU_DEVICE_CPU ((CUdevice)-1)
Device that represents the CPU

#define CU_DEVICE_INVALID ((CUdevice)-2)
Device that represents an invalid device

#define CU_GRAPH_COND_ASSIGN_DEFAULT 0x1
Conditional node handle flags Default value is applied when graph is launched.

#define CU_GRAPH_KERNEL_NODE_PORT_DEFAULT 0
This port activates when the kernel has finished executing.

#define CU_GRAPH_KERNEL_NODE_PORT_LAUNCH_ORDER 2
This port activates when all blocks of the kernel have begun execution. See also CU_LAUNCH_ATTRIBUTE_LAUNCH_COMPLETION_EVENT.

#define CU_GRAPH_KERNEL_NODE_PORT_PROGRAMMATIC 1
This port activates when all blocks of the kernel have performed cudaTriggerProgrammaticLaunchCompletion() or have terminated. It must be used with edge type CU_GRAPH_DEPENDENCY_TYPE_PROGRAMMATIC. See also CU_LAUNCH_ATTRIBUTE_PROGRAMMATIC_EVENT.

#define CU_IPC_HANDLE_SIZE 64
CUDA IPC handle size

#define CU_LAUNCH_KERNEL_REQUIRED_BLOCK_DIM 1
Launch with the required block dimension.

#define CU_LAUNCH_PARAM_BUFFER_POINTER
Indicator that the next value in the extra parameter to cuLaunchKernel will be a pointer to a buffer containing all kernel parameters used for launching kernel f. This buffer needs to honor all alignment/padding requirements of the individual parameters. If CU_LAUNCH_PARAM_BUFFER_SIZE is not also specified in the extra array, then CU_LAUNCH_PARAM_BUFFER_POINTER will have no effect.


                                 Value


((void*)CU_LAUNCH_PARAM_BUFFER_POINTER_AS_INT)

#define CU_LAUNCH_PARAM_BUFFER_POINTER_AS_INT 0x01
C++ compile time constant for CU_LAUNCH_PARAM_BUFFER_POINTER

#define CU_LAUNCH_PARAM_BUFFER_SIZE
Indicator that the next value in the extra parameter to cuLaunchKernel will be a pointer to a size_t which contains the size of the buffer specified with CU_LAUNCH_PARAM_BUFFER_POINTER. It is required that CU_LAUNCH_PARAM_BUFFER_POINTER also be specified in the extra array if the value associated with CU_LAUNCH_PARAM_BUFFER_SIZE is not zero.


                                 Value


((void*)CU_LAUNCH_PARAM_BUFFER_SIZE_AS_INT)

#define CU_LAUNCH_PARAM_BUFFER_SIZE_AS_INT 0x02
C++ compile time constant for CU_LAUNCH_PARAM_BUFFER_SIZE

#define CU_LAUNCH_PARAM_END
End of array terminator for the extra parameter to cuLaunchKernel

                                 Value


((void*)CU_LAUNCH_PARAM_END_AS_INT)

#define CU_LAUNCH_PARAM_END_AS_INT 0x00
C++ compile time constant for CU_LAUNCH_PARAM_END

#define CU_MEMHOSTALLOC_DEVICEMAP 0x02
If set, host memory is mapped into CUDA address space and cuMemHostGetDevicePointer() may be called on the host pointer. Flag for cuMemHostAlloc()

#define CU_MEMHOSTALLOC_PORTABLE 0x01
If set, host memory is portable between CUDA contexts. Flag for cuMemHostAlloc()

#define CU_MEMHOSTALLOC_WRITECOMBINED 0x04
If set, host memory is allocated as write-combined - fast to write, faster to DMA, slow to read except via SSE4 streaming
                                 load instruction (MOVNTDQA). Flag for cuMemHostAlloc()

#define CU_MEMHOSTREGISTER_DEVICEMAP 0x02
If set, host memory is mapped into CUDA address space and cuMemHostGetDevicePointer() may be called on the host pointer. Flag for cuMemHostRegister()

#define CU_MEMHOSTREGISTER_IOMEMORY 0x04
If set, the passed memory pointer is treated as pointing to some memory-mapped I/O space, e.g. belonging to a third-party
                                 PCIe device. On Windows the flag is a no-op. On Linux that memory is marked as non cache-coherent for the GPU and is expected
                                 to be physically contiguous. It may return CUDA_ERROR_NOT_PERMITTED if run as an unprivileged user, CUDA_ERROR_NOT_SUPPORTED on older Linux kernel versions. On all other platforms, it is not supported and CUDA_ERROR_NOT_SUPPORTED is returned. Flag for cuMemHostRegister()

#define CU_MEMHOSTREGISTER_PORTABLE 0x01
If set, host memory is portable between CUDA contexts. Flag for cuMemHostRegister()

#define CU_MEMHOSTREGISTER_READ_ONLY 0x08
If set, the passed memory pointer is treated as pointing to memory that is considered read-only by the device. On platforms
                                 without CU_DEVICE_ATTRIBUTE_PAGEABLE_MEMORY_ACCESS_USES_HOST_PAGE_TABLES, this flag is required in order to register memory mapped to the CPU as read-only. Support for the use of this flag can be
                                 queried from the device attribute CU_DEVICE_ATTRIBUTE_READ_ONLY_HOST_REGISTER_SUPPORTED. Using this flag with a current context associated with a device that does not have this attribute set will cause cuMemHostRegister to error with CUDA_ERROR_NOT_SUPPORTED.

#define CU_MEM_CREATE_USAGE_HW_DECOMPRESS 0x2
This flag, if set, indicates that the memory will be used as a buffer for hardware accelerated decompression.

#define CU_MEM_CREATE_USAGE_TILE_POOL 0x1
This flag if set indicates that the memory will be used as a tile pool.

#define CU_MEM_POOL_CREATE_USAGE_HW_DECOMPRESS 0x2
This flag, if set, indicates that the memory will be used as a buffer for hardware accelerated decompression.

#define CU_PARAM_TR_DEFAULT -1
For texture references loaded into the module, use default texunit from texture reference.

#define CU_STREAM_LEGACY ((CUstream)0x1)
Legacy stream handle
Stream handle that can be passed as a CUstream to use an implicit stream with legacy synchronization behavior.
See details of the  synchronization behavior.

#define CU_STREAM_PER_THREAD ((CUstream)0x2)
Per-thread stream handle
Stream handle that can be passed as a CUstream to use an implicit stream with per-thread synchronization behavior.
See details of the  synchronization behavior.

#define CU_TENSOR_MAP_NUM_QWORDS 16
Size of tensor map descriptor

#define CU_TRSA_OVERRIDE_FORMAT 0x01
Override the texref format with a format inferred from the array. Flag for cuTexRefSetArray()

#define CU_TRSF_DISABLE_TRILINEAR_OPTIMIZATION 0x20
Disable any trilinear filtering optimizations. Flag for cuTexRefSetFlags() and cuTexObjectCreate()

#define CU_TRSF_NORMALIZED_COORDINATES 0x02
Use normalized texture coordinates in the range [0,1) instead of [0,dim). Flag for cuTexRefSetFlags() and cuTexObjectCreate()

#define CU_TRSF_READ_AS_INTEGER 0x01
Read the texture as integers rather than promoting the values to floats in the range [0,1]. Flag for cuTexRefSetFlags() and cuTexObjectCreate()

#define CU_TRSF_SEAMLESS_CUBEMAP 0x40
Enable seamless cube map filtering. Flag for cuTexObjectCreate()

#define CU_TRSF_SRGB 0x10
Perform sRGB->linear conversion during texture read. Flag for cuTexRefSetFlags() and cuTexObjectCreate()

#define MAX_PLANES 3
Maximum number of planes per frame


### Typedefs


typedef struct CUaccessPolicyWindow_v1 CUaccessPolicyWindow
Access policy window

typedef CUarray_st *  CUarray
CUDA array

void
                              ( *CUasyncCallback )(  CUasyncNotificationInfo*
                               info,  void*
                               userData,  CUasyncCallbackHandle callback )
CUDA async notification callback

typedef CUasyncCallbackEntry_st *  CUasyncCallbackHandle
CUDA async notification callback handle

typedef CUctx_st *  CUcontext
A regular context handle

typedef CUdevice_v1 CUdevice
CUDA device

typedef int  CUdevice_v1
CUDA device

typedef CUdeviceptr_v2 CUdeviceptr
CUDA device pointer

typedef unsigned int  CUdeviceptr_v2
CUDA device pointer CUdeviceptr is defined as an unsigned integer type whose size matches the size of a pointer on the target
                                 platform.

typedef CUeglStreamConnection_st *  CUeglStreamConnection
CUDA EGLSream Connection

typedef CUevent_st *  CUevent
CUDA event

typedef struct CUexecAffinityParam_v1 CUexecAffinityParam
Execution Affinity Parameters

typedef CUextMemory_st *  CUexternalMemory
CUDA external memory

typedef CUextSemaphore_st *  CUexternalSemaphore
CUDA external semaphore

typedef CUfunc_st *  CUfunction
CUDA function

typedef CUgraph_st *  CUgraph
CUDA graph

typedef cuuint64_t  CUgraphConditionalHandle
CUDA graph conditional handle

typedef CUgraphDeviceUpdatableNode_st *  CUgraphDeviceNode
CUDA graph device node handle

typedef CUgraphExec_st *  CUgraphExec
CUDA executable graph

typedef CUgraphNode_st *  CUgraphNode
CUDA graph node

typedef CUgraphicsResource_st *  CUgraphicsResource
CUDA graphics interop resource

typedef CUgreenCtx_st *  CUgreenCtx
A green context handle. This handle can be used safely from only one CPU thread at a time. Created via cuGreenCtxCreate

void(CUDA_CB*
                              CUhostFn )(  void*
                               userData )
CUDA host function

typedef CUkern_st *  CUkernel
CUDA kernel

typedef CUlib_st *  CUlibrary
CUDA library

typedef CUmemPoolHandle_st *  CUmemoryPool
CUDA memory pool

typedef CUmipmappedArray_st *  CUmipmappedArray
CUDA mipmapped array

typedef CUmod_st *  CUmodule
CUDA module

size_t(CUDA_CB*
                              CUoccupancyB2DSize )(  int  blockSize )
Block size to per-block dynamic shared memory mapping for a certain kernel

typedef CUstream_st *  CUstream
CUDA stream

void(CUDA_CB*
                              CUstreamCallback )(  CUstream hStream,  CUresult status,  void*
                               userData )
CUDA stream callback

typedef CUsurfObject_v1 CUsurfObject
An opaque value that represents a CUDA surface object

typedef unsigned long long  CUsurfObject_v1
An opaque value that represents a CUDA surface object

typedef CUsurfref_st *  CUsurfref
CUDA surface reference

typedef CUtexObject_v1 CUtexObject
An opaque value that represents a CUDA texture object

typedef unsigned long long  CUtexObject_v1
An opaque value that represents a CUDA texture object

typedef CUtexref_st *  CUtexref
CUDA texture reference

typedef CUuserObject_st *  CUuserObject
CUDA user object for graphs


### Enumerations


enum CUDA_POINTER_ATTRIBUTE_ACCESS_FLAGS
Access flags that specify the level of access the current context's device has on the memory referenced.

                                 Values



CU_POINTER_ATTRIBUTE_ACCESS_FLAG_NONE = 0x0
No access, meaning the device cannot access this memory at all, thus must be staged through accessible memory in order to
                                    complete certain operations

CU_POINTER_ATTRIBUTE_ACCESS_FLAG_READ = 0x1
Read-only access, meaning writes to this memory are considered invalid accesses and thus return error in that case.
CU_POINTER_ATTRIBUTE_ACCESS_FLAG_READWRITE = 0x3
Read-write access, the device has full read-write access to the memory

enum CUGPUDirectRDMAWritesOrdering
Platform native ordering for GPUDirect RDMA writes

                                 Values



CU_GPU_DIRECT_RDMA_WRITES_ORDERING_NONE = 0
The device does not natively support ordering of remote writes. cuFlushGPUDirectRDMAWrites() can be leveraged if supported.

CU_GPU_DIRECT_RDMA_WRITES_ORDERING_OWNER = 100
Natively, the device can consistently consume remote writes, although other CUDA devices may not.
CU_GPU_DIRECT_RDMA_WRITES_ORDERING_ALL_DEVICES = 200
Any CUDA device in the system can consistently consume remote writes to this device.

enum CUaccessProperty
Specifies performance hint with CUaccessPolicyWindow for hitProp and missProp members.


                                 Values



CU_ACCESS_PROPERTY_NORMAL = 0
Normal cache persistence.
CU_ACCESS_PROPERTY_STREAMING = 1
Streaming access is less likely to persit from cache.
CU_ACCESS_PROPERTY_PERSISTING = 2
Persisting access is more likely to persist in cache.

enum CUaddress_mode
Texture reference addressing modes

                                 Values



CU_TR_ADDRESS_MODE_WRAP = 0
Wrapping address mode
CU_TR_ADDRESS_MODE_CLAMP = 1
Clamp to edge address mode
CU_TR_ADDRESS_MODE_MIRROR = 2
Mirror address mode
CU_TR_ADDRESS_MODE_BORDER = 3
Border address mode

enum CUarraySparseSubresourceType
Sparse subresource types

                                 Values



CU_ARRAY_SPARSE_SUBRESOURCE_TYPE_SPARSE_LEVEL = 0

CU_ARRAY_SPARSE_SUBRESOURCE_TYPE_MIPTAIL = 1

enum CUarray_cubemap_face
Array indices for cube faces

                                 Values



CU_CUBEMAP_FACE_POSITIVE_X = 0x00
Positive X face of cubemap
CU_CUBEMAP_FACE_NEGATIVE_X = 0x01
Negative X face of cubemap
CU_CUBEMAP_FACE_POSITIVE_Y = 0x02
Positive Y face of cubemap
CU_CUBEMAP_FACE_NEGATIVE_Y = 0x03
Negative Y face of cubemap
CU_CUBEMAP_FACE_POSITIVE_Z = 0x04
Positive Z face of cubemap
CU_CUBEMAP_FACE_NEGATIVE_Z = 0x05
Negative Z face of cubemap

enum CUarray_format
Array formats

                                 Values



CU_AD_FORMAT_UNSIGNED_INT8 = 0x01
Unsigned 8-bit integers
CU_AD_FORMAT_UNSIGNED_INT16 = 0x02
Unsigned 16-bit integers
CU_AD_FORMAT_UNSIGNED_INT32 = 0x03
Unsigned 32-bit integers
CU_AD_FORMAT_SIGNED_INT8 = 0x08
Signed 8-bit integers
CU_AD_FORMAT_SIGNED_INT16 = 0x09
Signed 16-bit integers
CU_AD_FORMAT_SIGNED_INT32 = 0x0a
Signed 32-bit integers
CU_AD_FORMAT_HALF = 0x10
16-bit floating point
CU_AD_FORMAT_FLOAT = 0x20
32-bit floating point
CU_AD_FORMAT_NV12 = 0xb0
8-bit YUV planar format, with 4:2:0 sampling
CU_AD_FORMAT_UNORM_INT8X1 = 0xc0
1 channel unsigned 8-bit normalized integer
CU_AD_FORMAT_UNORM_INT8X2 = 0xc1
2 channel unsigned 8-bit normalized integer
CU_AD_FORMAT_UNORM_INT8X4 = 0xc2
4 channel unsigned 8-bit normalized integer
CU_AD_FORMAT_UNORM_INT16X1 = 0xc3
1 channel unsigned 16-bit normalized integer
CU_AD_FORMAT_UNORM_INT16X2 = 0xc4
2 channel unsigned 16-bit normalized integer
CU_AD_FORMAT_UNORM_INT16X4 = 0xc5
4 channel unsigned 16-bit normalized integer
CU_AD_FORMAT_SNORM_INT8X1 = 0xc6
1 channel signed 8-bit normalized integer
CU_AD_FORMAT_SNORM_INT8X2 = 0xc7
2 channel signed 8-bit normalized integer
CU_AD_FORMAT_SNORM_INT8X4 = 0xc8
4 channel signed 8-bit normalized integer
CU_AD_FORMAT_SNORM_INT16X1 = 0xc9
1 channel signed 16-bit normalized integer
CU_AD_FORMAT_SNORM_INT16X2 = 0xca
2 channel signed 16-bit normalized integer
CU_AD_FORMAT_SNORM_INT16X4 = 0xcb
4 channel signed 16-bit normalized integer
CU_AD_FORMAT_BC1_UNORM = 0x91
4 channel unsigned normalized block-compressed (BC1 compression) format
CU_AD_FORMAT_BC1_UNORM_SRGB = 0x92
4 channel unsigned normalized block-compressed (BC1 compression) format with sRGB encoding
CU_AD_FORMAT_BC2_UNORM = 0x93
4 channel unsigned normalized block-compressed (BC2 compression) format
CU_AD_FORMAT_BC2_UNORM_SRGB = 0x94
4 channel unsigned normalized block-compressed (BC2 compression) format with sRGB encoding
CU_AD_FORMAT_BC3_UNORM = 0x95
4 channel unsigned normalized block-compressed (BC3 compression) format
CU_AD_FORMAT_BC3_UNORM_SRGB = 0x96
4 channel unsigned normalized block-compressed (BC3 compression) format with sRGB encoding
CU_AD_FORMAT_BC4_UNORM = 0x97
1 channel unsigned normalized block-compressed (BC4 compression) format
CU_AD_FORMAT_BC4_SNORM = 0x98
1 channel signed normalized block-compressed (BC4 compression) format
CU_AD_FORMAT_BC5_UNORM = 0x99
2 channel unsigned normalized block-compressed (BC5 compression) format
CU_AD_FORMAT_BC5_SNORM = 0x9a
2 channel signed normalized block-compressed (BC5 compression) format
CU_AD_FORMAT_BC6H_UF16 = 0x9b
3 channel unsigned half-float block-compressed (BC6H compression) format
CU_AD_FORMAT_BC6H_SF16 = 0x9c
3 channel signed half-float block-compressed (BC6H compression) format
CU_AD_FORMAT_BC7_UNORM = 0x9d
4 channel unsigned normalized block-compressed (BC7 compression) format
CU_AD_FORMAT_BC7_UNORM_SRGB = 0x9e
4 channel unsigned normalized block-compressed (BC7 compression) format with sRGB encoding
CU_AD_FORMAT_P010 = 0x9f
10-bit YUV planar format, with 4:2:0 sampling
CU_AD_FORMAT_P016 = 0xa1
16-bit YUV planar format, with 4:2:0 sampling
CU_AD_FORMAT_NV16 = 0xa2
8-bit YUV planar format, with 4:2:2 sampling
CU_AD_FORMAT_P210 = 0xa3
10-bit YUV planar format, with 4:2:2 sampling
CU_AD_FORMAT_P216 = 0xa4
16-bit YUV planar format, with 4:2:2 sampling
CU_AD_FORMAT_YUY2 = 0xa5
2 channel, 8-bit YUV packed planar format, with 4:2:2 sampling
CU_AD_FORMAT_Y210 = 0xa6
2 channel, 10-bit YUV packed planar format, with 4:2:2 sampling
CU_AD_FORMAT_Y216 = 0xa7
2 channel, 16-bit YUV packed planar format, with 4:2:2 sampling
CU_AD_FORMAT_AYUV = 0xa8
4 channel, 8-bit YUV packed planar format, with 4:4:4 sampling
CU_AD_FORMAT_Y410 = 0xa9
10-bit YUV packed planar format, with 4:4:4 sampling
CU_AD_FORMAT_Y416 = 0xb1
4 channel, 12-bit YUV packed planar format, with 4:4:4 sampling
CU_AD_FORMAT_Y444_PLANAR8 = 0xb2
3 channel 8-bit YUV planar format, with 4:4:4 sampling
CU_AD_FORMAT_Y444_PLANAR10 = 0xb3
3 channel 10-bit YUV planar format, with 4:4:4 sampling
CU_AD_FORMAT_YUV444_8bit_SemiPlanar = 0xb4
3 channel 8-bit YUV semi-planar format, with 4:4:4 sampling
CU_AD_FORMAT_YUV444_16bit_SemiPlanar = 0xb5
3 channel 16-bit YUV semi-planar format, with 4:4:4 sampling
CU_AD_FORMAT_UNORM_INT_101010_2 = 0x50
4 channel unorm R10G10B10A2 RGB format
CU_AD_FORMAT_UINT8_PACKED_422 = 0x51
4 channel unsigned 8-bit YUV packed format, with 4:2:2 sampling
CU_AD_FORMAT_UINT8_PACKED_444 = 0x52
4 channel unsigned 8-bit YUV packed format, with 4:4:4 sampling
CU_AD_FORMAT_UINT8_SEMIPLANAR_420 = 0x53
3 channel unsigned 8-bit YUV semi-planar format, with 4:2:0 sampling
CU_AD_FORMAT_UINT16_SEMIPLANAR_420 = 0x54
3 channel unsigned 16-bit YUV semi-planar format, with 4:2:0 sampling
CU_AD_FORMAT_UINT8_SEMIPLANAR_422 = 0x55
3 channel unsigned 8-bit YUV semi-planar format, with 4:2:2 sampling
CU_AD_FORMAT_UINT16_SEMIPLANAR_422 = 0x56
3 channel unsigned 16-bit YUV semi-planar format, with 4:2:2 sampling
CU_AD_FORMAT_UINT8_SEMIPLANAR_444 = 0x57
3 channel unsigned 8-bit YUV semi-planar format, with 4:4:4 sampling
CU_AD_FORMAT_UINT16_SEMIPLANAR_444 = 0x58
3 channel unsigned 16-bit YUV semi-planar format, with 4:4:4 sampling
CU_AD_FORMAT_UINT8_PLANAR_420 = 0x59
3 channel unsigned 8-bit YUV planar format, with 4:2:0 sampling
CU_AD_FORMAT_UINT16_PLANAR_420 = 0x5a
3 channel unsigned 16-bit YUV planar format, with 4:2:0 sampling
CU_AD_FORMAT_UINT8_PLANAR_422 = 0x5b
3 channel unsigned 8-bit YUV planar format, with 4:2:2 sampling
CU_AD_FORMAT_UINT16_PLANAR_422 = 0x5c
3 channel unsigned 16-bit YUV planar format, with 4:2:2 sampling
CU_AD_FORMAT_UINT8_PLANAR_444 = 0x5d
3 channel unsigned 8-bit YUV planar format, with 4:4:4 sampling
CU_AD_FORMAT_UINT16_PLANAR_444 = 0x5e
3 channel unsigned 16-bit YUV planar format, with 4:4:4 sampling
CU_AD_FORMAT_MAX = 0x7FFFFFFF

enum CUasyncNotificationType
Types of async notification that can be sent

                                 Values



CU_ASYNC_NOTIFICATION_TYPE_OVER_BUDGET = 0x1
Sent when the process has exceeded its device memory budget

enum CUatomicOperation
CUDA-valid Atomic Operations

                                 Values



CU_ATOMIC_OPERATION_INTEGER_ADD = 0

CU_ATOMIC_OPERATION_INTEGER_MIN = 1

CU_ATOMIC_OPERATION_INTEGER_MAX = 2

CU_ATOMIC_OPERATION_INTEGER_INCREMENT = 3

CU_ATOMIC_OPERATION_INTEGER_DECREMENT = 4

CU_ATOMIC_OPERATION_AND = 5

CU_ATOMIC_OPERATION_OR = 6

CU_ATOMIC_OPERATION_XOR = 7

CU_ATOMIC_OPERATION_EXCHANGE = 8

CU_ATOMIC_OPERATION_CAS = 9

CU_ATOMIC_OPERATION_FLOAT_ADD = 10

CU_ATOMIC_OPERATION_FLOAT_MIN = 11

CU_ATOMIC_OPERATION_FLOAT_MAX = 12

CU_ATOMIC_OPERATION_MAX

enum CUatomicOperationCapability
CUDA-valid Atomic Operation capabilities

                                 Values



CU_ATOMIC_CAPABILITY_SIGNED = 1u<<0

CU_ATOMIC_CAPABILITY_UNSIGNED = 1u<<1

CU_ATOMIC_CAPABILITY_REDUCTION = 1u<<2

CU_ATOMIC_CAPABILITY_SCALAR_32 = 1u<<3

CU_ATOMIC_CAPABILITY_SCALAR_64 = 1u<<4

CU_ATOMIC_CAPABILITY_SCALAR_128 = 1u<<5

CU_ATOMIC_CAPABILITY_VECTOR_32x4 = 1u<<6

enum CUclusterSchedulingPolicy
Cluster scheduling policies. These may be passed to cuFuncSetAttribute or cuKernelSetAttribute

                                 Values



CU_CLUSTER_SCHEDULING_POLICY_DEFAULT = 0
the default policy
CU_CLUSTER_SCHEDULING_POLICY_SPREAD = 1
spread the blocks within a cluster to the SMs
CU_CLUSTER_SCHEDULING_POLICY_LOAD_BALANCING = 2
allow the hardware to load-balance the blocks in a cluster to the SMs

enum CUcomputemode
Compute Modes

                                 Values



CU_COMPUTEMODE_DEFAULT = 0
Default compute mode (Multiple contexts allowed per device)
CU_COMPUTEMODE_PROHIBITED = 2
Compute-prohibited mode (No contexts can be created on this device at this time)
CU_COMPUTEMODE_EXCLUSIVE_PROCESS = 3
Compute-exclusive-process mode (Only one context used by a single process can be present on this device at a time)

enum CUctx_flags
Context creation flags

                                 Values



CU_CTX_SCHED_AUTO = 0x00
Automatic scheduling
CU_CTX_SCHED_SPIN = 0x01
Set spin as default scheduling
CU_CTX_SCHED_YIELD = 0x02
Set yield as default scheduling
CU_CTX_SCHED_BLOCKING_SYNC = 0x04
Set blocking synchronization as default scheduling
CU_CTX_BLOCKING_SYNC = 0x04

Deprecated
This flag was deprecated as of CUDA 4.0 and was replaced with CU_CTX_SCHED_BLOCKING_SYNC.
Set blocking synchronization as default scheduling



CU_CTX_SCHED_MASK = 0x07

CU_CTX_MAP_HOST = 0x08

Deprecated
This flag was deprecated as of CUDA 11.0 and it no longer has any effect. All contexts as of CUDA 3.2 behave as though the
                                          flag is enabled.

CU_CTX_LMEM_RESIZE_TO_MAX = 0x10
Keep local memory allocation after launch
CU_CTX_COREDUMP_ENABLE = 0x20
Trigger coredumps from exceptions in this context
CU_CTX_USER_COREDUMP_ENABLE = 0x40
Enable user pipe to trigger coredumps in this context
CU_CTX_SYNC_MEMOPS = 0x80
Ensure synchronous memory operations on this context will synchronize
CU_CTX_FLAGS_MASK = 0xFF

enum CUdeviceNumaConfig
CUDA device NUMA configuration

                                 Values



CU_DEVICE_NUMA_CONFIG_NONE = 0
The GPU is not a NUMA node
CU_DEVICE_NUMA_CONFIG_NUMA_NODE
The GPU is a NUMA node, CU_DEVICE_ATTRIBUTE_NUMA_ID contains its NUMA ID

enum CUdevice_P2PAttribute
P2P Attributes

                                 Values



CU_DEVICE_P2P_ATTRIBUTE_PERFORMANCE_RANK = 0x01
A relative value indicating the performance of the link between two devices
CU_DEVICE_P2P_ATTRIBUTE_ACCESS_SUPPORTED = 0x02
P2P Access is enable
CU_DEVICE_P2P_ATTRIBUTE_NATIVE_ATOMIC_SUPPORTED = 0x03
All CUDA-valid atomic operation over the link are supported
CU_DEVICE_P2P_ATTRIBUTE_ACCESS_ACCESS_SUPPORTED = 0x04

Deprecated
use CU_DEVICE_P2P_ATTRIBUTE_CUDA_ARRAY_ACCESS_SUPPORTED instead

CU_DEVICE_P2P_ATTRIBUTE_CUDA_ARRAY_ACCESS_SUPPORTED = 0x04
Accessing CUDA arrays over the link supported
CU_DEVICE_P2P_ATTRIBUTE_ONLY_PARTIAL_NATIVE_ATOMIC_SUPPORTED = 0x05
Only some CUDA-valid atomic operations over the link are supported.

enum CUdevice_attribute
Device properties

                                 Values



CU_DEVICE_ATTRIBUTE_MAX_THREADS_PER_BLOCK = 1
Maximum number of threads per block
CU_DEVICE_ATTRIBUTE_MAX_BLOCK_DIM_X = 2
Maximum block dimension X
CU_DEVICE_ATTRIBUTE_MAX_BLOCK_DIM_Y = 3
Maximum block dimension Y
CU_DEVICE_ATTRIBUTE_MAX_BLOCK_DIM_Z = 4
Maximum block dimension Z
CU_DEVICE_ATTRIBUTE_MAX_GRID_DIM_X = 5
Maximum grid dimension X
CU_DEVICE_ATTRIBUTE_MAX_GRID_DIM_Y = 6
Maximum grid dimension Y
CU_DEVICE_ATTRIBUTE_MAX_GRID_DIM_Z = 7
Maximum grid dimension Z
CU_DEVICE_ATTRIBUTE_MAX_SHARED_MEMORY_PER_BLOCK = 8
Maximum shared memory available per block in bytes
CU_DEVICE_ATTRIBUTE_SHARED_MEMORY_PER_BLOCK = 8
Deprecated, use CU_DEVICE_ATTRIBUTE_MAX_SHARED_MEMORY_PER_BLOCK
CU_DEVICE_ATTRIBUTE_TOTAL_CONSTANT_MEMORY = 9
Memory available on device for __constant__ variables in a CUDA C kernel in bytes
CU_DEVICE_ATTRIBUTE_WARP_SIZE = 10
Warp size in threads
CU_DEVICE_ATTRIBUTE_MAX_PITCH = 11
Maximum pitch in bytes allowed by memory copies
CU_DEVICE_ATTRIBUTE_MAX_REGISTERS_PER_BLOCK = 12
Maximum number of 32-bit registers available per block
CU_DEVICE_ATTRIBUTE_REGISTERS_PER_BLOCK = 12
Deprecated, use CU_DEVICE_ATTRIBUTE_MAX_REGISTERS_PER_BLOCK
CU_DEVICE_ATTRIBUTE_CLOCK_RATE = 13
Typical clock frequency in kilohertz
CU_DEVICE_ATTRIBUTE_TEXTURE_ALIGNMENT = 14
Alignment requirement for textures
CU_DEVICE_ATTRIBUTE_GPU_OVERLAP = 15
Device can possibly copy memory and execute a kernel concurrently. Deprecated. Use instead CU_DEVICE_ATTRIBUTE_ASYNC_ENGINE_COUNT.


CU_DEVICE_ATTRIBUTE_MULTIPROCESSOR_COUNT = 16
Number of multiprocessors on device
CU_DEVICE_ATTRIBUTE_KERNEL_EXEC_TIMEOUT = 17
Specifies whether there is a run time limit on kernels
CU_DEVICE_ATTRIBUTE_INTEGRATED = 18
Device is integrated with host memory
CU_DEVICE_ATTRIBUTE_CAN_MAP_HOST_MEMORY = 19
Device can map host memory into CUDA address space
CU_DEVICE_ATTRIBUTE_COMPUTE_MODE = 20
Compute mode (See CUcomputemode for details)

CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE1D_WIDTH = 21
Maximum 1D texture width
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_WIDTH = 22
Maximum 2D texture width
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_HEIGHT = 23
Maximum 2D texture height
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE3D_WIDTH = 24
Maximum 3D texture width
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE3D_HEIGHT = 25
Maximum 3D texture height
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE3D_DEPTH = 26
Maximum 3D texture depth
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_LAYERED_WIDTH = 27
Maximum 2D layered texture width
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_LAYERED_HEIGHT = 28
Maximum 2D layered texture height
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_LAYERED_LAYERS = 29
Maximum layers in a 2D layered texture
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_ARRAY_WIDTH = 27
Deprecated, use CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_LAYERED_WIDTH
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_ARRAY_HEIGHT = 28
Deprecated, use CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_LAYERED_HEIGHT
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_ARRAY_NUMSLICES = 29
Deprecated, use CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_LAYERED_LAYERS
CU_DEVICE_ATTRIBUTE_SURFACE_ALIGNMENT = 30
Alignment requirement for surfaces
CU_DEVICE_ATTRIBUTE_CONCURRENT_KERNELS = 31
Device can possibly execute multiple kernels concurrently
CU_DEVICE_ATTRIBUTE_ECC_ENABLED = 32
Device has ECC support enabled
CU_DEVICE_ATTRIBUTE_PCI_BUS_ID = 33
PCI bus ID of the device
CU_DEVICE_ATTRIBUTE_PCI_DEVICE_ID = 34
PCI device ID of the device
CU_DEVICE_ATTRIBUTE_TCC_DRIVER = 35
Device is using TCC driver model
CU_DEVICE_ATTRIBUTE_MEMORY_CLOCK_RATE = 36
Peak memory clock frequency in kilohertz
CU_DEVICE_ATTRIBUTE_GLOBAL_MEMORY_BUS_WIDTH = 37
Global memory bus width in bits
CU_DEVICE_ATTRIBUTE_L2_CACHE_SIZE = 38
Size of L2 cache in bytes
CU_DEVICE_ATTRIBUTE_MAX_THREADS_PER_MULTIPROCESSOR = 39
Maximum resident threads per multiprocessor
CU_DEVICE_ATTRIBUTE_ASYNC_ENGINE_COUNT = 40
Number of asynchronous engines
CU_DEVICE_ATTRIBUTE_UNIFIED_ADDRESSING = 41
Device shares a unified address space with the host
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE1D_LAYERED_WIDTH = 42
Maximum 1D layered texture width
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE1D_LAYERED_LAYERS = 43
Maximum layers in a 1D layered texture
CU_DEVICE_ATTRIBUTE_CAN_TEX2D_GATHER = 44
Deprecated, do not use.
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_GATHER_WIDTH = 45
Maximum 2D texture width if CUDA_ARRAY3D_TEXTURE_GATHER is set
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_GATHER_HEIGHT = 46
Maximum 2D texture height if CUDA_ARRAY3D_TEXTURE_GATHER is set
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE3D_WIDTH_ALTERNATE = 47
Alternate maximum 3D texture width
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE3D_HEIGHT_ALTERNATE = 48
Alternate maximum 3D texture height
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE3D_DEPTH_ALTERNATE = 49
Alternate maximum 3D texture depth
CU_DEVICE_ATTRIBUTE_PCI_DOMAIN_ID = 50
PCI domain ID of the device
CU_DEVICE_ATTRIBUTE_TEXTURE_PITCH_ALIGNMENT = 51
Pitch alignment requirement for textures
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURECUBEMAP_WIDTH = 52
Maximum cubemap texture width/height
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURECUBEMAP_LAYERED_WIDTH = 53
Maximum cubemap layered texture width/height
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURECUBEMAP_LAYERED_LAYERS = 54
Maximum layers in a cubemap layered texture
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACE1D_WIDTH = 55
Maximum 1D surface width
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACE2D_WIDTH = 56
Maximum 2D surface width
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACE2D_HEIGHT = 57
Maximum 2D surface height
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACE3D_WIDTH = 58
Maximum 3D surface width
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACE3D_HEIGHT = 59
Maximum 3D surface height
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACE3D_DEPTH = 60
Maximum 3D surface depth
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACE1D_LAYERED_WIDTH = 61
Maximum 1D layered surface width
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACE1D_LAYERED_LAYERS = 62
Maximum layers in a 1D layered surface
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACE2D_LAYERED_WIDTH = 63
Maximum 2D layered surface width
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACE2D_LAYERED_HEIGHT = 64
Maximum 2D layered surface height
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACE2D_LAYERED_LAYERS = 65
Maximum layers in a 2D layered surface
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACECUBEMAP_WIDTH = 66
Maximum cubemap surface width
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACECUBEMAP_LAYERED_WIDTH = 67
Maximum cubemap layered surface width
CU_DEVICE_ATTRIBUTE_MAXIMUM_SURFACECUBEMAP_LAYERED_LAYERS = 68
Maximum layers in a cubemap layered surface
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE1D_LINEAR_WIDTH = 69
Deprecated, do not use. Use cudaDeviceGetTexture1DLinearMaxWidth() or cuDeviceGetTexture1DLinearMaxWidth() instead.

CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_LINEAR_WIDTH = 70
Maximum 2D linear texture width
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_LINEAR_HEIGHT = 71
Maximum 2D linear texture height
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_LINEAR_PITCH = 72
Maximum 2D linear texture pitch in bytes
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_MIPMAPPED_WIDTH = 73
Maximum mipmapped 2D texture width
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE2D_MIPMAPPED_HEIGHT = 74
Maximum mipmapped 2D texture height
CU_DEVICE_ATTRIBUTE_COMPUTE_CAPABILITY_MAJOR = 75
Major compute capability version number
CU_DEVICE_ATTRIBUTE_COMPUTE_CAPABILITY_MINOR = 76
Minor compute capability version number
CU_DEVICE_ATTRIBUTE_MAXIMUM_TEXTURE1D_MIPMAPPED_WIDTH = 77
Maximum mipmapped 1D texture width
CU_DEVICE_ATTRIBUTE_STREAM_PRIORITIES_SUPPORTED = 78
Device supports stream priorities
CU_DEVICE_ATTRIBUTE_GLOBAL_L1_CACHE_SUPPORTED = 79
Device supports caching globals in L1
CU_DEVICE_ATTRIBUTE_LOCAL_L1_CACHE_SUPPORTED = 80
Device supports caching locals in L1
CU_DEVICE_ATTRIBUTE_MAX_SHARED_MEMORY_PER_MULTIPROCESSOR = 81
Maximum shared memory available per multiprocessor in bytes
CU_DEVICE_ATTRIBUTE_MAX_REGISTERS_PER_MULTIPROCESSOR = 82
Maximum number of 32-bit registers available per multiprocessor
CU_DEVICE_ATTRIBUTE_MANAGED_MEMORY = 83
Device can allocate managed memory on this system
CU_DEVICE_ATTRIBUTE_MULTI_GPU_BOARD = 84
Device is on a multi-GPU board
CU_DEVICE_ATTRIBUTE_MULTI_GPU_BOARD_GROUP_ID = 85
Unique id for a group of devices on the same multi-GPU board
CU_DEVICE_ATTRIBUTE_HOST_NATIVE_ATOMIC_SUPPORTED = 86
Link between the device and the host supports all native atomic operations
CU_DEVICE_ATTRIBUTE_SINGLE_TO_DOUBLE_PRECISION_PERF_RATIO = 87
Ratio of single precision performance (in floating-point operations per second) to double precision performance
CU_DEVICE_ATTRIBUTE_PAGEABLE_MEMORY_ACCESS = 88
Device supports coherently accessing pageable memory without calling cudaHostRegister on it
CU_DEVICE_ATTRIBUTE_CONCURRENT_MANAGED_ACCESS = 89
Device can coherently access managed memory concurrently with the CPU
CU_DEVICE_ATTRIBUTE_COMPUTE_PREEMPTION_SUPPORTED = 90
Device supports compute preemption.
CU_DEVICE_ATTRIBUTE_CAN_USE_HOST_POINTER_FOR_REGISTERED_MEM = 91
Device can access host registered memory at the same virtual address as the CPU
CU_DEVICE_ATTRIBUTE_CAN_USE_STREAM_MEM_OPS_V1 = 92
Deprecated, along with v1 MemOps API, cuStreamBatchMemOp and related APIs are supported.

CU_DEVICE_ATTRIBUTE_CAN_USE_64_BIT_STREAM_MEM_OPS_V1 = 93
Deprecated, along with v1 MemOps API, 64-bit operations are supported in cuStreamBatchMemOp and related APIs.

CU_DEVICE_ATTRIBUTE_CAN_USE_STREAM_WAIT_VALUE_NOR_V1 = 94
Deprecated, along with v1 MemOps API, CU_STREAM_WAIT_VALUE_NOR is supported.

CU_DEVICE_ATTRIBUTE_COOPERATIVE_LAUNCH = 95
Device supports launching cooperative kernels via cuLaunchCooperativeKernel

CU_DEVICE_ATTRIBUTE_COOPERATIVE_MULTI_DEVICE_LAUNCH = 96
Deprecated, cuLaunchCooperativeKernelMultiDevice is deprecated.

CU_DEVICE_ATTRIBUTE_MAX_SHARED_MEMORY_PER_BLOCK_OPTIN = 97
Maximum optin shared memory per block
CU_DEVICE_ATTRIBUTE_CAN_FLUSH_REMOTE_WRITES = 98
The CU_STREAM_WAIT_VALUE_FLUSH flag and the CU_STREAM_MEM_OP_FLUSH_REMOTE_WRITES MemOp are supported on the device. See Stream Memory Operations for additional details.

CU_DEVICE_ATTRIBUTE_HOST_REGISTER_SUPPORTED = 99
Device supports host memory registration via cudaHostRegister.

CU_DEVICE_ATTRIBUTE_PAGEABLE_MEMORY_ACCESS_USES_HOST_PAGE_TABLES = 100
Device accesses pageable memory via the host's page tables.
CU_DEVICE_ATTRIBUTE_DIRECT_MANAGED_MEM_ACCESS_FROM_HOST = 101
The host can directly access managed memory on the device without migration.
CU_DEVICE_ATTRIBUTE_VIRTUAL_ADDRESS_MANAGEMENT_SUPPORTED = 102
Deprecated, Use CU_DEVICE_ATTRIBUTE_VIRTUAL_MEMORY_MANAGEMENT_SUPPORTED
CU_DEVICE_ATTRIBUTE_VIRTUAL_MEMORY_MANAGEMENT_SUPPORTED = 102
Device supports virtual memory management APIs like cuMemAddressReserve, cuMemCreate, cuMemMap and related APIs

CU_DEVICE_ATTRIBUTE_HANDLE_TYPE_POSIX_FILE_DESCRIPTOR_SUPPORTED = 103
Device supports exporting memory to a posix file descriptor with cuMemExportToShareableHandle, if requested via cuMemCreate

CU_DEVICE_ATTRIBUTE_HANDLE_TYPE_WIN32_HANDLE_SUPPORTED = 104
Device supports exporting memory to a Win32 NT handle with cuMemExportToShareableHandle, if requested via cuMemCreate

CU_DEVICE_ATTRIBUTE_HANDLE_TYPE_WIN32_KMT_HANDLE_SUPPORTED = 105
Device supports exporting memory to a Win32 KMT handle with cuMemExportToShareableHandle, if requested via cuMemCreate

CU_DEVICE_ATTRIBUTE_MAX_BLOCKS_PER_MULTIPROCESSOR = 106
Maximum number of blocks per multiprocessor
CU_DEVICE_ATTRIBUTE_GENERIC_COMPRESSION_SUPPORTED = 107
Device supports compression of memory
CU_DEVICE_ATTRIBUTE_MAX_PERSISTING_L2_CACHE_SIZE = 108
Maximum L2 persisting lines capacity setting in bytes.
CU_DEVICE_ATTRIBUTE_MAX_ACCESS_POLICY_WINDOW_SIZE = 109
Maximum value of CUaccessPolicyWindow::num_bytes.

CU_DEVICE_ATTRIBUTE_GPU_DIRECT_RDMA_WITH_CUDA_VMM_SUPPORTED = 110
Device supports specifying the GPUDirect RDMA flag with cuMemCreate

CU_DEVICE_ATTRIBUTE_RESERVED_SHARED_MEMORY_PER_BLOCK = 111
Shared memory reserved by CUDA driver per block in bytes
CU_DEVICE_ATTRIBUTE_SPARSE_CUDA_ARRAY_SUPPORTED = 112
Device supports sparse CUDA arrays and sparse CUDA mipmapped arrays
CU_DEVICE_ATTRIBUTE_READ_ONLY_HOST_REGISTER_SUPPORTED = 113
Device supports using the cuMemHostRegister flag CU_MEMHOSTERGISTER_READ_ONLY to register memory that must be mapped as read-only to the GPU

CU_DEVICE_ATTRIBUTE_TIMELINE_SEMAPHORE_INTEROP_SUPPORTED = 114
External timeline semaphore interop is supported on the device
CU_DEVICE_ATTRIBUTE_MEMORY_POOLS_SUPPORTED = 115
Device supports using the cuMemAllocAsync and cuMemPool family of APIs

CU_DEVICE_ATTRIBUTE_GPU_DIRECT_RDMA_SUPPORTED = 116
Device supports GPUDirect RDMA APIs, like nvidia_p2p_get_pages (see https://docs.nvidia.com/cuda/gpudirect-rdma for more information)

CU_DEVICE_ATTRIBUTE_GPU_DIRECT_RDMA_FLUSH_WRITES_OPTIONS = 117
The returned attribute shall be interpreted as a bitmask, where the individual bits are described by the CUflushGPUDirectRDMAWritesOptions enum

CU_DEVICE_ATTRIBUTE_GPU_DIRECT_RDMA_WRITES_ORDERING = 118
GPUDirect RDMA writes to the device do not need to be flushed for consumers within the scope indicated by the returned attribute.
                                    See CUGPUDirectRDMAWritesOrdering for the numerical values returned here.

CU_DEVICE_ATTRIBUTE_MEMPOOL_SUPPORTED_HANDLE_TYPES = 119
Handle types supported with mempool based IPC
CU_DEVICE_ATTRIBUTE_CLUSTER_LAUNCH = 120
Indicates device supports cluster launch
CU_DEVICE_ATTRIBUTE_DEFERRED_MAPPING_CUDA_ARRAY_SUPPORTED = 121
Device supports deferred mapping CUDA arrays and CUDA mipmapped arrays
CU_DEVICE_ATTRIBUTE_CAN_USE_64_BIT_STREAM_MEM_OPS = 122
64-bit operations are supported in cuStreamBatchMemOp and related MemOp APIs.

CU_DEVICE_ATTRIBUTE_CAN_USE_STREAM_WAIT_VALUE_NOR = 123

CU_STREAM_WAIT_VALUE_NOR is supported by MemOp APIs.

CU_DEVICE_ATTRIBUTE_DMA_BUF_SUPPORTED = 124
Device supports buffer sharing with dma_buf mechanism.
CU_DEVICE_ATTRIBUTE_IPC_EVENT_SUPPORTED = 125
Device supports IPC Events.
CU_DEVICE_ATTRIBUTE_MEM_SYNC_DOMAIN_COUNT = 126
Number of memory domains the device supports.
CU_DEVICE_ATTRIBUTE_TENSOR_MAP_ACCESS_SUPPORTED = 127
Device supports accessing memory using Tensor Map.
CU_DEVICE_ATTRIBUTE_HANDLE_TYPE_FABRIC_SUPPORTED = 128
Device supports exporting memory to a fabric handle with cuMemExportToShareableHandle() or requested with cuMemCreate()

CU_DEVICE_ATTRIBUTE_UNIFIED_FUNCTION_POINTERS = 129
Device supports unified function pointers.
CU_DEVICE_ATTRIBUTE_NUMA_CONFIG = 130
NUMA configuration of a device: value is of type CUdeviceNumaConfig enum

CU_DEVICE_ATTRIBUTE_NUMA_ID = 131
NUMA node ID of the GPU memory
CU_DEVICE_ATTRIBUTE_MULTICAST_SUPPORTED = 132
Device supports switch multicast and reduction operations.
CU_DEVICE_ATTRIBUTE_MPS_ENABLED = 133
Indicates if contexts created on this device will be shared via MPS
CU_DEVICE_ATTRIBUTE_HOST_NUMA_ID = 134
NUMA ID of the host node closest to the device. Returns -1 when system does not support NUMA.
CU_DEVICE_ATTRIBUTE_D3D12_CIG_SUPPORTED = 135
Device supports CIG with D3D12.
CU_DEVICE_ATTRIBUTE_MEM_DECOMPRESS_ALGORITHM_MASK = 136
The returned valued shall be interpreted as a bitmask, where the individual bits are described by the CUmemDecompressAlgorithm enum.

CU_DEVICE_ATTRIBUTE_MEM_DECOMPRESS_MAXIMUM_LENGTH = 137
The returned valued is the maximum length in bytes of a single decompress operation that is allowed.
CU_DEVICE_ATTRIBUTE_VULKAN_CIG_SUPPORTED = 138
Device supports CIG with Vulkan.
CU_DEVICE_ATTRIBUTE_GPU_PCI_DEVICE_ID = 139
The combined 16-bit PCI device ID and 16-bit PCI vendor ID.
CU_DEVICE_ATTRIBUTE_GPU_PCI_SUBSYSTEM_ID = 140
The combined 16-bit PCI subsystem ID and 16-bit PCI subsystem vendor ID.
CU_DEVICE_ATTRIBUTE_HOST_NUMA_VIRTUAL_MEMORY_MANAGEMENT_SUPPORTED = 141
Device supports HOST_NUMA location with the virtual memory management APIs like cuMemCreate, cuMemMap and related APIs

CU_DEVICE_ATTRIBUTE_HOST_NUMA_MEMORY_POOLS_SUPPORTED = 142
Device supports HOST_NUMA location with the cuMemAllocAsync and cuMemPool family of APIs

CU_DEVICE_ATTRIBUTE_HOST_NUMA_MULTINODE_IPC_SUPPORTED = 143
Device supports HOST_NUMA location IPC between nodes in a multi-node system.
CU_DEVICE_ATTRIBUTE_HOST_MEMORY_POOLS_SUPPORTED = 144
Device suports HOST location with the cuMemAllocAsync and cuMemPool family of APIs

CU_DEVICE_ATTRIBUTE_HOST_VIRTUAL_MEMORY_MANAGEMENT_SUPPORTED = 145
Device supports HOST location with the virtual memory management APIs like cuMemCreate, cuMemMap and related APIs

CU_DEVICE_ATTRIBUTE_HOST_ALLOC_DMA_BUF_SUPPORTED = 146
Device supports page-locked host memory buffer sharing with dma_buf mechanism.
CU_DEVICE_ATTRIBUTE_ONLY_PARTIAL_HOST_NATIVE_ATOMIC_SUPPORTED = 147
Link between the device and the host supports only some native atomic operations
CU_DEVICE_ATTRIBUTE_ATOMIC_REDUCTION_SUPPORTED = 148
Device supports atomic reduction operations in stream batch memory operations
CU_DEVICE_ATTRIBUTE_MAX

enum CUdriverProcAddressQueryResult
Flags to indicate search status. For more details see cuGetProcAddress

                                 Values



CU_GET_PROC_ADDRESS_SUCCESS = 0
Symbol was succesfully found
CU_GET_PROC_ADDRESS_SYMBOL_NOT_FOUND = 1
Symbol was not found in search
CU_GET_PROC_ADDRESS_VERSION_NOT_SUFFICIENT = 2
Symbol was found but version supplied was not sufficient

enum CUdriverProcAddress_flags
Flags to specify search options. For more details see cuGetProcAddress

                                 Values



CU_GET_PROC_ADDRESS_DEFAULT = 0
Default search mode for driver symbols.
CU_GET_PROC_ADDRESS_LEGACY_STREAM = 1<<0
Search for legacy versions of driver symbols.
CU_GET_PROC_ADDRESS_PER_THREAD_DEFAULT_STREAM = 1<<1
Search for per-thread versions of driver symbols.

enum CUeglColorFormat
CUDA EGL Color Format - The different planar and multiplanar formats currently supported for CUDA_EGL interops. Three channel
                                 formats are currently not supported for CU_EGL_FRAME_TYPE_ARRAY

                                 Values



CU_EGL_COLOR_FORMAT_YUV420_PLANAR = 0x00
Y, U, V in three surfaces, each in a separate surface, U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_YUV420_SEMIPLANAR = 0x01
Y, UV in two surfaces (UV as one surface) with VU byte ordering, width, height ratio same as YUV420Planar.
CU_EGL_COLOR_FORMAT_YUV422_PLANAR = 0x02
Y, U, V each in a separate surface, U/V width = 1/2 Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_YUV422_SEMIPLANAR = 0x03
Y, UV in two surfaces with VU byte ordering, width, height ratio same as YUV422Planar.
CU_EGL_COLOR_FORMAT_RGB = 0x04
R/G/B three channels in one surface with BGR byte ordering. Only pitch linear format supported.
CU_EGL_COLOR_FORMAT_BGR = 0x05
R/G/B three channels in one surface with RGB byte ordering. Only pitch linear format supported.
CU_EGL_COLOR_FORMAT_ARGB = 0x06
R/G/B/A four channels in one surface with BGRA byte ordering.
CU_EGL_COLOR_FORMAT_RGBA = 0x07
R/G/B/A four channels in one surface with ABGR byte ordering.
CU_EGL_COLOR_FORMAT_L = 0x08
single luminance channel in one surface.
CU_EGL_COLOR_FORMAT_R = 0x09
single color channel in one surface.
CU_EGL_COLOR_FORMAT_YUV444_PLANAR = 0x0A
Y, U, V in three surfaces, each in a separate surface, U/V width = Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_YUV444_SEMIPLANAR = 0x0B
Y, UV in two surfaces (UV as one surface) with VU byte ordering, width, height ratio same as YUV444Planar.
CU_EGL_COLOR_FORMAT_YUYV_422 = 0x0C
Y, U, V in one surface, interleaved as UYVY in one channel.
CU_EGL_COLOR_FORMAT_UYVY_422 = 0x0D
Y, U, V in one surface, interleaved as YUYV in one channel.
CU_EGL_COLOR_FORMAT_ABGR = 0x0E
R/G/B/A four channels in one surface with RGBA byte ordering.
CU_EGL_COLOR_FORMAT_BGRA = 0x0F
R/G/B/A four channels in one surface with ARGB byte ordering.
CU_EGL_COLOR_FORMAT_A = 0x10
Alpha color format - one channel in one surface.
CU_EGL_COLOR_FORMAT_RG = 0x11
R/G color format - two channels in one surface with GR byte ordering
CU_EGL_COLOR_FORMAT_AYUV = 0x12
Y, U, V, A four channels in one surface, interleaved as VUYA.
CU_EGL_COLOR_FORMAT_YVU444_SEMIPLANAR = 0x13
Y, VU in two surfaces (VU as one surface) with UV byte ordering, U/V width = Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_YVU422_SEMIPLANAR = 0x14
Y, VU in two surfaces (VU as one surface) with UV byte ordering, U/V width = 1/2 Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_YVU420_SEMIPLANAR = 0x15
Y, VU in two surfaces (VU as one surface) with UV byte ordering, U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_Y10V10U10_444_SEMIPLANAR = 0x16
Y10, V10U10 in two surfaces (VU as one surface) with UV byte ordering, U/V width = Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_Y10V10U10_420_SEMIPLANAR = 0x17
Y10, V10U10 in two surfaces (VU as one surface) with UV byte ordering, U/V width = 1/2 Y width, U/V height = 1/2 Y height.


CU_EGL_COLOR_FORMAT_Y12V12U12_444_SEMIPLANAR = 0x18
Y12, V12U12 in two surfaces (VU as one surface) with UV byte ordering, U/V width = Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_Y12V12U12_420_SEMIPLANAR = 0x19
Y12, V12U12 in two surfaces (VU as one surface) with UV byte ordering, U/V width = 1/2 Y width, U/V height = 1/2 Y height.


CU_EGL_COLOR_FORMAT_VYUY_ER = 0x1A
Extended Range Y, U, V in one surface, interleaved as YVYU in one channel.
CU_EGL_COLOR_FORMAT_UYVY_ER = 0x1B
Extended Range Y, U, V in one surface, interleaved as YUYV in one channel.
CU_EGL_COLOR_FORMAT_YUYV_ER = 0x1C
Extended Range Y, U, V in one surface, interleaved as UYVY in one channel.
CU_EGL_COLOR_FORMAT_YVYU_ER = 0x1D
Extended Range Y, U, V in one surface, interleaved as VYUY in one channel.
CU_EGL_COLOR_FORMAT_YUV_ER = 0x1E
Extended Range Y, U, V three channels in one surface, interleaved as VUY. Only pitch linear format supported.
CU_EGL_COLOR_FORMAT_YUVA_ER = 0x1F
Extended Range Y, U, V, A four channels in one surface, interleaved as AVUY.
CU_EGL_COLOR_FORMAT_AYUV_ER = 0x20
Extended Range Y, U, V, A four channels in one surface, interleaved as VUYA.
CU_EGL_COLOR_FORMAT_YUV444_PLANAR_ER = 0x21
Extended Range Y, U, V in three surfaces, U/V width = Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_YUV422_PLANAR_ER = 0x22
Extended Range Y, U, V in three surfaces, U/V width = 1/2 Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_YUV420_PLANAR_ER = 0x23
Extended Range Y, U, V in three surfaces, U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_YUV444_SEMIPLANAR_ER = 0x24
Extended Range Y, UV in two surfaces (UV as one surface) with VU byte ordering, U/V width = Y width, U/V height = Y height.


CU_EGL_COLOR_FORMAT_YUV422_SEMIPLANAR_ER = 0x25
Extended Range Y, UV in two surfaces (UV as one surface) with VU byte ordering, U/V width = 1/2 Y width, U/V height = Y height.


CU_EGL_COLOR_FORMAT_YUV420_SEMIPLANAR_ER = 0x26
Extended Range Y, UV in two surfaces (UV as one surface) with VU byte ordering, U/V width = 1/2 Y width, U/V height = 1/2
                                    Y height.

CU_EGL_COLOR_FORMAT_YVU444_PLANAR_ER = 0x27
Extended Range Y, V, U in three surfaces, U/V width = Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_YVU422_PLANAR_ER = 0x28
Extended Range Y, V, U in three surfaces, U/V width = 1/2 Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_YVU420_PLANAR_ER = 0x29
Extended Range Y, V, U in three surfaces, U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_YVU444_SEMIPLANAR_ER = 0x2A
Extended Range Y, VU in two surfaces (VU as one surface) with UV byte ordering, U/V width = Y width, U/V height = Y height.


CU_EGL_COLOR_FORMAT_YVU422_SEMIPLANAR_ER = 0x2B
Extended Range Y, VU in two surfaces (VU as one surface) with UV byte ordering, U/V width = 1/2 Y width, U/V height = Y height.


CU_EGL_COLOR_FORMAT_YVU420_SEMIPLANAR_ER = 0x2C
Extended Range Y, VU in two surfaces (VU as one surface) with UV byte ordering, U/V width = 1/2 Y width, U/V height = 1/2
                                    Y height.

CU_EGL_COLOR_FORMAT_BAYER_RGGB = 0x2D
Bayer format - one channel in one surface with interleaved RGGB ordering.
CU_EGL_COLOR_FORMAT_BAYER_BGGR = 0x2E
Bayer format - one channel in one surface with interleaved BGGR ordering.
CU_EGL_COLOR_FORMAT_BAYER_GRBG = 0x2F
Bayer format - one channel in one surface with interleaved GRBG ordering.
CU_EGL_COLOR_FORMAT_BAYER_GBRG = 0x30
Bayer format - one channel in one surface with interleaved GBRG ordering.
CU_EGL_COLOR_FORMAT_BAYER10_RGGB = 0x31
Bayer10 format - one channel in one surface with interleaved RGGB ordering. Out of 16 bits, 10 bits used 6 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER10_BGGR = 0x32
Bayer10 format - one channel in one surface with interleaved BGGR ordering. Out of 16 bits, 10 bits used 6 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER10_GRBG = 0x33
Bayer10 format - one channel in one surface with interleaved GRBG ordering. Out of 16 bits, 10 bits used 6 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER10_GBRG = 0x34
Bayer10 format - one channel in one surface with interleaved GBRG ordering. Out of 16 bits, 10 bits used 6 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER12_RGGB = 0x35
Bayer12 format - one channel in one surface with interleaved RGGB ordering. Out of 16 bits, 12 bits used 4 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER12_BGGR = 0x36
Bayer12 format - one channel in one surface with interleaved BGGR ordering. Out of 16 bits, 12 bits used 4 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER12_GRBG = 0x37
Bayer12 format - one channel in one surface with interleaved GRBG ordering. Out of 16 bits, 12 bits used 4 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER12_GBRG = 0x38
Bayer12 format - one channel in one surface with interleaved GBRG ordering. Out of 16 bits, 12 bits used 4 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER14_RGGB = 0x39
Bayer14 format - one channel in one surface with interleaved RGGB ordering. Out of 16 bits, 14 bits used 2 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER14_BGGR = 0x3A
Bayer14 format - one channel in one surface with interleaved BGGR ordering. Out of 16 bits, 14 bits used 2 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER14_GRBG = 0x3B
Bayer14 format - one channel in one surface with interleaved GRBG ordering. Out of 16 bits, 14 bits used 2 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER14_GBRG = 0x3C
Bayer14 format - one channel in one surface with interleaved GBRG ordering. Out of 16 bits, 14 bits used 2 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER20_RGGB = 0x3D
Bayer20 format - one channel in one surface with interleaved RGGB ordering. Out of 32 bits, 20 bits used 12 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER20_BGGR = 0x3E
Bayer20 format - one channel in one surface with interleaved BGGR ordering. Out of 32 bits, 20 bits used 12 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER20_GRBG = 0x3F
Bayer20 format - one channel in one surface with interleaved GRBG ordering. Out of 32 bits, 20 bits used 12 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER20_GBRG = 0x40
Bayer20 format - one channel in one surface with interleaved GBRG ordering. Out of 32 bits, 20 bits used 12 bits No-op.
CU_EGL_COLOR_FORMAT_YVU444_PLANAR = 0x41
Y, V, U in three surfaces, each in a separate surface, U/V width = Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_YVU422_PLANAR = 0x42
Y, V, U in three surfaces, each in a separate surface, U/V width = 1/2 Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_YVU420_PLANAR = 0x43
Y, V, U in three surfaces, each in a separate surface, U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_BAYER_ISP_RGGB = 0x44
Nvidia proprietary Bayer ISP format - one channel in one surface with interleaved RGGB ordering and mapped to opaque integer
                                    datatype.

CU_EGL_COLOR_FORMAT_BAYER_ISP_BGGR = 0x45
Nvidia proprietary Bayer ISP format - one channel in one surface with interleaved BGGR ordering and mapped to opaque integer
                                    datatype.

CU_EGL_COLOR_FORMAT_BAYER_ISP_GRBG = 0x46
Nvidia proprietary Bayer ISP format - one channel in one surface with interleaved GRBG ordering and mapped to opaque integer
                                    datatype.

CU_EGL_COLOR_FORMAT_BAYER_ISP_GBRG = 0x47
Nvidia proprietary Bayer ISP format - one channel in one surface with interleaved GBRG ordering and mapped to opaque integer
                                    datatype.

CU_EGL_COLOR_FORMAT_BAYER_BCCR = 0x48
Bayer format - one channel in one surface with interleaved BCCR ordering.
CU_EGL_COLOR_FORMAT_BAYER_RCCB = 0x49
Bayer format - one channel in one surface with interleaved RCCB ordering.
CU_EGL_COLOR_FORMAT_BAYER_CRBC = 0x4A
Bayer format - one channel in one surface with interleaved CRBC ordering.
CU_EGL_COLOR_FORMAT_BAYER_CBRC = 0x4B
Bayer format - one channel in one surface with interleaved CBRC ordering.
CU_EGL_COLOR_FORMAT_BAYER10_CCCC = 0x4C
Bayer10 format - one channel in one surface with interleaved CCCC ordering. Out of 16 bits, 10 bits used 6 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER12_BCCR = 0x4D
Bayer12 format - one channel in one surface with interleaved BCCR ordering. Out of 16 bits, 12 bits used 4 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER12_RCCB = 0x4E
Bayer12 format - one channel in one surface with interleaved RCCB ordering. Out of 16 bits, 12 bits used 4 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER12_CRBC = 0x4F
Bayer12 format - one channel in one surface with interleaved CRBC ordering. Out of 16 bits, 12 bits used 4 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER12_CBRC = 0x50
Bayer12 format - one channel in one surface with interleaved CBRC ordering. Out of 16 bits, 12 bits used 4 bits No-op.
CU_EGL_COLOR_FORMAT_BAYER12_CCCC = 0x51
Bayer12 format - one channel in one surface with interleaved CCCC ordering. Out of 16 bits, 12 bits used 4 bits No-op.
CU_EGL_COLOR_FORMAT_Y = 0x52
Color format for single Y plane.
CU_EGL_COLOR_FORMAT_YUV420_SEMIPLANAR_2020 = 0x53
Y, UV in two surfaces (UV as one surface) U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_YVU420_SEMIPLANAR_2020 = 0x54
Y, VU in two surfaces (VU as one surface) U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_YUV420_PLANAR_2020 = 0x55
Y, U, V each in a separate surface, U/V width = 1/2 Y width, U/V height= 1/2 Y height.
CU_EGL_COLOR_FORMAT_YVU420_PLANAR_2020 = 0x56
Y, V, U each in a separate surface, U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_YUV420_SEMIPLANAR_709 = 0x57
Y, UV in two surfaces (UV as one surface) U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_YVU420_SEMIPLANAR_709 = 0x58
Y, VU in two surfaces (VU as one surface) U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_YUV420_PLANAR_709 = 0x59
Y, U, V each in a separate surface, U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_YVU420_PLANAR_709 = 0x5A
Y, V, U each in a separate surface, U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_Y10V10U10_420_SEMIPLANAR_709 = 0x5B
Y10, V10U10 in two surfaces (VU as one surface), U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_Y10V10U10_420_SEMIPLANAR_2020 = 0x5C
Y10, V10U10 in two surfaces (VU as one surface), U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_Y10V10U10_422_SEMIPLANAR_2020 = 0x5D
Y10, V10U10 in two surfaces(VU as one surface) U/V width = 1/2 Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_Y10V10U10_422_SEMIPLANAR = 0x5E
Y10, V10U10 in two surfaces(VU as one surface) U/V width = 1/2 Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_Y10V10U10_422_SEMIPLANAR_709 = 0x5F
Y10, V10U10 in two surfaces(VU as one surface) U/V width = 1/2 Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_Y_ER = 0x60
Extended Range Color format for single Y plane.
CU_EGL_COLOR_FORMAT_Y_709_ER = 0x61
Extended Range Color format for single Y plane.
CU_EGL_COLOR_FORMAT_Y10_ER = 0x62
Extended Range Color format for single Y10 plane.
CU_EGL_COLOR_FORMAT_Y10_709_ER = 0x63
Extended Range Color format for single Y10 plane.
CU_EGL_COLOR_FORMAT_Y12_ER = 0x64
Extended Range Color format for single Y12 plane.
CU_EGL_COLOR_FORMAT_Y12_709_ER = 0x65
Extended Range Color format for single Y12 plane.
CU_EGL_COLOR_FORMAT_YUVA = 0x66
Y, U, V, A four channels in one surface, interleaved as AVUY.
CU_EGL_COLOR_FORMAT_YUV = 0x67
Y, U, V three channels in one surface, interleaved as VUY. Only pitch linear format supported.
CU_EGL_COLOR_FORMAT_YVYU = 0x68
Y, U, V in one surface, interleaved as YVYU in one channel.
CU_EGL_COLOR_FORMAT_VYUY = 0x69
Y, U, V in one surface, interleaved as VYUY in one channel.
CU_EGL_COLOR_FORMAT_Y10V10U10_420_SEMIPLANAR_ER = 0x6A
Extended Range Y10, V10U10 in two surfaces(VU as one surface) U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_Y10V10U10_420_SEMIPLANAR_709_ER = 0x6B
Extended Range Y10, V10U10 in two surfaces(VU as one surface) U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_Y10V10U10_444_SEMIPLANAR_ER = 0x6C
Extended Range Y10, V10U10 in two surfaces (VU as one surface) U/V width = Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_Y10V10U10_444_SEMIPLANAR_709_ER = 0x6D
Extended Range Y10, V10U10 in two surfaces (VU as one surface) U/V width = Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_Y12V12U12_420_SEMIPLANAR_ER = 0x6E
Extended Range Y12, V12U12 in two surfaces (VU as one surface) U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_Y12V12U12_420_SEMIPLANAR_709_ER = 0x6F
Extended Range Y12, V12U12 in two surfaces (VU as one surface) U/V width = 1/2 Y width, U/V height = 1/2 Y height.
CU_EGL_COLOR_FORMAT_Y12V12U12_444_SEMIPLANAR_ER = 0x70
Extended Range Y12, V12U12 in two surfaces (VU as one surface) U/V width = Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_Y12V12U12_444_SEMIPLANAR_709_ER = 0x71
Extended Range Y12, V12U12 in two surfaces (VU as one surface) U/V width = Y width, U/V height = Y height.
CU_EGL_COLOR_FORMAT_UYVY_709 = 0x72
Y, U, V in one surface, interleaved as UYVY in one channel.
CU_EGL_COLOR_FORMAT_UYVY_709_ER = 0x73
Extended Range Y, U, V in one surface, interleaved as UYVY in one channel.
CU_EGL_COLOR_FORMAT_UYVY_2020 = 0x74
Y, U, V in one surface, interleaved as UYVY in one channel.
CU_EGL_COLOR_FORMAT_MAX

enum CUeglFrameType
CUDA EglFrame type - array or pointer

                                 Values



CU_EGL_FRAME_TYPE_ARRAY = 0
Frame type CUDA array
CU_EGL_FRAME_TYPE_PITCH = 1
Frame type pointer

enum CUeglResourceLocationFlags
Resource location flags- sysmem or vidmem
For CUDA context on iGPU, since video and system memory are equivalent - these flags will not have an effect on the execution.
For CUDA context on dGPU, applications can use the flag CUeglResourceLocationFlags to give a hint about the desired location.

CU_EGL_RESOURCE_LOCATION_SYSMEM - the frame data is made resident on the system memory to be accessed by CUDA.

CU_EGL_RESOURCE_LOCATION_VIDMEM - the frame data is made resident on the dedicated video memory to be accessed by CUDA.

There may be an additional latency due to new allocation and data migration, if the frame is produced on a different memory.



                                 Values



CU_EGL_RESOURCE_LOCATION_SYSMEM = 0x00
Resource location sysmem
CU_EGL_RESOURCE_LOCATION_VIDMEM = 0x01
Resource location vidmem

enum CUevent_flags
Event creation flags

                                 Values



CU_EVENT_DEFAULT = 0x0
Default event flag
CU_EVENT_BLOCKING_SYNC = 0x1
Event uses blocking synchronization
CU_EVENT_DISABLE_TIMING = 0x2
Event will not record timing data
CU_EVENT_INTERPROCESS = 0x4
Event is suitable for interprocess use. CU_EVENT_DISABLE_TIMING must be set

enum CUevent_record_flags
Event record flags

                                 Values



CU_EVENT_RECORD_DEFAULT = 0x0
Default event record flag
CU_EVENT_RECORD_EXTERNAL = 0x1
When using stream capture, create an event record node instead of the default behavior. This flag is invalid when used outside
                                    of capture.

enum CUevent_sched_flags
Event sched flags

                                 Values



CU_EVENT_SCHED_AUTO = 0x00
Automatic scheduling
CU_EVENT_SCHED_SPIN = 0x01
Set spin as default scheduling
CU_EVENT_SCHED_YIELD = 0x02
Set yield as default scheduling
CU_EVENT_SCHED_BLOCKING_SYNC = 0x04
Set blocking synchronization as default scheduling

enum CUevent_wait_flags
Event wait flags

                                 Values



CU_EVENT_WAIT_DEFAULT = 0x0
Default event wait flag
CU_EVENT_WAIT_EXTERNAL = 0x1
When using stream capture, create an event wait node instead of the default behavior. This flag is invalid when used outside
                                    of capture.

enum CUexecAffinityType
Execution Affinity Types

                                 Values



CU_EXEC_AFFINITY_TYPE_SM_COUNT = 0
Create a context with limited SMs.
CU_EXEC_AFFINITY_TYPE_MAX

enum CUexternalMemoryHandleType
External memory handle types

                                 Values



CU_EXTERNAL_MEMORY_HANDLE_TYPE_OPAQUE_FD = 1
Handle is an opaque file descriptor
CU_EXTERNAL_MEMORY_HANDLE_TYPE_OPAQUE_WIN32 = 2
Handle is an opaque shared NT handle
CU_EXTERNAL_MEMORY_HANDLE_TYPE_OPAQUE_WIN32_KMT = 3
Handle is an opaque, globally shared handle
CU_EXTERNAL_MEMORY_HANDLE_TYPE_D3D12_HEAP = 4
Handle is a D3D12 heap object
CU_EXTERNAL_MEMORY_HANDLE_TYPE_D3D12_RESOURCE = 5
Handle is a D3D12 committed resource
CU_EXTERNAL_MEMORY_HANDLE_TYPE_D3D11_RESOURCE = 6
Handle is a shared NT handle to a D3D11 resource
CU_EXTERNAL_MEMORY_HANDLE_TYPE_D3D11_RESOURCE_KMT = 7
Handle is a globally shared handle to a D3D11 resource
CU_EXTERNAL_MEMORY_HANDLE_TYPE_NVSCIBUF = 8
Handle is an NvSciBuf object
CU_EXTERNAL_MEMORY_HANDLE_TYPE_DMABUF_FD = 9
Handle is a dma_buf file descriptor

enum CUexternalSemaphoreHandleType
External semaphore handle types

                                 Values



CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_OPAQUE_FD = 1
Handle is an opaque file descriptor
CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_OPAQUE_WIN32 = 2
Handle is an opaque shared NT handle
CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_OPAQUE_WIN32_KMT = 3
Handle is an opaque, globally shared handle
CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_D3D12_FENCE = 4
Handle is a shared NT handle referencing a D3D12 fence object
CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_D3D11_FENCE = 5
Handle is a shared NT handle referencing a D3D11 fence object
CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_NVSCISYNC = 6
Opaque handle to NvSciSync Object
CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_D3D11_KEYED_MUTEX = 7
Handle is a shared NT handle referencing a D3D11 keyed mutex object
CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_D3D11_KEYED_MUTEX_KMT = 8
Handle is a globally shared handle referencing a D3D11 keyed mutex object
CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_TIMELINE_SEMAPHORE_FD = 9
Handle is an opaque file descriptor referencing a timeline semaphore
CU_EXTERNAL_SEMAPHORE_HANDLE_TYPE_TIMELINE_SEMAPHORE_WIN32 = 10
Handle is an opaque shared NT handle referencing a timeline semaphore

enum CUfilter_mode
Texture reference filtering modes

                                 Values



CU_TR_FILTER_MODE_POINT = 0
Point filter mode
CU_TR_FILTER_MODE_LINEAR = 1
Linear filter mode

enum CUflushGPUDirectRDMAWritesOptions
Bitmasks for CU_DEVICE_ATTRIBUTE_GPU_DIRECT_RDMA_FLUSH_WRITES_OPTIONS

                                 Values



CU_FLUSH_GPU_DIRECT_RDMA_WRITES_OPTION_HOST = 1<<0

cuFlushGPUDirectRDMAWrites() and its CUDA Runtime API counterpart are supported on the device.

CU_FLUSH_GPU_DIRECT_RDMA_WRITES_OPTION_MEMOPS = 1<<1
The CU_STREAM_WAIT_VALUE_FLUSH flag and the CU_STREAM_MEM_OP_FLUSH_REMOTE_WRITES MemOp are supported on the device.

enum CUflushGPUDirectRDMAWritesScope
The scopes for cuFlushGPUDirectRDMAWrites

                                 Values



CU_FLUSH_GPU_DIRECT_RDMA_WRITES_TO_OWNER = 100
Blocks until remote writes are visible to the CUDA device context owning the data.
CU_FLUSH_GPU_DIRECT_RDMA_WRITES_TO_ALL_DEVICES = 200
Blocks until remote writes are visible to all CUDA device contexts.

enum CUflushGPUDirectRDMAWritesTarget
The targets for cuFlushGPUDirectRDMAWrites

                                 Values



CU_FLUSH_GPU_DIRECT_RDMA_WRITES_TARGET_CURRENT_CTX = 0
Sets the target for cuFlushGPUDirectRDMAWrites() to the currently active CUDA device context.

enum CUfunc_cache
Function cache configurations

                                 Values



CU_FUNC_CACHE_PREFER_NONE = 0x00
no preference for shared memory or L1 (default)
CU_FUNC_CACHE_PREFER_SHARED = 0x01
prefer larger shared memory and smaller L1 cache
CU_FUNC_CACHE_PREFER_L1 = 0x02
prefer larger L1 cache and smaller shared memory
CU_FUNC_CACHE_PREFER_EQUAL = 0x03
prefer equal sized L1 cache and shared memory

enum CUfunction_attribute
Function properties

                                 Values



CU_FUNC_ATTRIBUTE_MAX_THREADS_PER_BLOCK = 0
The maximum number of threads per block, beyond which a launch of the function would fail. This number depends on both the
                                    function and the device on which the function is currently loaded.

CU_FUNC_ATTRIBUTE_SHARED_SIZE_BYTES = 1
The size in bytes of statically-allocated shared memory required by this function. This does not include dynamically-allocated
                                    shared memory requested by the user at runtime.

CU_FUNC_ATTRIBUTE_CONST_SIZE_BYTES = 2
The size in bytes of user-allocated constant memory required by this function.
CU_FUNC_ATTRIBUTE_LOCAL_SIZE_BYTES = 3
The size in bytes of local memory used by each thread of this function.
CU_FUNC_ATTRIBUTE_NUM_REGS = 4
The number of registers used by each thread of this function.
CU_FUNC_ATTRIBUTE_PTX_VERSION = 5
The PTX virtual architecture version for which the function was compiled. This value is the major PTX version * 10 + the minor
                                    PTX version, so a PTX version 1.3 function would return the value 13. Note that this may return the undefined value of 0 for
                                    cubins compiled prior to CUDA 3.0.

CU_FUNC_ATTRIBUTE_BINARY_VERSION = 6
The binary architecture version for which the function was compiled. This value is the major binary version * 10 + the minor
                                    binary version, so a binary version 1.3 function would return the value 13. Note that this will return a value of 10 for legacy
                                    cubins that do not have a properly-encoded binary architecture version.

CU_FUNC_ATTRIBUTE_CACHE_MODE_CA = 7
The attribute to indicate whether the function has been compiled with user specified option "-Xptxas --dlcm=ca" set .
CU_FUNC_ATTRIBUTE_MAX_DYNAMIC_SHARED_SIZE_BYTES = 8
The maximum size in bytes of dynamically-allocated shared memory that can be used by this function. If the user-specified
                                    dynamic shared memory size is larger than this value, the launch will fail. The default value of this attribute is CU_DEVICE_ATTRIBUTE_MAX_SHARED_MEMORY_PER_BLOCK - CU_FUNC_ATTRIBUTE_SHARED_SIZE_BYTES, except when CU_FUNC_ATTRIBUTE_SHARED_SIZE_BYTES is greater than CU_DEVICE_ATTRIBUTE_MAX_SHARED_MEMORY_PER_BLOCK, then the default value of this attribute is 0. The value can be increased to CU_DEVICE_ATTRIBUTE_MAX_SHARED_MEMORY_PER_BLOCK_OPTIN - CU_FUNC_ATTRIBUTE_SHARED_SIZE_BYTES. See cuFuncSetAttribute, cuKernelSetAttribute

CU_FUNC_ATTRIBUTE_PREFERRED_SHARED_MEMORY_CARVEOUT = 9
On devices where the L1 cache and shared memory use the same hardware resources, this sets the shared memory carveout preference,
                                    in percent of the total shared memory. Refer to CU_DEVICE_ATTRIBUTE_MAX_SHARED_MEMORY_PER_MULTIPROCESSOR. This is only a hint, and the driver can choose a different ratio if required to execute the function. See cuFuncSetAttribute, cuKernelSetAttribute

CU_FUNC_ATTRIBUTE_CLUSTER_SIZE_MUST_BE_SET = 10
If this attribute is set, the kernel must launch with a valid cluster size specified. See cuFuncSetAttribute, cuKernelSetAttribute

CU_FUNC_ATTRIBUTE_REQUIRED_CLUSTER_WIDTH = 11
The required cluster width in blocks. The values must either all be 0 or all be positive. The validity of the cluster dimensions
                                    is otherwise checked at launch time.If the value is set during compile time, it cannot be set at runtime. Setting it at runtime
                                    will return CUDA_ERROR_NOT_PERMITTED. See cuFuncSetAttribute, cuKernelSetAttribute

CU_FUNC_ATTRIBUTE_REQUIRED_CLUSTER_HEIGHT = 12
The required cluster height in blocks. The values must either all be 0 or all be positive. The validity of the cluster dimensions
                                    is otherwise checked at launch time.If the value is set during compile time, it cannot be set at runtime. Setting it at runtime
                                    should return CUDA_ERROR_NOT_PERMITTED. See cuFuncSetAttribute, cuKernelSetAttribute

CU_FUNC_ATTRIBUTE_REQUIRED_CLUSTER_DEPTH = 13
The required cluster depth in blocks. The values must either all be 0 or all be positive. The validity of the cluster dimensions
                                    is otherwise checked at launch time.If the value is set during compile time, it cannot be set at runtime. Setting it at runtime
                                    should return CUDA_ERROR_NOT_PERMITTED. See cuFuncSetAttribute, cuKernelSetAttribute

CU_FUNC_ATTRIBUTE_NON_PORTABLE_CLUSTER_SIZE_ALLOWED = 14
Whether the function can be launched with non-portable cluster size. 1 is allowed, 0 is disallowed. A non-portable cluster
                                    size may only function on the specific SKUs the program is tested on. The launch might fail if the program is run on a different
                                    hardware platform.CUDA API provides cudaOccupancyMaxActiveClusters to assist with checking whether the desired size can be
                                    launched on the current device.Portable Cluster SizeA portable cluster size is guaranteed to be functional on all compute
                                    capabilities higher than the target compute capability. The portable cluster size for sm_90 is 8 blocks per cluster. This
                                    value may increase for future compute capabilities.The specific hardware unit may support higher cluster sizes that’s not
                                    guaranteed to be portable. See cuFuncSetAttribute, cuKernelSetAttribute

CU_FUNC_ATTRIBUTE_CLUSTER_SCHEDULING_POLICY_PREFERENCE = 15
The block scheduling policy of a function. The value type is CUclusterSchedulingPolicy / cudaClusterSchedulingPolicy. See
                                    cuFuncSetAttribute, cuKernelSetAttribute

CU_FUNC_ATTRIBUTE_MAX

enum CUgraphChildGraphNodeOwnership
Child graph node ownership

                                 Values



CU_GRAPH_CHILD_GRAPH_OWNERSHIP_CLONE = 0
Default behavior for a child graph node. Child graph is cloned into the parent and memory allocation/free nodes can't be present
                                    in the child graph.

CU_GRAPH_CHILD_GRAPH_OWNERSHIP_MOVE = 1
The child graph is moved to the parent. The handle to the child graph is owned by the parent and will be destroyed when the
                                    parent is destroyed.The following restrictions apply to child graphs after they have been moved: Cannot be independently instantiated
                                    or destroyed; Cannot be added as a child graph of a separate parent graph; Cannot be used as an argument to cuGraphExecUpdate;
                                    Cannot have additional memory allocation or free nodes added.

enum CUgraphConditionalNodeType
Conditional node types

                                 Values



CU_GRAPH_COND_TYPE_IF = 0
Conditional 'if/else' Node. Body[0] executed if condition is non-zero. If size == 2, an optional ELSE graph is created and this is executed if the condition is zero.

CU_GRAPH_COND_TYPE_WHILE = 1
Conditional 'while' Node. Body executed repeatedly while condition value is non-zero.
CU_GRAPH_COND_TYPE_SWITCH = 2
Conditional 'switch' Node. Body[n] is executed once, where 'n' is the value of the condition. If the condition does not match
                                    a body index, no body is launched.

enum CUgraphDebugDot_flags
The additional write options for cuGraphDebugDotPrint

                                 Values



CU_GRAPH_DEBUG_DOT_FLAGS_VERBOSE = 1<<0
Output all debug data as if every debug flag is enabled
CU_GRAPH_DEBUG_DOT_FLAGS_RUNTIME_TYPES = 1<<1
Use CUDA Runtime structures for output
CU_GRAPH_DEBUG_DOT_FLAGS_KERNEL_NODE_PARAMS = 1<<2
Adds CUDA_KERNEL_NODE_PARAMS values to output
CU_GRAPH_DEBUG_DOT_FLAGS_MEMCPY_NODE_PARAMS = 1<<3
Adds CUDA_MEMCPY3D values to output
CU_GRAPH_DEBUG_DOT_FLAGS_MEMSET_NODE_PARAMS = 1<<4
Adds CUDA_MEMSET_NODE_PARAMS values to output
CU_GRAPH_DEBUG_DOT_FLAGS_HOST_NODE_PARAMS = 1<<5
Adds CUDA_HOST_NODE_PARAMS values to output
CU_GRAPH_DEBUG_DOT_FLAGS_EVENT_NODE_PARAMS = 1<<6
Adds CUevent handle from record and wait nodes to output
CU_GRAPH_DEBUG_DOT_FLAGS_EXT_SEMAS_SIGNAL_NODE_PARAMS = 1<<7
Adds CUDA_EXT_SEM_SIGNAL_NODE_PARAMS values to output
CU_GRAPH_DEBUG_DOT_FLAGS_EXT_SEMAS_WAIT_NODE_PARAMS = 1<<8
Adds CUDA_EXT_SEM_WAIT_NODE_PARAMS values to output
CU_GRAPH_DEBUG_DOT_FLAGS_KERNEL_NODE_ATTRIBUTES = 1<<9
Adds CUkernelNodeAttrValue values to output
CU_GRAPH_DEBUG_DOT_FLAGS_HANDLES = 1<<10
Adds node handles and every kernel function handle to output
CU_GRAPH_DEBUG_DOT_FLAGS_MEM_ALLOC_NODE_PARAMS = 1<<11
Adds memory alloc node parameters to output
CU_GRAPH_DEBUG_DOT_FLAGS_MEM_FREE_NODE_PARAMS = 1<<12
Adds memory free node parameters to output
CU_GRAPH_DEBUG_DOT_FLAGS_BATCH_MEM_OP_NODE_PARAMS = 1<<13
Adds batch mem op node parameters to output
CU_GRAPH_DEBUG_DOT_FLAGS_EXTRA_TOPO_INFO = 1<<14
Adds edge numbering information
CU_GRAPH_DEBUG_DOT_FLAGS_CONDITIONAL_NODE_PARAMS = 1<<15
Adds conditional node parameters to output

enum CUgraphDependencyType
Type annotations that can be applied to graph edges as part of CUgraphEdgeData.


                                 Values



CU_GRAPH_DEPENDENCY_TYPE_DEFAULT = 0
This is an ordinary dependency.
CU_GRAPH_DEPENDENCY_TYPE_PROGRAMMATIC = 1
This dependency type allows the downstream node to use cudaGridDependencySynchronize(). It may only be used between kernel nodes, and must be used with either the CU_GRAPH_KERNEL_NODE_PORT_PROGRAMMATIC or CU_GRAPH_KERNEL_NODE_PORT_LAUNCH_ORDER outgoing port.

enum CUgraphExecUpdateResult
CUDA Graph Update error types

                                 Values



CU_GRAPH_EXEC_UPDATE_SUCCESS = 0x0
The update succeeded
CU_GRAPH_EXEC_UPDATE_ERROR = 0x1
The update failed for an unexpected reason which is described in the return value of the function
CU_GRAPH_EXEC_UPDATE_ERROR_TOPOLOGY_CHANGED = 0x2
The update failed because the topology changed
CU_GRAPH_EXEC_UPDATE_ERROR_NODE_TYPE_CHANGED = 0x3
The update failed because a node type changed
CU_GRAPH_EXEC_UPDATE_ERROR_FUNCTION_CHANGED = 0x4
The update failed because the function of a kernel node changed (CUDA driver < 11.2)
CU_GRAPH_EXEC_UPDATE_ERROR_PARAMETERS_CHANGED = 0x5
The update failed because the parameters changed in a way that is not supported
CU_GRAPH_EXEC_UPDATE_ERROR_NOT_SUPPORTED = 0x6
The update failed because something about the node is not supported
CU_GRAPH_EXEC_UPDATE_ERROR_UNSUPPORTED_FUNCTION_CHANGE = 0x7
The update failed because the function of a kernel node changed in an unsupported way
CU_GRAPH_EXEC_UPDATE_ERROR_ATTRIBUTES_CHANGED = 0x8
The update failed because the node attributes changed in a way that is not supported

enum CUgraphInstantiateResult
Graph instantiation results

                                 Values



CUDA_GRAPH_INSTANTIATE_SUCCESS = 0
Instantiation succeeded
CUDA_GRAPH_INSTANTIATE_ERROR = 1
Instantiation failed for an unexpected reason which is described in the return value of the function
CUDA_GRAPH_INSTANTIATE_INVALID_STRUCTURE = 2
Instantiation failed due to invalid structure, such as cycles
CUDA_GRAPH_INSTANTIATE_NODE_OPERATION_NOT_SUPPORTED = 3
Instantiation for device launch failed because the graph contained an unsupported operation
CUDA_GRAPH_INSTANTIATE_MULTIPLE_CTXS_NOT_SUPPORTED = 4
Instantiation for device launch failed due to the nodes belonging to different contexts
CUDA_GRAPH_INSTANTIATE_CONDITIONAL_HANDLE_UNUSED = 5
One or more conditional handles are not associated with conditional nodes

enum CUgraphInstantiate_flags
Flags for instantiating a graph

                                 Values



CUDA_GRAPH_INSTANTIATE_FLAG_AUTO_FREE_ON_LAUNCH = 1
Automatically free memory allocated in a graph before relaunching.
CUDA_GRAPH_INSTANTIATE_FLAG_UPLOAD = 2
Automatically upload the graph after instantiation. Only supported by cuGraphInstantiateWithParams. The upload will be performed using the stream provided in instantiateParams.

CUDA_GRAPH_INSTANTIATE_FLAG_DEVICE_LAUNCH = 4
Instantiate the graph to be launchable from the device. This flag can only be used on platforms which support unified addressing.
                                    This flag cannot be used in conjunction with CUDA_GRAPH_INSTANTIATE_FLAG_AUTO_FREE_ON_LAUNCH.

CUDA_GRAPH_INSTANTIATE_FLAG_USE_NODE_PRIORITY = 8
Run the graph using the per-node priority attributes rather than the priority of the stream it is launched into.

enum CUgraphNodeType
Graph node types

                                 Values



CU_GRAPH_NODE_TYPE_KERNEL = 0
GPU kernel node
CU_GRAPH_NODE_TYPE_MEMCPY = 1
Memcpy node
CU_GRAPH_NODE_TYPE_MEMSET = 2
Memset node
CU_GRAPH_NODE_TYPE_HOST = 3
Host (executable) node
CU_GRAPH_NODE_TYPE_GRAPH = 4
Node which executes an embedded graph
CU_GRAPH_NODE_TYPE_EMPTY = 5
Empty (no-op) node
CU_GRAPH_NODE_TYPE_WAIT_EVENT = 6
External event wait node
CU_GRAPH_NODE_TYPE_EVENT_RECORD = 7
External event record node
CU_GRAPH_NODE_TYPE_EXT_SEMAS_SIGNAL = 8
External semaphore signal node
CU_GRAPH_NODE_TYPE_EXT_SEMAS_WAIT = 9
External semaphore wait node
CU_GRAPH_NODE_TYPE_MEM_ALLOC = 10
Memory Allocation Node
CU_GRAPH_NODE_TYPE_MEM_FREE = 11
Memory Free Node
CU_GRAPH_NODE_TYPE_BATCH_MEM_OP = 12
Batch MemOp Node See cuStreamBatchMemOp and CUstreamBatchMemOpType for what these nodes can do.

CU_GRAPH_NODE_TYPE_CONDITIONAL = 13
Conditional NodeMay be used to implement a conditional execution path or loop inside of a graph. The graph(s) contained within
                                    the body of the conditional node can be selectively executed or iterated upon based on the value of a conditional variable.Handles
                                    must be created in advance of creating the node using cuGraphConditionalHandleCreate.The following restrictions apply to graphs which contain conditional nodes: The graph cannot be used in a child node. Only
                                    one instantiation of the graph may exist at any point in time. The graph cannot be cloned.To set the control value, supply
                                    a default value when creating the handle and/or call cudaGraphSetConditional from device code.

enum CUgraphicsMapResourceFlags
Flags for mapping and unmapping interop resources

                                 Values



CU_GRAPHICS_MAP_RESOURCE_FLAGS_NONE = 0x00

CU_GRAPHICS_MAP_RESOURCE_FLAGS_READ_ONLY = 0x01

CU_GRAPHICS_MAP_RESOURCE_FLAGS_WRITE_DISCARD = 0x02

enum CUgraphicsRegisterFlags
Flags to register a graphics resource

                                 Values



CU_GRAPHICS_REGISTER_FLAGS_NONE = 0x00

CU_GRAPHICS_REGISTER_FLAGS_READ_ONLY = 0x01

CU_GRAPHICS_REGISTER_FLAGS_WRITE_DISCARD = 0x02

CU_GRAPHICS_REGISTER_FLAGS_SURFACE_LDST = 0x04

CU_GRAPHICS_REGISTER_FLAGS_TEXTURE_GATHER = 0x08

enum CUipcMem_flags
CUDA Ipc Mem Flags

                                 Values



CU_IPC_MEM_LAZY_ENABLE_PEER_ACCESS = 0x1
Automatically enable peer access between remote devices as needed

enum CUjitInputType
Device code formats

                                 Values



CU_JIT_INPUT_CUBIN = 0
Compiled device-class-specific device code
                                    Applicable options: none

CU_JIT_INPUT_PTX = 1
PTX source code
                                    Applicable options: PTX compiler options

CU_JIT_INPUT_FATBINARY = 2
Bundle of multiple cubins and/or PTX of some device code
                                    Applicable options: PTX compiler options, CU_JIT_FALLBACK_STRATEGY

CU_JIT_INPUT_OBJECT = 3
Host object with embedded device code
                                    Applicable options: PTX compiler options, CU_JIT_FALLBACK_STRATEGY

CU_JIT_INPUT_LIBRARY = 4
Archive of host objects with embedded device code
                                    Applicable options: PTX compiler options, CU_JIT_FALLBACK_STRATEGY

CU_JIT_INPUT_NVVM = 5

Deprecated
High-level intermediate code for link-time optimization
                                          Applicable options: NVVM compiler options, PTX compiler options

                                       Only valid with LTO-IR compiled with toolkits prior to CUDA 12.0


CU_JIT_NUM_INPUT_TYPES = 6

enum CUjit_cacheMode
Caching modes for dlcm

                                 Values



CU_JIT_CACHE_OPTION_NONE = 0
Compile with no -dlcm flag specified
CU_JIT_CACHE_OPTION_CG
Compile with L1 cache disabled
CU_JIT_CACHE_OPTION_CA
Compile with L1 cache enabled

enum CUjit_fallback
Cubin matching fallback strategies

                                 Values



CU_PREFER_PTX = 0
Prefer to compile ptx if exact binary match not found
CU_PREFER_BINARY
Prefer to fall back to compatible binary code if exact match not found

enum CUjit_option
Online compiler and linker options

                                 Values



CU_JIT_MAX_REGISTERS = 0
Max number of registers that a thread may use.
                                    Option type: unsigned int
                                    Applies to: compiler only

CU_JIT_THREADS_PER_BLOCK = 1
IN: Specifies minimum number of threads per block to target compilation for
                                    OUT: Returns the number of threads the compiler actually targeted. This restricts the resource utilization of the compiler
                                    (e.g. max registers) such that a block with the given number of threads should be able to launch based on register limitations.
                                    Note, this option does not currently take into account any other resource limitations, such as shared memory utilization.
                                    Cannot be combined with CU_JIT_TARGET.
                                    Option type: unsigned int
                                    Applies to: compiler only

CU_JIT_WALL_TIME = 2
Overwrites the option value with the total wall clock time, in milliseconds, spent in the compiler and linker
                                    Option type: float
                                    Applies to: compiler and linker

CU_JIT_INFO_LOG_BUFFER = 3
Pointer to a buffer in which to print any log messages that are informational in nature (the buffer size is specified via
                                    option CU_JIT_INFO_LOG_BUFFER_SIZE_BYTES)
                                    Option type: char *
                                    Applies to: compiler and linker

CU_JIT_INFO_LOG_BUFFER_SIZE_BYTES = 4
IN: Log buffer size in bytes. Log messages will be capped at this size (including null terminator)
                                    OUT: Amount of log buffer filled with messages
                                    Option type: unsigned int
                                    Applies to: compiler and linker

CU_JIT_ERROR_LOG_BUFFER = 5
Pointer to a buffer in which to print any log messages that reflect errors (the buffer size is specified via option CU_JIT_ERROR_LOG_BUFFER_SIZE_BYTES)
                                    Option type: char *
                                    Applies to: compiler and linker

CU_JIT_ERROR_LOG_BUFFER_SIZE_BYTES = 6
IN: Log buffer size in bytes. Log messages will be capped at this size (including null terminator)
                                    OUT: Amount of log buffer filled with messages
                                    Option type: unsigned int
                                    Applies to: compiler and linker

CU_JIT_OPTIMIZATION_LEVEL = 7
Level of optimizations to apply to generated code (0 - 4), with 4 being the default and highest level of optimizations.
                                    Option type: unsigned int
                                    Applies to: compiler only

CU_JIT_TARGET_FROM_CUCONTEXT = 8
No option value required. Determines the target based on the current attached context (default)
                                    Option type: No option value needed
                                    Applies to: compiler and linker

CU_JIT_TARGET = 9
Target is chosen based on supplied CUjit_target. Cannot be combined with CU_JIT_THREADS_PER_BLOCK.
                                    Option type: unsigned int for enumerated type CUjit_target
                                    Applies to: compiler and linker

CU_JIT_FALLBACK_STRATEGY = 10
Specifies choice of fallback strategy if matching cubin is not found. Choice is based on supplied CUjit_fallback. This option cannot be used with cuLink* APIs as the linker requires exact matches.
                                    Option type: unsigned int for enumerated type CUjit_fallback
                                    Applies to: compiler only

CU_JIT_GENERATE_DEBUG_INFO = 11
Specifies whether to create debug information in output (-g) (0: false, default)
                                    Option type: int
                                    Applies to: compiler and linker

CU_JIT_LOG_VERBOSE = 12
Generate verbose log messages (0: false, default)
                                    Option type: int
                                    Applies to: compiler and linker

CU_JIT_GENERATE_LINE_INFO = 13
Generate line number information (-lineinfo) (0: false, default)
                                    Option type: int
                                    Applies to: compiler only

CU_JIT_CACHE_MODE = 14
Specifies whether to enable caching explicitly (-dlcm)
                                    Choice is based on supplied CUjit_cacheMode_enum.
                                    Option type: unsigned int for enumerated type CUjit_cacheMode_enum
                                    Applies to: compiler only

CU_JIT_NEW_SM3X_OPT = 15

Deprecated
This jit option is deprecated and should not be used.

CU_JIT_FAST_COMPILE = 16
This jit option is used for internal purpose only.
CU_JIT_GLOBAL_SYMBOL_NAMES = 17
Array of device symbol names that will be relocated to the corresponding host addresses stored in CU_JIT_GLOBAL_SYMBOL_ADDRESSES.
                                    Must contain CU_JIT_GLOBAL_SYMBOL_COUNT entries.
                                    When loading a device module, driver will relocate all encountered unresolved symbols to the host addresses.
                                    It is only allowed to register symbols that correspond to unresolved global variables.
                                    It is illegal to register the same device symbol at multiple addresses.
                                    Option type: const char 
                                    Applies to: dynamic linker only

CU_JIT_GLOBAL_SYMBOL_ADDRESSES = 18
Array of host addresses that will be used to relocate corresponding device symbols stored in CU_JIT_GLOBAL_SYMBOL_NAMES.
                                    Must contain CU_JIT_GLOBAL_SYMBOL_COUNT entries.
                                    Option type: void 
                                    Applies to: dynamic linker only

CU_JIT_GLOBAL_SYMBOL_COUNT = 19
Number of entries in CU_JIT_GLOBAL_SYMBOL_NAMES and CU_JIT_GLOBAL_SYMBOL_ADDRESSES arrays.
                                    Option type: unsigned int
                                    Applies to: dynamic linker only

CU_JIT_LTO = 20

Deprecated
Enable link-time optimization (-dlto) for device code (Disabled by default).
                                          This option is not supported on 32-bit platforms.
                                          Option type: int
                                          Applies to: compiler and linker

                                       Only valid with LTO-IR compiled with toolkits prior to CUDA 12.0


CU_JIT_FTZ = 21

Deprecated
Control single-precision denormals (-ftz) support (0: false, default). 1 : flushes denormal values to zero 0 : preserves denormal
                                          values Option type: int
                                          Applies to: link-time optimization specified with CU_JIT_LTO

                                       Only valid with LTO-IR compiled with toolkits prior to CUDA 12.0


CU_JIT_PREC_DIV = 22

Deprecated
Control single-precision floating-point division and reciprocals (-prec-div) support (1: true, default). 1 : Enables the IEEE
                                          round-to-nearest mode 0 : Enables the fast approximation mode Option type: int
                                          Applies to: link-time optimization specified with CU_JIT_LTO

                                       Only valid with LTO-IR compiled with toolkits prior to CUDA 12.0


CU_JIT_PREC_SQRT = 23

Deprecated
Control single-precision floating-point square root (-prec-sqrt) support (1: true, default). 1 : Enables the IEEE round-to-nearest
                                          mode 0 : Enables the fast approximation mode Option type: int
                                          Applies to: link-time optimization specified with CU_JIT_LTO

                                       Only valid with LTO-IR compiled with toolkits prior to CUDA 12.0


CU_JIT_FMA = 24

Deprecated
Enable/Disable the contraction of floating-point multiplies and adds/subtracts into floating-point multiply-add (-fma) operations
                                          (1: Enable, default; 0: Disable). Option type: int
                                          Applies to: link-time optimization specified with CU_JIT_LTO

                                       Only valid with LTO-IR compiled with toolkits prior to CUDA 12.0


CU_JIT_REFERENCED_KERNEL_NAMES = 25

Deprecated
Array of kernel names that should be preserved at link time while others can be removed.
                                          Must contain CU_JIT_REFERENCED_KERNEL_COUNT entries.
                                          Note that kernel names can be mangled by the compiler in which case the mangled name needs to be specified.
                                          Wildcard "*" can be used to represent zero or more characters instead of specifying the full or mangled name.
                                          It is important to note that the wildcard "*" is also added implicitly. For example, specifying "foo" will match "foobaz",
                                          "barfoo", "barfoobaz" and thus preserve all kernels with those names. This can be avoided by providing a more specific name
                                          like "barfoobaz".
                                          Option type: const char 
                                          Applies to: dynamic linker only

                                       Only valid with LTO-IR compiled with toolkits prior to CUDA 12.0


CU_JIT_REFERENCED_KERNEL_COUNT = 26

Deprecated
Number of entries in CU_JIT_REFERENCED_KERNEL_NAMES array.
                                          Option type: unsigned int
                                          Applies to: dynamic linker only

                                       Only valid with LTO-IR compiled with toolkits prior to CUDA 12.0


CU_JIT_REFERENCED_VARIABLE_NAMES = 27

Deprecated
Array of variable names (__device__ and/or __constant__) that should be preserved at link time while others can be removed.
                                          Must contain CU_JIT_REFERENCED_VARIABLE_COUNT entries.
                                          Note that variable names can be mangled by the compiler in which case the mangled name needs to be specified.
                                          Wildcard "*" can be used to represent zero or more characters instead of specifying the full or mangled name.
                                          It is important to note that the wildcard "*" is also added implicitly. For example, specifying "foo" will match "foobaz",
                                          "barfoo", "barfoobaz" and thus preserve all variables with those names. This can be avoided by providing a more specific name
                                          like "barfoobaz".
                                          Option type: const char 
                                          Applies to: link-time optimization specified with CU_JIT_LTO

                                       Only valid with LTO-IR compiled with toolkits prior to CUDA 12.0


CU_JIT_REFERENCED_VARIABLE_COUNT = 28

Deprecated
Number of entries in CU_JIT_REFERENCED_VARIABLE_NAMES array.
                                          Option type: unsigned int
                                          Applies to: link-time optimization specified with CU_JIT_LTO

                                       Only valid with LTO-IR compiled with toolkits prior to CUDA 12.0


CU_JIT_OPTIMIZE_UNUSED_DEVICE_VARIABLES = 29

Deprecated
This option serves as a hint to enable the JIT compiler/linker to remove constant (__constant__) and device (__device__) variables
                                          unreferenced in device code (Disabled by default).
                                          Note that host references to constant and device variables using APIs like cuModuleGetGlobal() with this option specified may result in undefined behavior unless the variables are explicitly specified using CU_JIT_REFERENCED_VARIABLE_NAMES.
                                          Option type: int
                                          Applies to: link-time optimization specified with CU_JIT_LTO

                                       Only valid with LTO-IR compiled with toolkits prior to CUDA 12.0


CU_JIT_POSITION_INDEPENDENT_CODE = 30
Generate position independent code (0: false)
                                    Option type: int
                                    Applies to: compiler only

CU_JIT_MIN_CTA_PER_SM = 31
This option hints to the JIT compiler the minimum number of CTAs from the kernel’s grid to be mapped to a SM. This option
                                    is ignored when used together with CU_JIT_MAX_REGISTERS or CU_JIT_THREADS_PER_BLOCK. Optimizations based on this option need CU_JIT_MAX_THREADS_PER_BLOCK to be specified as well. For kernels already using PTX directive .minnctapersm, this option will be ignored by default. Use
                                    CU_JIT_OVERRIDE_DIRECTIVE_VALUES to let this option take precedence over the PTX directive. Option type: unsigned int
                                    Applies to: compiler only

CU_JIT_MAX_THREADS_PER_BLOCK = 32
Maximum number threads in a thread block, computed as the product of the maximum extent specifed for each dimension of the
                                    block. This limit is guaranteed not to be exeeded in any invocation of the kernel. Exceeding the the maximum number of threads
                                    results in runtime error or kernel launch failure. For kernels already using PTX directive .maxntid, this option will be ignored
                                    by default. Use CU_JIT_OVERRIDE_DIRECTIVE_VALUES to let this option take precedence over the PTX directive. Option type: int
                                    Applies to: compiler only

CU_JIT_OVERRIDE_DIRECTIVE_VALUES = 33
This option lets the values specified using CU_JIT_MAX_REGISTERS, CU_JIT_THREADS_PER_BLOCK, CU_JIT_MAX_THREADS_PER_BLOCK and CU_JIT_MIN_CTA_PER_SM take precedence over any PTX directives. (0: Disable, default; 1: Enable) Option type: int
                                    Applies to: compiler only

CU_JIT_SPLIT_COMPILE = 34
This option specifies the maximum number of concurrent threads to use when running compiler optimizations. If the specified
                                    value is 1, the option will be ignored. If the specified value is 0, the number of threads will match the number of CPUs on
                                    the underlying machine. Otherwise, if the option is N, then up to N threads will be used. Option type: unsigned int
                                    Applies to: compiler only

CU_JIT_BINARY_LOADER_THREAD_COUNT = 35
This option specifies the maximum number of concurrent threads to use when compiling device code. If the specified value is
                                    1, the option will be ignored. If the specified value is 0, the number of threads will match the number of CPUs on the underlying
                                    machine. Otherwise, if the option is N, then up to N threads will be used. This option is ignored if the env var CUDA_BINARY_LOADER_THREAD_COUNT
                                    is set. Option type: unsigned int
                                    Applies to: compiler and linker

CU_JIT_NUM_OPTIONS

enum CUjit_target
Online compilation targets

                                 Values



CU_TARGET_COMPUTE_30 = 30
Compute device class 3.0
CU_TARGET_COMPUTE_32 = 32
Compute device class 3.2
CU_TARGET_COMPUTE_35 = 35
Compute device class 3.5
CU_TARGET_COMPUTE_37 = 37
Compute device class 3.7
CU_TARGET_COMPUTE_50 = 50
Compute device class 5.0
CU_TARGET_COMPUTE_52 = 52
Compute device class 5.2
CU_TARGET_COMPUTE_53 = 53
Compute device class 5.3
CU_TARGET_COMPUTE_60 = 60
Compute device class 6.0.
CU_TARGET_COMPUTE_61 = 61
Compute device class 6.1.
CU_TARGET_COMPUTE_62 = 62
Compute device class 6.2.
CU_TARGET_COMPUTE_70 = 70
Compute device class 7.0.
CU_TARGET_COMPUTE_72 = 72
Compute device class 7.2.
CU_TARGET_COMPUTE_75 = 75
Compute device class 7.5.
CU_TARGET_COMPUTE_80 = 80
Compute device class 8.0.
CU_TARGET_COMPUTE_86 = 86
Compute device class 8.6.
CU_TARGET_COMPUTE_87 = 87
Compute device class 8.7.
CU_TARGET_COMPUTE_89 = 89
Compute device class 8.9.
CU_TARGET_COMPUTE_90 = 90
Compute device class 9.0.
CU_TARGET_COMPUTE_100 = 100
Compute device class 10.0.
CU_TARGET_COMPUTE_110 = 110
Compute device class 11.0.
CU_TARGET_COMPUTE_103 = 103
Compute device class 10.3.
CU_TARGET_COMPUTE_120 = 120
Compute device class 12.0.
CU_TARGET_COMPUTE_121 = 121
Compute device class 12.1. Compute device class 9.0. with accelerated features.
CU_TARGET_COMPUTE_90A = CU_COMPUTE_ACCELERATED_TARGET_BASE+CU_TARGET_COMPUTE_90
Compute device class 10.0. with accelerated features.
CU_TARGET_COMPUTE_100A = CU_COMPUTE_ACCELERATED_TARGET_BASE+CU_TARGET_COMPUTE_100
Compute device class 11.0 with accelerated features.
CU_TARGET_COMPUTE_110A = CU_COMPUTE_ACCELERATED_TARGET_BASE+CU_TARGET_COMPUTE_110
Compute device class 10.3. with accelerated features.
CU_TARGET_COMPUTE_103A = CU_COMPUTE_ACCELERATED_TARGET_BASE+CU_TARGET_COMPUTE_103
Compute device class 12.0. with accelerated features.
CU_TARGET_COMPUTE_120A = CU_COMPUTE_ACCELERATED_TARGET_BASE+CU_TARGET_COMPUTE_120
Compute device class 12.1. with accelerated features.
CU_TARGET_COMPUTE_121A = CU_COMPUTE_ACCELERATED_TARGET_BASE+CU_TARGET_COMPUTE_121
Compute device class 10.x with family features.
CU_TARGET_COMPUTE_100F = CU_COMPUTE_FAMILY_TARGET_BASE+CU_TARGET_COMPUTE_100
Compute device class 11.0 with family features.
CU_TARGET_COMPUTE_110F = CU_COMPUTE_FAMILY_TARGET_BASE+CU_TARGET_COMPUTE_110
Compute device class 10.3. with family features.
CU_TARGET_COMPUTE_103F = CU_COMPUTE_FAMILY_TARGET_BASE+CU_TARGET_COMPUTE_103
Compute device class 12.0. with family features.
CU_TARGET_COMPUTE_120F = CU_COMPUTE_FAMILY_TARGET_BASE+CU_TARGET_COMPUTE_120
Compute device class 12.1. with family features.
CU_TARGET_COMPUTE_121F = CU_COMPUTE_FAMILY_TARGET_BASE+CU_TARGET_COMPUTE_121

enum CUlaunchAttributeID
Launch attributes enum; used as id field of CUlaunchAttribute

                                 Values



CU_LAUNCH_ATTRIBUTE_IGNORE = 0
Ignored entry, for convenient composition
CU_LAUNCH_ATTRIBUTE_ACCESS_POLICY_WINDOW = 1
Valid for streams, graph nodes, launches. See CUlaunchAttributeValue::accessPolicyWindow.

CU_LAUNCH_ATTRIBUTE_COOPERATIVE = 2
Valid for graph nodes, launches. See CUlaunchAttributeValue::cooperative.

CU_LAUNCH_ATTRIBUTE_SYNCHRONIZATION_POLICY = 3
Valid for streams. See CUlaunchAttributeValue::syncPolicy.

CU_LAUNCH_ATTRIBUTE_CLUSTER_DIMENSION = 4
Valid for graph nodes, launches. See CUlaunchAttributeValue::clusterDim.

CU_LAUNCH_ATTRIBUTE_CLUSTER_SCHEDULING_POLICY_PREFERENCE = 5
Valid for graph nodes, launches. See CUlaunchAttributeValue::clusterSchedulingPolicyPreference.

CU_LAUNCH_ATTRIBUTE_PROGRAMMATIC_STREAM_SERIALIZATION = 6
Valid for launches. Setting CUlaunchAttributeValue::programmaticStreamSerializationAllowed to non-0 signals that the kernel will use programmatic means to resolve its stream dependency, so that the CUDA runtime should
                                    opportunistically allow the grid's execution to overlap with the previous kernel in the stream, if that kernel requests the
                                    overlap. The dependent launches can choose to wait on the dependency using the programmatic sync (cudaGridDependencySynchronize() or equivalent PTX instructions).

CU_LAUNCH_ATTRIBUTE_PROGRAMMATIC_EVENT = 7
Valid for launches. Set CUlaunchAttributeValue::programmaticEvent to record the event. Event recorded through this launch attribute is guaranteed to only trigger after all block in the associated
                                    kernel trigger the event. A block can trigger the event through PTX launchdep.release or CUDA builtin function cudaTriggerProgrammaticLaunchCompletion(). A trigger can also be inserted at the beginning of each block's execution if triggerAtBlockStart is set to non-0. The dependent
                                    launches can choose to wait on the dependency using the programmatic sync (cudaGridDependencySynchronize() or equivalent PTX instructions). Note that dependents (including the CPU thread calling cuEventSynchronize()) are not guaranteed to observe the release precisely when it is released. For example, cuEventSynchronize() may only observe the event trigger long after the associated kernel has completed. This recording type is primarily meant
                                    for establishing programmatic dependency between device tasks. Note also this type of dependency allows, but does not guarantee,
                                    concurrent execution of tasks.
                                    The event supplied must not be an interprocess or interop event. The event must disable timing (i.e. must be created with
                                    the CU_EVENT_DISABLE_TIMING flag set).

CU_LAUNCH_ATTRIBUTE_PRIORITY = 8
Valid for streams, graph nodes, launches. See CUlaunchAttributeValue::priority.

CU_LAUNCH_ATTRIBUTE_MEM_SYNC_DOMAIN_MAP = 9
Valid for streams, graph nodes, launches. See CUlaunchAttributeValue::memSyncDomainMap.

CU_LAUNCH_ATTRIBUTE_MEM_SYNC_DOMAIN = 10
Valid for streams, graph nodes, launches. See CUlaunchAttributeValue::memSyncDomain.

CU_LAUNCH_ATTRIBUTE_PREFERRED_CLUSTER_DIMENSION = 11
Valid for graph nodes, launches. Set CUlaunchAttributeValue::preferredClusterDim to allow the kernel launch to specify a preferred substitute cluster dimension. Blocks may be grouped according to either
                                    the dimensions specified with this attribute (grouped into a "preferred substitute cluster"), or the one specified with CU_LAUNCH_ATTRIBUTE_CLUSTER_DIMENSION attribute (grouped into a "regular cluster"). The cluster dimensions of a "preferred substitute cluster" shall be an integer
                                    multiple greater than zero of the regular cluster dimensions. The device will attempt - on a best-effort basis - to group
                                    thread blocks into preferred clusters over grouping them into regular clusters. When it deems necessary (primarily when the
                                    device temporarily runs out of physical resources to launch the larger preferred clusters), the device may switch to launch
                                    the regular clusters instead to attempt to utilize as much of the physical device resources as possible.
                                    Each type of cluster will have its enumeration / coordinate setup as if the grid consists solely of its type of cluster. For
                                    example, if the preferred substitute cluster dimensions double the regular cluster dimensions, there might be simultaneously
                                    a regular cluster indexed at (1,0,0), and a preferred cluster indexed at (1,0,0). In this example, the preferred substitute
                                    cluster (1,0,0) replaces regular clusters (2,0,0) and (3,0,0) and groups their blocks.
                                    This attribute will only take effect when a regular cluster dimension has been specified. The preferred substitute cluster
                                    dimension must be an integer multiple greater than zero of the regular cluster dimension and must divide the grid. It must
                                    also be no more than `maxBlocksPerCluster`, if it is set in the kernel's `__launch_bounds__`. Otherwise it must be less than
                                    the maximum value the driver can support. Otherwise, setting this attribute to a value physically unable to fit on any particular
                                    device is permitted.

CU_LAUNCH_ATTRIBUTE_LAUNCH_COMPLETION_EVENT = 12
Valid for launches. Set CUlaunchAttributeValue::launchCompletionEvent to record the event.
                                    Nominally, the event is triggered once all blocks of the kernel have begun execution. Currently this is a best effort. If
                                    a kernel B has a launch completion dependency on a kernel A, B may wait until A is complete. Alternatively, blocks of B may
                                    begin before all blocks of A have begun, for example if B can claim execution resources unavailable to A (e.g. they run on
                                    different GPUs) or if B is a higher priority than A. Exercise caution if such an ordering inversion could lead to deadlock.

                                    A launch completion event is nominally similar to a programmatic event with triggerAtBlockStart set except that it is not visible to cudaGridDependencySynchronize() and can be used with compute capability less than 9.0.
                                    The event supplied must not be an interprocess or interop event. The event must disable timing (i.e. must be created with
                                    the CU_EVENT_DISABLE_TIMING flag set).

CU_LAUNCH_ATTRIBUTE_DEVICE_UPDATABLE_KERNEL_NODE = 13
Valid for graph nodes, launches. This attribute is graphs-only, and passing it to a launch in a non-capturing stream will
                                    result in an error.
                                    CUlaunchAttributeValue::deviceUpdatableKernelNode::deviceUpdatable can only be set to 0 or 1. Setting the field to 1 indicates
                                    that the corresponding kernel node should be device-updatable. On success, a handle will be returned via CUlaunchAttributeValue::deviceUpdatableKernelNode::devNode
                                    which can be passed to the various device-side update functions to update the node's kernel parameters from within another
                                    kernel. For more information on the types of device updates that can be made, as well as the relevant limitations thereof,
                                    see cudaGraphKernelNodeUpdatesApply.
                                    Nodes which are device-updatable have additional restrictions compared to regular kernel nodes. Firstly, device-updatable
                                    nodes cannot be removed from their graph via cuGraphDestroyNode. Additionally, once opted-in to this functionality, a node cannot opt out, and any attempt to set the deviceUpdatable attribute
                                    to 0 will result in an error. Device-updatable kernel nodes also cannot have their attributes copied to/from another kernel
                                    node via cuGraphKernelNodeCopyAttributes. Graphs containing one or more device-updatable nodes also do not allow multiple instantiation, and neither the graph nor
                                    its instantiated version can be passed to cuGraphExecUpdate.
                                    If a graph contains device-updatable nodes and updates those nodes from the device from within the graph, the graph must be
                                    uploaded with cuGraphUpload before it is launched. For such a graph, if host-side executable graph updates are made to the device-updatable nodes, the
                                    graph must be uploaded before it is launched again.

CU_LAUNCH_ATTRIBUTE_PREFERRED_SHARED_MEMORY_CARVEOUT = 14
Valid for launches. On devices where the L1 cache and shared memory use the same hardware resources, setting CUlaunchAttributeValue::sharedMemCarveout to a percentage between 0-100 signals the CUDA driver to set the shared memory carveout preference, in percent of the total
                                    shared memory for that kernel launch. This attribute takes precedence over CU_FUNC_ATTRIBUTE_PREFERRED_SHARED_MEMORY_CARVEOUT. This is only a hint, and the CUDA driver can choose a different configuration if required for the launch.

CU_LAUNCH_ATTRIBUTE_NVLINK_UTIL_CENTRIC_SCHEDULING = 16
Valid for streams, graph nodes, launches. This attribute is a hint to the CUDA runtime that the launch should attempt to make
                                    the kernel maximize its NVLINK utilization.
                                    When possible to honor this hint, CUDA will assume each block in the grid launch will carry out an even amount of NVLINK traffic,
                                    and make a best-effort attempt to adjust the kernel launch based on that assumption.
                                    This attribute is a hint only. CUDA makes no functional or performance guarantee. Its applicability can be affected by many
                                    different factors, including driver version (i.e. CUDA doesn't guarantee the performance characteristics will be maintained
                                    between driver versions or a driver update could alter or regress previously observed perf characteristics.) It also doesn't
                                    guarantee a successful result, i.e. applying the attribute may not improve the performance of either the targeted kernel or
                                    the encapsulating application.
                                    Valid values for CUlaunchAttributeValue::nvlinkUtilCentricScheduling are 0 (disabled) and 1 (enabled).

enum CUlaunchMemSyncDomain
Memory Synchronization Domain
A kernel can be launched in a specified memory synchronization domain that affects all memory operations issued by that kernel.
                                 A memory barrier issued in one domain will only order memory operations in that domain, thus eliminating latency increase
                                 from memory barriers ordering unrelated traffic.

By default, kernels are launched in domain 0. Kernel launched with CU_LAUNCH_MEM_SYNC_DOMAIN_REMOTE will have a different domain ID. User may also alter the domain ID with CUlaunchMemSyncDomainMap for a specific stream / graph node / kernel launch. See CU_LAUNCH_ATTRIBUTE_MEM_SYNC_DOMAIN, cuStreamSetAttribute, cuLaunchKernelEx, cuGraphKernelNodeSetAttribute.

Memory operations done in kernels launched in different domains are considered system-scope distanced. In other words, a GPU
                                 scoped memory synchronization is not sufficient for memory order to be observed by kernels in another memory synchronization
                                 domain even if they are on the same GPU.


                                 Values



CU_LAUNCH_MEM_SYNC_DOMAIN_DEFAULT = 0
Launch kernels in the default domain
CU_LAUNCH_MEM_SYNC_DOMAIN_REMOTE = 1
Launch kernels in the remote domain

enum CUlibraryOption
Library options to be specified with cuLibraryLoadData() or cuLibraryLoadFromFile()

                                 Values



CU_LIBRARY_HOST_UNIVERSAL_FUNCTION_AND_DATA_TABLE = 0

CU_LIBRARY_BINARY_IS_PRESERVED = 1
Specifes that the argument code passed to cuLibraryLoadData() will be preserved. Specifying this option will let the driver know that code can be accessed at any point until cuLibraryUnload(). The default behavior is for the driver to allocate and maintain its own copy of code. Note that this is only a memory usage optimization hint and the driver can choose to ignore it if required. Specifying this
                                    option with cuLibraryLoadFromFile() is invalid and will return CUDA_ERROR_INVALID_VALUE.

CU_LIBRARY_NUM_OPTIONS

enum CUlimit
Limits

                                 Values



CU_LIMIT_STACK_SIZE = 0x00
GPU thread stack size
CU_LIMIT_PRINTF_FIFO_SIZE = 0x01
GPU printf FIFO size
CU_LIMIT_MALLOC_HEAP_SIZE = 0x02
GPU malloc heap size
CU_LIMIT_DEV_RUNTIME_SYNC_DEPTH = 0x03
GPU device runtime launch synchronize depth
CU_LIMIT_DEV_RUNTIME_PENDING_LAUNCH_COUNT = 0x04
GPU device runtime pending launch count
CU_LIMIT_MAX_L2_FETCH_GRANULARITY = 0x05
A value between 0 and 128 that indicates the maximum fetch granularity of L2 (in Bytes). This is a hint
CU_LIMIT_PERSISTING_L2_CACHE_SIZE = 0x06
A size in bytes for L2 persisting lines cache size
CU_LIMIT_SHMEM_SIZE = 0x07
A maximum size in bytes of shared memory available to CUDA kernels on a CIG context. Can only be queried, cannot be set
CU_LIMIT_CIG_ENABLED = 0x08
A non-zero value indicates this CUDA context is a CIG-enabled context. Can only be queried, cannot be set
CU_LIMIT_CIG_SHMEM_FALLBACK_ENABLED = 0x09
When set to zero, CUDA will fail to launch a kernel on a CIG context, instead of using the fallback path, if the kernel uses
                                    more shared memory than available

CU_LIMIT_MAX

enum CUmemAccess_flags
Specifies the memory protection flags for mapping.

                                 Values



CU_MEM_ACCESS_FLAGS_PROT_NONE = 0x0
Default, make the address range not accessible
CU_MEM_ACCESS_FLAGS_PROT_READ = 0x1
Make the address range read accessible
CU_MEM_ACCESS_FLAGS_PROT_READWRITE = 0x3
Make the address range read-write accessible
CU_MEM_ACCESS_FLAGS_PROT_MAX = 0x7FFFFFFF

enum CUmemAllocationCompType
Specifies compression attribute for an allocation.

                                 Values



CU_MEM_ALLOCATION_COMP_NONE = 0x0
Allocating non-compressible memory
CU_MEM_ALLOCATION_COMP_GENERIC = 0x1
Allocating compressible memory

enum CUmemAllocationGranularity_flags
Flag for requesting different optimal and required granularities for an allocation.

                                 Values



CU_MEM_ALLOC_GRANULARITY_MINIMUM = 0x0
Minimum required granularity for allocation
CU_MEM_ALLOC_GRANULARITY_RECOMMENDED = 0x1
Recommended granularity for allocation for best performance

enum CUmemAllocationHandleType
Flags for specifying particular handle types

                                 Values



CU_MEM_HANDLE_TYPE_NONE = 0x0
Does not allow any export mechanism. >
CU_MEM_HANDLE_TYPE_POSIX_FILE_DESCRIPTOR = 0x1
Allows a file descriptor to be used for exporting. Permitted only on POSIX systems. (int)
CU_MEM_HANDLE_TYPE_WIN32 = 0x2
Allows a Win32 NT handle to be used for exporting. (HANDLE)
CU_MEM_HANDLE_TYPE_WIN32_KMT = 0x4
Allows a Win32 KMT handle to be used for exporting. (D3DKMT_HANDLE)
CU_MEM_HANDLE_TYPE_FABRIC = 0x8
Allows a fabric handle to be used for exporting. (CUmemFabricHandle)
CU_MEM_HANDLE_TYPE_MAX = 0x7FFFFFFF

enum CUmemAllocationType
Defines the allocation types available

                                 Values



CU_MEM_ALLOCATION_TYPE_INVALID = 0x0

CU_MEM_ALLOCATION_TYPE_PINNED = 0x1
This allocation type is 'pinned', i.e. cannot migrate from its current location while the application is actively using it


CU_MEM_ALLOCATION_TYPE_MANAGED = 0x2
This allocation type is managed memory
CU_MEM_ALLOCATION_TYPE_MAX = 0x7FFFFFFF

enum CUmemAttach_flags
CUDA Mem Attach Flags

                                 Values



CU_MEM_ATTACH_GLOBAL = 0x1
Memory can be accessed by any stream on any device
CU_MEM_ATTACH_HOST = 0x2
Memory cannot be accessed by any stream on any device
CU_MEM_ATTACH_SINGLE = 0x4
Memory can only be accessed by a single stream on the associated device

enum CUmemHandleType
Memory handle types

                                 Values



CU_MEM_HANDLE_TYPE_GENERIC = 0

enum CUmemLocationType
Specifies the type of location

                                 Values



CU_MEM_LOCATION_TYPE_INVALID = 0x0

CU_MEM_LOCATION_TYPE_NONE = 0x0
Location is unspecified. This is used when creating a managed memory pool to indicate no preferred location for the pool
CU_MEM_LOCATION_TYPE_DEVICE = 0x1
Location is a device location, thus id is a device ordinal
CU_MEM_LOCATION_TYPE_HOST = 0x2
Location is host, id is ignored
CU_MEM_LOCATION_TYPE_HOST_NUMA = 0x3
Location is a host NUMA node, thus id is a host NUMA node id
CU_MEM_LOCATION_TYPE_HOST_NUMA_CURRENT = 0x4
Location is a host NUMA node of the current thread, id is ignored
CU_MEM_LOCATION_TYPE_MAX = 0x7FFFFFFF

enum CUmemOperationType
Memory operation types

                                 Values



CU_MEM_OPERATION_TYPE_MAP = 1

CU_MEM_OPERATION_TYPE_UNMAP = 2

enum CUmemPool_attribute
CUDA memory pool attributes

                                 Values



CU_MEMPOOL_ATTR_REUSE_FOLLOW_EVENT_DEPENDENCIES = 1
(value type = int) Allow cuMemAllocAsync to use memory asynchronously freed in another streams as long as a stream ordering
                                    dependency of the allocating stream on the free action exists. Cuda events and null stream interactions can create the required
                                    stream ordered dependencies. (default enabled)

CU_MEMPOOL_ATTR_REUSE_ALLOW_OPPORTUNISTIC
(value type = int) Allow reuse of already completed frees when there is no dependency between the free and allocation. (default
                                    enabled)

CU_MEMPOOL_ATTR_REUSE_ALLOW_INTERNAL_DEPENDENCIES
(value type = int) Allow cuMemAllocAsync to insert new stream dependencies in order to establish the stream ordering required
                                    to reuse a piece of memory released by cuMemFreeAsync (default enabled).

CU_MEMPOOL_ATTR_RELEASE_THRESHOLD
(value type = cuuint64_t) Amount of reserved memory in bytes to hold onto before trying to release memory back to the OS.
                                    When more than the release threshold bytes of memory are held by the memory pool, the allocator will try to release memory
                                    back to the OS on the next call to stream, event or context synchronize. (default 0)

CU_MEMPOOL_ATTR_RESERVED_MEM_CURRENT
(value type = cuuint64_t) Amount of backing memory currently allocated for the mempool.
CU_MEMPOOL_ATTR_RESERVED_MEM_HIGH
(value type = cuuint64_t) High watermark of backing memory allocated for the mempool since the last time it was reset. High
                                    watermark can only be reset to zero.

CU_MEMPOOL_ATTR_USED_MEM_CURRENT
(value type = cuuint64_t) Amount of memory from the pool that is currently in use by the application.
CU_MEMPOOL_ATTR_USED_MEM_HIGH
(value type = cuuint64_t) High watermark of the amount of memory from the pool that was in use by the application since the
                                    last time it was reset. High watermark can only be reset to zero.

enum CUmemRangeFlags
Flag for requesting handle type for address range.

                                 Values



CU_MEM_RANGE_FLAG_DMA_BUF_MAPPING_TYPE_PCIE = 0x1
Indicates that DMA_BUF handle should be mapped via PCIe BAR1

enum CUmemRangeHandleType
Specifies the handle type for address range

                                 Values



CU_MEM_RANGE_HANDLE_TYPE_DMA_BUF_FD = 0x1

CU_MEM_RANGE_HANDLE_TYPE_MAX = 0x7FFFFFFF

enum CUmem_advise
Memory advise values

                                 Values



CU_MEM_ADVISE_SET_READ_MOSTLY = 1
Data will mostly be read and only occasionally be written to
CU_MEM_ADVISE_UNSET_READ_MOSTLY = 2
Undo the effect of CU_MEM_ADVISE_SET_READ_MOSTLY

CU_MEM_ADVISE_SET_PREFERRED_LOCATION = 3
Set the preferred location for the data as the specified device
CU_MEM_ADVISE_UNSET_PREFERRED_LOCATION = 4
Clear the preferred location for the data
CU_MEM_ADVISE_SET_ACCESSED_BY = 5
Data will be accessed by the specified device, so prevent page faults as much as possible
CU_MEM_ADVISE_UNSET_ACCESSED_BY = 6
Let the Unified Memory subsystem decide on the page faulting policy for the specified device

enum CUmemcpy3DOperandType
These flags allow applications to convey the operand type for individual copies specified in cuMemcpy3DBatchAsync.


                                 Values



CU_MEMCPY_OPERAND_TYPE_POINTER = 0x1
Memcpy operand is a valid pointer.
CU_MEMCPY_OPERAND_TYPE_ARRAY = 0x2
Memcpy operand is a CUarray.
CU_MEMCPY_OPERAND_TYPE_MAX = 0x7FFFFFFF

enum CUmemcpyFlags
Flags to specify for copies within a batch. For more details see cuMemcpyBatchAsync.


                                 Values



CU_MEMCPY_FLAG_DEFAULT = 0x0

CU_MEMCPY_FLAG_PREFER_OVERLAP_WITH_COMPUTE = 0x1
Hint to the driver to try and overlap the copy with compute work on the SMs.

enum CUmemcpySrcAccessOrder
These flags allow applications to convey the source access ordering CUDA must maintain. The destination will always be accessed
                                 in stream order.


                                 Values



CU_MEMCPY_SRC_ACCESS_ORDER_INVALID = 0x0
Default invalid.
CU_MEMCPY_SRC_ACCESS_ORDER_STREAM = 0x1
Indicates that access to the source pointer must be in stream order.
CU_MEMCPY_SRC_ACCESS_ORDER_DURING_API_CALL = 0x2
Indicates that access to the source pointer can be out of stream order and all accesses must be complete before the API call
                                    returns. This flag is suited for ephemeral sources (ex., stack variables) when it's known that no prior operations in the
                                    stream can be accessing the memory and also that the lifetime of the memory is limited to the scope that the source variable
                                    was declared in. Specifying this flag allows the driver to optimize the copy and removes the need for the user to synchronize
                                    the stream after the API call.

CU_MEMCPY_SRC_ACCESS_ORDER_ANY = 0x3
Indicates that access to the source pointer can be out of stream order and the accesses can happen even after the API call
                                    returns. This flag is suited for host pointers allocated outside CUDA (ex., via malloc) when it's known that no prior operations
                                    in the stream can be accessing the memory. Specifying this flag allows the driver to optimize the copy on certain platforms.


CU_MEMCPY_SRC_ACCESS_ORDER_MAX = 0x7FFFFFFF

enum CUmemorytype
Memory types

                                 Values



CU_MEMORYTYPE_HOST = 0x01
Host memory
CU_MEMORYTYPE_DEVICE = 0x02
Device memory
CU_MEMORYTYPE_ARRAY = 0x03
Array memory
CU_MEMORYTYPE_UNIFIED = 0x04
Unified device or host memory

enum CUmulticastGranularity_flags
Flags for querying different granularities for a multicast object

                                 Values



CU_MULTICAST_GRANULARITY_MINIMUM = 0x0
Minimum required granularity
CU_MULTICAST_GRANULARITY_RECOMMENDED = 0x1
Recommended granularity for best performance

enum CUoccupancy_flags
Occupancy calculator flag

                                 Values



CU_OCCUPANCY_DEFAULT = 0x0
Default behavior
CU_OCCUPANCY_DISABLE_CACHING_OVERRIDE = 0x1
Assume global caching is enabled and cannot be automatically turned off

enum CUpointer_attribute
Pointer information

                                 Values



CU_POINTER_ATTRIBUTE_CONTEXT = 1
The CUcontext on which a pointer was allocated or registered

CU_POINTER_ATTRIBUTE_MEMORY_TYPE = 2
The CUmemorytype describing the physical location of a pointer

CU_POINTER_ATTRIBUTE_DEVICE_POINTER = 3
The address at which a pointer's memory may be accessed on the device
CU_POINTER_ATTRIBUTE_HOST_POINTER = 4
The address at which a pointer's memory may be accessed on the host
CU_POINTER_ATTRIBUTE_P2P_TOKENS = 5
A pair of tokens for use with the nv-p2p.h Linux kernel interface
CU_POINTER_ATTRIBUTE_SYNC_MEMOPS = 6
Synchronize every synchronous memory operation initiated on this region
CU_POINTER_ATTRIBUTE_BUFFER_ID = 7
A process-wide unique ID for an allocated memory region
CU_POINTER_ATTRIBUTE_IS_MANAGED = 8
Indicates if the pointer points to managed memory
CU_POINTER_ATTRIBUTE_DEVICE_ORDINAL = 9
A device ordinal of a device on which a pointer was allocated or registered
CU_POINTER_ATTRIBUTE_IS_LEGACY_CUDA_IPC_CAPABLE = 10
1 if this pointer maps to an allocation that is suitable for cudaIpcGetMemHandle, 0 otherwise

CU_POINTER_ATTRIBUTE_RANGE_START_ADDR = 11
Starting address for this requested pointer
CU_POINTER_ATTRIBUTE_RANGE_SIZE = 12
Size of the address range for this requested pointer
CU_POINTER_ATTRIBUTE_MAPPED = 13
1 if this pointer is in a valid address range that is mapped to a backing allocation, 0 otherwise
CU_POINTER_ATTRIBUTE_ALLOWED_HANDLE_TYPES = 14
Bitmask of allowed CUmemAllocationHandleType for this allocation

CU_POINTER_ATTRIBUTE_IS_GPU_DIRECT_RDMA_CAPABLE = 15
1 if the memory this pointer is referencing can be used with the GPUDirect RDMA API
CU_POINTER_ATTRIBUTE_ACCESS_FLAGS = 16
Returns the access flags the device associated with the current context has on the corresponding memory referenced by the
                                    pointer given

CU_POINTER_ATTRIBUTE_MEMPOOL_HANDLE = 17
Returns the mempool handle for the allocation if it was allocated from a mempool. Otherwise returns NULL.
CU_POINTER_ATTRIBUTE_MAPPING_SIZE = 18
Size of the actual underlying mapping that the pointer belongs to
CU_POINTER_ATTRIBUTE_MAPPING_BASE_ADDR = 19
The start address of the mapping that the pointer belongs to
CU_POINTER_ATTRIBUTE_MEMORY_BLOCK_ID = 20
A process-wide unique id corresponding to the physical allocation the pointer belongs to
CU_POINTER_ATTRIBUTE_IS_HW_DECOMPRESS_CAPABLE = 21
Returns in *data a boolean that indicates whether the pointer points to memory that is capable to be used for hardware accelerated decompression.

enum CUprocessState
CUDA Process States

                                 Values



CU_PROCESS_STATE_RUNNING = 0
Default process state
CU_PROCESS_STATE_LOCKED
CUDA API locks are taken so further CUDA API calls will block
CU_PROCESS_STATE_CHECKPOINTED
Application memory contents have been checkpointed and underlying allocations and device handles have been released
CU_PROCESS_STATE_FAILED
Application entered an uncorrectable error during the checkpoint/restore process

enum CUresourceViewFormat
Resource view format

                                 Values



CU_RES_VIEW_FORMAT_NONE = 0x00
No resource view format (use underlying resource format)
CU_RES_VIEW_FORMAT_UINT_1X8 = 0x01
1 channel unsigned 8-bit integers
CU_RES_VIEW_FORMAT_UINT_2X8 = 0x02
2 channel unsigned 8-bit integers
CU_RES_VIEW_FORMAT_UINT_4X8 = 0x03
4 channel unsigned 8-bit integers
CU_RES_VIEW_FORMAT_SINT_1X8 = 0x04
1 channel signed 8-bit integers
CU_RES_VIEW_FORMAT_SINT_2X8 = 0x05
2 channel signed 8-bit integers
CU_RES_VIEW_FORMAT_SINT_4X8 = 0x06
4 channel signed 8-bit integers
CU_RES_VIEW_FORMAT_UINT_1X16 = 0x07
1 channel unsigned 16-bit integers
CU_RES_VIEW_FORMAT_UINT_2X16 = 0x08
2 channel unsigned 16-bit integers
CU_RES_VIEW_FORMAT_UINT_4X16 = 0x09
4 channel unsigned 16-bit integers
CU_RES_VIEW_FORMAT_SINT_1X16 = 0x0a
1 channel signed 16-bit integers
CU_RES_VIEW_FORMAT_SINT_2X16 = 0x0b
2 channel signed 16-bit integers
CU_RES_VIEW_FORMAT_SINT_4X16 = 0x0c
4 channel signed 16-bit integers
CU_RES_VIEW_FORMAT_UINT_1X32 = 0x0d
1 channel unsigned 32-bit integers
CU_RES_VIEW_FORMAT_UINT_2X32 = 0x0e
2 channel unsigned 32-bit integers
CU_RES_VIEW_FORMAT_UINT_4X32 = 0x0f
4 channel unsigned 32-bit integers
CU_RES_VIEW_FORMAT_SINT_1X32 = 0x10
1 channel signed 32-bit integers
CU_RES_VIEW_FORMAT_SINT_2X32 = 0x11
2 channel signed 32-bit integers
CU_RES_VIEW_FORMAT_SINT_4X32 = 0x12
4 channel signed 32-bit integers
CU_RES_VIEW_FORMAT_FLOAT_1X16 = 0x13
1 channel 16-bit floating point
CU_RES_VIEW_FORMAT_FLOAT_2X16 = 0x14
2 channel 16-bit floating point
CU_RES_VIEW_FORMAT_FLOAT_4X16 = 0x15
4 channel 16-bit floating point
CU_RES_VIEW_FORMAT_FLOAT_1X32 = 0x16
1 channel 32-bit floating point
CU_RES_VIEW_FORMAT_FLOAT_2X32 = 0x17
2 channel 32-bit floating point
CU_RES_VIEW_FORMAT_FLOAT_4X32 = 0x18
4 channel 32-bit floating point
CU_RES_VIEW_FORMAT_UNSIGNED_BC1 = 0x19
Block compressed 1
CU_RES_VIEW_FORMAT_UNSIGNED_BC2 = 0x1a
Block compressed 2
CU_RES_VIEW_FORMAT_UNSIGNED_BC3 = 0x1b
Block compressed 3
CU_RES_VIEW_FORMAT_UNSIGNED_BC4 = 0x1c
Block compressed 4 unsigned
CU_RES_VIEW_FORMAT_SIGNED_BC4 = 0x1d
Block compressed 4 signed
CU_RES_VIEW_FORMAT_UNSIGNED_BC5 = 0x1e
Block compressed 5 unsigned
CU_RES_VIEW_FORMAT_SIGNED_BC5 = 0x1f
Block compressed 5 signed
CU_RES_VIEW_FORMAT_UNSIGNED_BC6H = 0x20
Block compressed 6 unsigned half-float
CU_RES_VIEW_FORMAT_SIGNED_BC6H = 0x21
Block compressed 6 signed half-float
CU_RES_VIEW_FORMAT_UNSIGNED_BC7 = 0x22
Block compressed 7

enum CUresourcetype
Resource types

                                 Values



CU_RESOURCE_TYPE_ARRAY = 0x00
Array resource
CU_RESOURCE_TYPE_MIPMAPPED_ARRAY = 0x01
Mipmapped array resource
CU_RESOURCE_TYPE_LINEAR = 0x02
Linear resource
CU_RESOURCE_TYPE_PITCH2D = 0x03
Pitch 2D resource

enum CUresult
Error codes

                                 Values



CUDA_SUCCESS = 0
The API call returned with no errors. In the case of query calls, this also means that the operation being queried is complete
                                    (see cuEventQuery() and cuStreamQuery()).

CUDA_ERROR_INVALID_VALUE = 1
This indicates that one or more of the parameters passed to the API call is not within an acceptable range of values.
CUDA_ERROR_OUT_OF_MEMORY = 2
The API call failed because it was unable to allocate enough memory or other resources to perform the requested operation.


CUDA_ERROR_NOT_INITIALIZED = 3
This indicates that the CUDA driver has not been initialized with cuInit() or that initialization has failed.

CUDA_ERROR_DEINITIALIZED = 4
This indicates that the CUDA driver is in the process of shutting down.
CUDA_ERROR_PROFILER_DISABLED = 5
This indicates profiler is not initialized for this run. This can happen when the application is running with external profiling
                                    tools like visual profiler.

CUDA_ERROR_PROFILER_NOT_INITIALIZED = 6

Deprecated
This error return is deprecated as of CUDA 5.0. It is no longer an error to attempt to enable/disable the profiling via cuProfilerStart or cuProfilerStop without initialization.

CUDA_ERROR_PROFILER_ALREADY_STARTED = 7

Deprecated
This error return is deprecated as of CUDA 5.0. It is no longer an error to call cuProfilerStart() when profiling is already enabled.

CUDA_ERROR_PROFILER_ALREADY_STOPPED = 8

Deprecated
This error return is deprecated as of CUDA 5.0. It is no longer an error to call cuProfilerStop() when profiling is already disabled.

CUDA_ERROR_STUB_LIBRARY = 34
This indicates that the CUDA driver that the application has loaded is a stub library. Applications that run with the stub
                                    rather than a real driver loaded will result in CUDA API returning this error.

CUDA_ERROR_CALL_REQUIRES_NEWER_DRIVER = 36
This indicates that the API call requires a newer CUDA driver than the one currently installed. Users should install an updated
                                    NVIDIA CUDA driver to allow the API call to succeed.

CUDA_ERROR_DEVICE_UNAVAILABLE = 46
This indicates that requested CUDA device is unavailable at the current time. Devices are often unavailable due to use of
                                    CU_COMPUTEMODE_EXCLUSIVE_PROCESS or CU_COMPUTEMODE_PROHIBITED.

CUDA_ERROR_NO_DEVICE = 100
This indicates that no CUDA-capable devices were detected by the installed CUDA driver.
CUDA_ERROR_INVALID_DEVICE = 101
This indicates that the device ordinal supplied by the user does not correspond to a valid CUDA device or that the action
                                    requested is invalid for the specified device.

CUDA_ERROR_DEVICE_NOT_LICENSED = 102
This error indicates that the Grid license is not applied.
CUDA_ERROR_INVALID_IMAGE = 200
This indicates that the device kernel image is invalid. This can also indicate an invalid CUDA module.
CUDA_ERROR_INVALID_CONTEXT = 201
This most frequently indicates that there is no context bound to the current thread. This can also be returned if the context
                                    passed to an API call is not a valid handle (such as a context that has had cuCtxDestroy() invoked on it). This can also be returned if a user mixes different API versions (i.e. 3010 context with 3020 API calls).
                                    See cuCtxGetApiVersion() for more details. This can also be returned if the green context passed to an API call was not converted to a CUcontext using cuCtxFromGreenCtx API.

CUDA_ERROR_CONTEXT_ALREADY_CURRENT = 202

Deprecated
This error return is deprecated as of CUDA 3.2. It is no longer an error to attempt to push the active context via cuCtxPushCurrent().
This indicated that the context being supplied as a parameter to the API call was already the active context.



CUDA_ERROR_MAP_FAILED = 205
This indicates that a map or register operation has failed.
CUDA_ERROR_UNMAP_FAILED = 206
This indicates that an unmap or unregister operation has failed.
CUDA_ERROR_ARRAY_IS_MAPPED = 207
This indicates that the specified array is currently mapped and thus cannot be destroyed.
CUDA_ERROR_ALREADY_MAPPED = 208
This indicates that the resource is already mapped.
CUDA_ERROR_NO_BINARY_FOR_GPU = 209
This indicates that there is no kernel image available that is suitable for the device. This can occur when a user specifies
                                    code generation options for a particular CUDA source file that do not include the corresponding device configuration.

CUDA_ERROR_ALREADY_ACQUIRED = 210
This indicates that a resource has already been acquired.
CUDA_ERROR_NOT_MAPPED = 211
This indicates that a resource is not mapped.
CUDA_ERROR_NOT_MAPPED_AS_ARRAY = 212
This indicates that a mapped resource is not available for access as an array.
CUDA_ERROR_NOT_MAPPED_AS_POINTER = 213
This indicates that a mapped resource is not available for access as a pointer.
CUDA_ERROR_ECC_UNCORRECTABLE = 214
This indicates that an uncorrectable ECC error was detected during execution.
CUDA_ERROR_UNSUPPORTED_LIMIT = 215
This indicates that the CUlimit passed to the API call is not supported by the active device.

CUDA_ERROR_CONTEXT_ALREADY_IN_USE = 216
This indicates that the CUcontext passed to the API call can only be bound to a single CPU thread at a time but is already bound to a CPU thread.

CUDA_ERROR_PEER_ACCESS_UNSUPPORTED = 217
This indicates that peer access is not supported across the given devices.
CUDA_ERROR_INVALID_PTX = 218
This indicates that a PTX JIT compilation failed.
CUDA_ERROR_INVALID_GRAPHICS_CONTEXT = 219
This indicates an error with OpenGL or DirectX context.
CUDA_ERROR_NVLINK_UNCORRECTABLE = 220
This indicates that an uncorrectable NVLink error was detected during the execution.
CUDA_ERROR_JIT_COMPILER_NOT_FOUND = 221
This indicates that the PTX JIT compiler library was not found.
CUDA_ERROR_UNSUPPORTED_PTX_VERSION = 222
This indicates that the provided PTX was compiled with an unsupported toolchain.
CUDA_ERROR_JIT_COMPILATION_DISABLED = 223
This indicates that the PTX JIT compilation was disabled.
CUDA_ERROR_UNSUPPORTED_EXEC_AFFINITY = 224
This indicates that the CUexecAffinityType passed to the API call is not supported by the active device.

CUDA_ERROR_UNSUPPORTED_DEVSIDE_SYNC = 225
This indicates that the code to be compiled by the PTX JIT contains unsupported call to cudaDeviceSynchronize.
CUDA_ERROR_CONTAINED = 226
This indicates that an exception occurred on the device that is now contained by the GPU's error containment capability. Common
                                    causes are - a. Certain types of invalid accesses of peer GPU memory over nvlink b. Certain classes of hardware errors This
                                    leaves the process in an inconsistent state and any further CUDA work will return the same error. To continue using CUDA,
                                    the process must be terminated and relaunched.

CUDA_ERROR_INVALID_SOURCE = 300
This indicates that the device kernel source is invalid. This includes compilation/linker errors encountered in device code
                                    or user error.

CUDA_ERROR_FILE_NOT_FOUND = 301
This indicates that the file specified was not found.
CUDA_ERROR_SHARED_OBJECT_SYMBOL_NOT_FOUND = 302
This indicates that a link to a shared object failed to resolve.
CUDA_ERROR_SHARED_OBJECT_INIT_FAILED = 303
This indicates that initialization of a shared object failed.
CUDA_ERROR_OPERATING_SYSTEM = 304
This indicates that an OS call failed.
CUDA_ERROR_INVALID_HANDLE = 400
This indicates that a resource handle passed to the API call was not valid. Resource handles are opaque types like CUstream and CUevent.

CUDA_ERROR_ILLEGAL_STATE = 401
This indicates that a resource required by the API call is not in a valid state to perform the requested operation.
CUDA_ERROR_LOSSY_QUERY = 402
This indicates an attempt was made to introspect an object in a way that would discard semantically important information.
                                    This is either due to the object using funtionality newer than the API version used to introspect it or omission of optional
                                    return arguments.

CUDA_ERROR_NOT_FOUND = 500
This indicates that a named symbol was not found. Examples of symbols are global/constant variable names, driver function
                                    names, texture names, and surface names.

CUDA_ERROR_NOT_READY = 600
This indicates that asynchronous operations issued previously have not completed yet. This result is not actually an error,
                                    but must be indicated differently than CUDA_SUCCESS (which indicates completion). Calls that may return this value include cuEventQuery() and cuStreamQuery().

CUDA_ERROR_ILLEGAL_ADDRESS = 700
While executing a kernel, the device encountered a load or store instruction on an invalid memory address. This leaves the
                                    process in an inconsistent state and any further CUDA work will return the same error. To continue using CUDA, the process
                                    must be terminated and relaunched.

CUDA_ERROR_LAUNCH_OUT_OF_RESOURCES = 701
This indicates that a launch did not occur because it did not have appropriate resources. This error usually indicates that
                                    the user has attempted to pass too many arguments to the device kernel, or the kernel launch specifies too many threads for
                                    the kernel's register count. Passing arguments of the wrong size (i.e. a 64-bit pointer when a 32-bit int is expected) is
                                    equivalent to passing too many arguments and can also result in this error.

CUDA_ERROR_LAUNCH_TIMEOUT = 702
This indicates that the device kernel took too long to execute. This can only occur if timeouts are enabled - see the device
                                    attribute CU_DEVICE_ATTRIBUTE_KERNEL_EXEC_TIMEOUT for more information. This leaves the process in an inconsistent state and any further CUDA work will return the same error.
                                    To continue using CUDA, the process must be terminated and relaunched.

CUDA_ERROR_LAUNCH_INCOMPATIBLE_TEXTURING = 703
This error indicates a kernel launch that uses an incompatible texturing mode.
CUDA_ERROR_PEER_ACCESS_ALREADY_ENABLED = 704
This error indicates that a call to cuCtxEnablePeerAccess() is trying to re-enable peer access to a context which has already had peer access to it enabled.

CUDA_ERROR_PEER_ACCESS_NOT_ENABLED = 705
This error indicates that cuCtxDisablePeerAccess() is trying to disable peer access which has not been enabled yet via cuCtxEnablePeerAccess().

CUDA_ERROR_PRIMARY_CONTEXT_ACTIVE = 708
This error indicates that the primary context for the specified device has already been initialized.
CUDA_ERROR_CONTEXT_IS_DESTROYED = 709
This error indicates that the context current to the calling thread has been destroyed using cuCtxDestroy, or is a primary context which has not yet been initialized.

CUDA_ERROR_ASSERT = 710
A device-side assert triggered during kernel execution. The context cannot be used anymore, and must be destroyed. All existing
                                    device memory allocations from this context are invalid and must be reconstructed if the program is to continue using CUDA.


CUDA_ERROR_TOO_MANY_PEERS = 711
This error indicates that the hardware resources required to enable peer access have been exhausted for one or more of the
                                    devices passed to cuCtxEnablePeerAccess().

CUDA_ERROR_HOST_MEMORY_ALREADY_REGISTERED = 712
This error indicates that the memory range passed to cuMemHostRegister() has already been registered.

CUDA_ERROR_HOST_MEMORY_NOT_REGISTERED = 713
This error indicates that the pointer passed to cuMemHostUnregister() does not correspond to any currently registered memory region.

CUDA_ERROR_HARDWARE_STACK_ERROR = 714
While executing a kernel, the device encountered a stack error. This can be due to stack corruption or exceeding the stack
                                    size limit. This leaves the process in an inconsistent state and any further CUDA work will return the same error. To continue
                                    using CUDA, the process must be terminated and relaunched.

CUDA_ERROR_ILLEGAL_INSTRUCTION = 715
While executing a kernel, the device encountered an illegal instruction. This leaves the process in an inconsistent state
                                    and any further CUDA work will return the same error. To continue using CUDA, the process must be terminated and relaunched.


CUDA_ERROR_MISALIGNED_ADDRESS = 716
While executing a kernel, the device encountered a load or store instruction on a memory address which is not aligned. This
                                    leaves the process in an inconsistent state and any further CUDA work will return the same error. To continue using CUDA,
                                    the process must be terminated and relaunched.

CUDA_ERROR_INVALID_ADDRESS_SPACE = 717
While executing a kernel, the device encountered an instruction which can only operate on memory locations in certain address
                                    spaces (global, shared, or local), but was supplied a memory address not belonging to an allowed address space. This leaves
                                    the process in an inconsistent state and any further CUDA work will return the same error. To continue using CUDA, the process
                                    must be terminated and relaunched.

CUDA_ERROR_INVALID_PC = 718
While executing a kernel, the device program counter wrapped its address space. This leaves the process in an inconsistent
                                    state and any further CUDA work will return the same error. To continue using CUDA, the process must be terminated and relaunched.


CUDA_ERROR_LAUNCH_FAILED = 719
An exception occurred on the device while executing a kernel. Common causes include dereferencing an invalid device pointer
                                    and accessing out of bounds shared memory. Less common cases can be system specific - more information about these cases can
                                    be found in the system specific user guide. This leaves the process in an inconsistent state and any further CUDA work will
                                    return the same error. To continue using CUDA, the process must be terminated and relaunched.

CUDA_ERROR_COOPERATIVE_LAUNCH_TOO_LARGE = 720
This error indicates that the number of blocks launched per grid for a kernel that was launched via either cuLaunchCooperativeKernel or cuLaunchCooperativeKernelMultiDevice exceeds the maximum number of blocks as allowed by cuOccupancyMaxActiveBlocksPerMultiprocessor or cuOccupancyMaxActiveBlocksPerMultiprocessorWithFlags times the number of multiprocessors as specified by the device attribute CU_DEVICE_ATTRIBUTE_MULTIPROCESSOR_COUNT.

CUDA_ERROR_TENSOR_MEMORY_LEAK = 721
An exception occurred on the device while exiting a kernel using tensor memory: the tensor memory was not completely deallocated.
                                    This leaves the process in an inconsistent state and any further CUDA work will return the same error. To continue using CUDA,
                                    the process must be terminated and relaunched.

CUDA_ERROR_NOT_PERMITTED = 800
This error indicates that the attempted operation is not permitted.
CUDA_ERROR_NOT_SUPPORTED = 801
This error indicates that the attempted operation is not supported on the current system or device.
CUDA_ERROR_SYSTEM_NOT_READY = 802
This error indicates that the system is not yet ready to start any CUDA work. To continue using CUDA, verify the system configuration
                                    is in a valid state and all required driver daemons are actively running. More information about this error can be found in
                                    the system specific user guide.

CUDA_ERROR_SYSTEM_DRIVER_MISMATCH = 803
This error indicates that there is a mismatch between the versions of the display driver and the CUDA driver. Refer to the
                                    compatibility documentation for supported versions.

CUDA_ERROR_COMPAT_NOT_SUPPORTED_ON_DEVICE = 804
This error indicates that the system was upgraded to run with forward compatibility but the visible hardware detected by CUDA
                                    does not support this configuration. Refer to the compatibility documentation for the supported hardware matrix or ensure
                                    that only supported hardware is visible during initialization via the CUDA_VISIBLE_DEVICES environment variable.

CUDA_ERROR_MPS_CONNECTION_FAILED = 805
This error indicates that the MPS client failed to connect to the MPS control daemon or the MPS server.
CUDA_ERROR_MPS_RPC_FAILURE = 806
This error indicates that the remote procedural call between the MPS server and the MPS client failed.
CUDA_ERROR_MPS_SERVER_NOT_READY = 807
This error indicates that the MPS server is not ready to accept new MPS client requests. This error can be returned when the
                                    MPS server is in the process of recovering from a fatal failure.

CUDA_ERROR_MPS_MAX_CLIENTS_REACHED = 808
This error indicates that the hardware resources required to create MPS client have been exhausted.
CUDA_ERROR_MPS_MAX_CONNECTIONS_REACHED = 809
This error indicates the the hardware resources required to support device connections have been exhausted.
CUDA_ERROR_MPS_CLIENT_TERMINATED = 810
This error indicates that the MPS client has been terminated by the server. To continue using CUDA, the process must be terminated
                                    and relaunched.

CUDA_ERROR_CDP_NOT_SUPPORTED = 811
This error indicates that the module is using CUDA Dynamic Parallelism, but the current configuration, like MPS, does not
                                    support it.

CUDA_ERROR_CDP_VERSION_MISMATCH = 812
This error indicates that a module contains an unsupported interaction between different versions of CUDA Dynamic Parallelism.


CUDA_ERROR_STREAM_CAPTURE_UNSUPPORTED = 900
This error indicates that the operation is not permitted when the stream is capturing.
CUDA_ERROR_STREAM_CAPTURE_INVALIDATED = 901
This error indicates that the current capture sequence on the stream has been invalidated due to a previous error.
CUDA_ERROR_STREAM_CAPTURE_MERGE = 902
This error indicates that the operation would have resulted in a merge of two independent capture sequences.
CUDA_ERROR_STREAM_CAPTURE_UNMATCHED = 903
This error indicates that the capture was not initiated in this stream.
CUDA_ERROR_STREAM_CAPTURE_UNJOINED = 904
This error indicates that the capture sequence contains a fork that was not joined to the primary stream.
CUDA_ERROR_STREAM_CAPTURE_ISOLATION = 905
This error indicates that a dependency would have been created which crosses the capture sequence boundary. Only implicit
                                    in-stream ordering dependencies are allowed to cross the boundary.

CUDA_ERROR_STREAM_CAPTURE_IMPLICIT = 906
This error indicates a disallowed implicit dependency on a current capture sequence from cudaStreamLegacy.
CUDA_ERROR_CAPTURED_EVENT = 907
This error indicates that the operation is not permitted on an event which was last recorded in a capturing stream.
CUDA_ERROR_STREAM_CAPTURE_WRONG_THREAD = 908
A stream capture sequence not initiated with the CU_STREAM_CAPTURE_MODE_RELAXED argument to cuStreamBeginCapture was passed to cuStreamEndCapture in a different thread.

CUDA_ERROR_TIMEOUT = 909
This error indicates that the timeout specified for the wait operation has lapsed.
CUDA_ERROR_GRAPH_EXEC_UPDATE_FAILURE = 910
This error indicates that the graph update was not performed because it included changes which violated constraints specific
                                    to instantiated graph update.

CUDA_ERROR_EXTERNAL_DEVICE = 911
This indicates that an async error has occurred in a device outside of CUDA. If CUDA was waiting for an external device's
                                    signal before consuming shared data, the external device signaled an error indicating that the data is not valid for consumption.
                                    This leaves the process in an inconsistent state and any further CUDA work will return the same error. To continue using CUDA,
                                    the process must be terminated and relaunched.

CUDA_ERROR_INVALID_CLUSTER_SIZE = 912
Indicates a kernel launch error due to cluster misconfiguration.
CUDA_ERROR_FUNCTION_NOT_LOADED = 913
Indiciates a function handle is not loaded when calling an API that requires a loaded function.
CUDA_ERROR_INVALID_RESOURCE_TYPE = 914
This error indicates one or more resources passed in are not valid resource types for the operation.
CUDA_ERROR_INVALID_RESOURCE_CONFIGURATION = 915
This error indicates one or more resources are insufficient or non-applicable for the operation.
CUDA_ERROR_KEY_ROTATION = 916
This error indicates that an error happened during the key rotation sequence.
CUDA_ERROR_STREAM_DETACHED = 917
This error indicates that the requested operation is not permitted because the stream is in a detached state. This can occur
                                    if the green context associated with the stream has been destroyed, limiting the stream's operational capabilities.

CUDA_ERROR_UNKNOWN = 999
This indicates that an unknown internal error has occurred.

enum CUshared_carveout
Shared memory carveout configurations. These may be passed to cuFuncSetAttribute or cuKernelSetAttribute

                                 Values



CU_SHAREDMEM_CARVEOUT_DEFAULT = -1
No preference for shared memory or L1 (default)
CU_SHAREDMEM_CARVEOUT_MAX_SHARED = 100
Prefer maximum available shared memory, minimum L1 cache
CU_SHAREDMEM_CARVEOUT_MAX_L1 = 0
Prefer maximum available L1 cache, minimum shared memory

enum CUsharedconfig
Deprecated
Shared memory configurations


                                 Values



CU_SHARED_MEM_CONFIG_DEFAULT_BANK_SIZE = 0x00
set default shared memory bank size
CU_SHARED_MEM_CONFIG_FOUR_BYTE_BANK_SIZE = 0x01
set shared memory bank width to four bytes
CU_SHARED_MEM_CONFIG_EIGHT_BYTE_BANK_SIZE = 0x02
set shared memory bank width to eight bytes

enum CUstreamAtomicReductionDataType
Atomic reduction data types for CUstreamBatchMemOpParams::atomicReduction::dataType

                                 Values



CU_STREAM_ATOMIC_REDUCTION_UNSIGNED_32 = CU_ATOMIC_CAPABILITY_UNSIGNED|CU_ATOMIC_CAPABILITY_SCALAR_32|CU_ATOMIC_CAPABILITY_REDUCTION

CU_STREAM_ATOMIC_REDUCTION_UNSIGNED_64 = CU_ATOMIC_CAPABILITY_UNSIGNED|CU_ATOMIC_CAPABILITY_SCALAR_64|CU_ATOMIC_CAPABILITY_REDUCTION

enum CUstreamAtomicReductionOpType
Atomic reduction operation types for CUstreamBatchMemOpParams::atomicReduction::reductionOp

                                 Values



CU_STREAM_ATOMIC_REDUCTION_OP_OR = CU_ATOMIC_OPERATION_OR
Performs an atomic OR: *(address) = *(address) | value
CU_STREAM_ATOMIC_REDUCTION_OP_AND = CU_ATOMIC_OPERATION_AND
Performs an atomic AND: *(address) = *(address) & value
CU_STREAM_ATOMIC_REDUCTION_OP_ADD = CU_ATOMIC_OPERATION_INTEGER_ADD
Performs an atomic ADD: *(address) = *(address) + value

enum CUstreamBatchMemOpType
Operations for cuStreamBatchMemOp

                                 Values



CU_STREAM_MEM_OP_WAIT_VALUE_32 = 1
Represents a cuStreamWaitValue32 operation

CU_STREAM_MEM_OP_WRITE_VALUE_32 = 2
Represents a cuStreamWriteValue32 operation

CU_STREAM_MEM_OP_WAIT_VALUE_64 = 4
Represents a cuStreamWaitValue64 operation

CU_STREAM_MEM_OP_WRITE_VALUE_64 = 5
Represents a cuStreamWriteValue64 operation

CU_STREAM_MEM_OP_BARRIER = 6
Insert a memory barrier of the specified type
CU_STREAM_MEM_OP_ATOMIC_REDUCTION = 8
Perform a atomic reduction. See CUstreamBatchMemOpParams::atomicReduction
CU_STREAM_MEM_OP_FLUSH_REMOTE_WRITES = 3
This has the same effect as CU_STREAM_WAIT_VALUE_FLUSH, but as a standalone operation.

enum CUstreamCaptureMode
Possible modes for stream capture thread interactions. For more details see cuStreamBeginCapture and cuThreadExchangeStreamCaptureMode

                                 Values



CU_STREAM_CAPTURE_MODE_GLOBAL = 0

CU_STREAM_CAPTURE_MODE_THREAD_LOCAL = 1

CU_STREAM_CAPTURE_MODE_RELAXED = 2

enum CUstreamCaptureStatus
Possible stream capture statuses returned by cuStreamIsCapturing

                                 Values



CU_STREAM_CAPTURE_STATUS_NONE = 0
Stream is not capturing
CU_STREAM_CAPTURE_STATUS_ACTIVE = 1
Stream is actively capturing
CU_STREAM_CAPTURE_STATUS_INVALIDATED = 2
Stream is part of a capture sequence that has been invalidated, but not terminated

enum CUstreamMemoryBarrier_flags
Flags for CUstreamBatchMemOpParams::memoryBarrier

                                 Values



CU_STREAM_MEMORY_BARRIER_TYPE_SYS = 0x0
System-wide memory barrier.
CU_STREAM_MEMORY_BARRIER_TYPE_GPU = 0x1
Limit memory barrier scope to the GPU.

enum CUstreamUpdateCaptureDependencies_flags
Flags for cuStreamUpdateCaptureDependencies

                                 Values



CU_STREAM_ADD_CAPTURE_DEPENDENCIES = 0x0
Add new nodes to the dependency set
CU_STREAM_SET_CAPTURE_DEPENDENCIES = 0x1
Replace the dependency set with the new nodes

enum CUstreamWaitValue_flags
Flags for cuStreamWaitValue32 and cuStreamWaitValue64

                                 Values



CU_STREAM_WAIT_VALUE_GEQ = 0x0
Wait until (int32_t)(*addr - value) >= 0 (or int64_t for 64 bit values). Note this is a cyclic comparison which ignores wraparound.
                                    (Default behavior.)

CU_STREAM_WAIT_VALUE_EQ = 0x1
Wait until *addr == value.
CU_STREAM_WAIT_VALUE_AND = 0x2
Wait until (*addr & value) != 0.
CU_STREAM_WAIT_VALUE_NOR = 0x3
Wait until ~(*addr | value) != 0. Support for this operation can be queried with cuDeviceGetAttribute() and CU_DEVICE_ATTRIBUTE_CAN_USE_STREAM_WAIT_VALUE_NOR.

CU_STREAM_WAIT_VALUE_FLUSH = 1<<30
Follow the wait operation with a flush of outstanding remote writes. This means that, if a remote write operation is guaranteed
                                    to have reached the device before the wait can be satisfied, that write is guaranteed to be visible to downstream device work.
                                    The device is permitted to reorder remote writes internally. For example, this flag would be required if two remote writes
                                    arrive in a defined order, the wait is satisfied by the second write, and downstream work needs to observe the first write.
                                    Support for this operation is restricted to selected platforms and can be queried with CU_DEVICE_ATTRIBUTE_CAN_FLUSH_REMOTE_WRITES.

enum CUstreamWriteValue_flags
Flags for cuStreamWriteValue32

                                 Values



CU_STREAM_WRITE_VALUE_DEFAULT = 0x0
Default behavior
CU_STREAM_WRITE_VALUE_NO_MEMORY_BARRIER = 0x1
Permits the write to be reordered with writes which were issued before it, as a performance optimization. Normally, cuStreamWriteValue32 will provide a memory fence before the write, which has similar semantics to __threadfence_system() but is scoped to the
                                    stream rather than a CUDA thread. This flag is not supported in the v2 API.

enum CUstream_flags
Stream creation flags

                                 Values



CU_STREAM_DEFAULT = 0x0
Default stream flag
CU_STREAM_NON_BLOCKING = 0x1
Stream does not synchronize with stream 0 (the NULL stream)

enum CUtensorMapDataType
Tensor map data type

                                 Values



CU_TENSOR_MAP_DATA_TYPE_UINT8 = 0

CU_TENSOR_MAP_DATA_TYPE_UINT16

CU_TENSOR_MAP_DATA_TYPE_UINT32

CU_TENSOR_MAP_DATA_TYPE_INT32

CU_TENSOR_MAP_DATA_TYPE_UINT64

CU_TENSOR_MAP_DATA_TYPE_INT64

CU_TENSOR_MAP_DATA_TYPE_FLOAT16

CU_TENSOR_MAP_DATA_TYPE_FLOAT32

CU_TENSOR_MAP_DATA_TYPE_FLOAT64

CU_TENSOR_MAP_DATA_TYPE_BFLOAT16

CU_TENSOR_MAP_DATA_TYPE_FLOAT32_FTZ

CU_TENSOR_MAP_DATA_TYPE_TFLOAT32

CU_TENSOR_MAP_DATA_TYPE_TFLOAT32_FTZ

CU_TENSOR_MAP_DATA_TYPE_16U4_ALIGN8B

CU_TENSOR_MAP_DATA_TYPE_16U4_ALIGN16B

CU_TENSOR_MAP_DATA_TYPE_16U6_ALIGN16B

enum CUtensorMapFloatOOBfill
Tensor map out-of-bounds fill type

                                 Values



CU_TENSOR_MAP_FLOAT_OOB_FILL_NONE = 0

CU_TENSOR_MAP_FLOAT_OOB_FILL_NAN_REQUEST_ZERO_FMA

enum CUtensorMapIm2ColWideMode
Tensor map Im2Col wide mode

                                 Values



CU_TENSOR_MAP_IM2COL_WIDE_MODE_W = 0

CU_TENSOR_MAP_IM2COL_WIDE_MODE_W128

enum CUtensorMapInterleave
Tensor map interleave layout type

                                 Values



CU_TENSOR_MAP_INTERLEAVE_NONE = 0

CU_TENSOR_MAP_INTERLEAVE_16B

CU_TENSOR_MAP_INTERLEAVE_32B

enum CUtensorMapL2promotion
Tensor map L2 promotion type

                                 Values



CU_TENSOR_MAP_L2_PROMOTION_NONE = 0

CU_TENSOR_MAP_L2_PROMOTION_L2_64B

CU_TENSOR_MAP_L2_PROMOTION_L2_128B

CU_TENSOR_MAP_L2_PROMOTION_L2_256B

enum CUtensorMapSwizzle
Tensor map swizzling mode of shared memory banks

                                 Values



CU_TENSOR_MAP_SWIZZLE_NONE = 0

CU_TENSOR_MAP_SWIZZLE_32B

CU_TENSOR_MAP_SWIZZLE_64B

CU_TENSOR_MAP_SWIZZLE_128B

CU_TENSOR_MAP_SWIZZLE_128B_ATOM_32B

CU_TENSOR_MAP_SWIZZLE_128B_ATOM_32B_FLIP_8B

CU_TENSOR_MAP_SWIZZLE_128B_ATOM_64B

enum CUuserObjectRetain_flags
Flags for retaining user object references for graphs

                                 Values



CU_GRAPH_USER_OBJECT_MOVE = 1
Transfer references from the caller rather than creating new references.

enum CUuserObject_flags
Flags for user objects for graphs

                                 Values



CU_USER_OBJECT_NO_DESTRUCTOR_SYNC = 1
Indicates the destructor execution is not synchronized by any CUDA handle.

enum cl_context_flags
NVCL context scheduling flags

                                 Values



NVCL_CTX_SCHED_AUTO = 0x00
Automatic scheduling
NVCL_CTX_SCHED_SPIN = 0x01
Set spin as default scheduling
NVCL_CTX_SCHED_YIELD = 0x02
Set yield as default scheduling
NVCL_CTX_SCHED_BLOCKING_SYNC = 0x04
Set blocking synchronization as default scheduling

enum cl_event_flags
NVCL event scheduling flags

                                 Values



NVCL_EVENT_SCHED_AUTO = 0x00
Automatic scheduling
NVCL_EVENT_SCHED_SPIN = 0x01
Set spin as default scheduling
NVCL_EVENT_SCHED_YIELD = 0x02
Set yield as default scheduling
NVCL_EVENT_SCHED_BLOCKING_SYNC = 0x04
Set blocking synchronization as default scheduling


---