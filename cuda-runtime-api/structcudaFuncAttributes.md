# CUDA Runtime API

[< Previous](structcudaExternalSemaphoreWaitParams.html) | [Next >](structcudaGraphEdgeData.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.30. cudaFuncAttributes Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


CUDA function attributes


### Public Variables


int  binaryVersionint  cacheModeCAint  clusterDimMustBeSetint  clusterSchedulingPolicyPreferencesize_t  constSizeBytessize_t  localSizeBytesint  maxDynamicSharedSizeBytesint  maxThreadsPerBlockint  nonPortableClusterSizeAllowedint  numRegsint  preferredShmemCarveoutint  ptxVersionint  requiredClusterWidthint  reserved[16]size_t  sharedSizeBytes

### Variables


int  cudaFuncAttributes::binaryVersion [inherited]
The binary architecture version for which the function was compiled. This value is the major binary version * 10 + the minor
                                 binary version, so a binary version 1.3 function would return the value 13.

int  cudaFuncAttributes::cacheModeCA [inherited]
The attribute to indicate whether the function has been compiled with user specified option "-Xptxas --dlcm=ca" set.

int  cudaFuncAttributes::clusterDimMustBeSet [inherited]
If this attribute is set, the kernel must launch with a valid cluster dimension specified.

int  cudaFuncAttributes::clusterSchedulingPolicyPreference [inherited]
The block scheduling policy of a function. See cudaFuncSetAttribute

size_t  cudaFuncAttributes::constSizeBytes [inherited]
The size in bytes of user-allocated constant memory required by this function.

size_t  cudaFuncAttributes::localSizeBytes [inherited]
The size in bytes of local memory used by each thread of this function.

int  cudaFuncAttributes::maxDynamicSharedSizeBytes [inherited]
The maximum size in bytes of dynamic shared memory per block for this function. Any launch must have a dynamic shared memory
                                 size smaller than this value.

int  cudaFuncAttributes::maxThreadsPerBlock [inherited]
The maximum number of threads per block, beyond which a launch of the function would fail. This number depends on both the
                                 function and the device on which the function is currently loaded.

int  cudaFuncAttributes::nonPortableClusterSizeAllowed [inherited]
Whether the function can be launched with non-portable cluster size. 1 is allowed, 0 is disallowed. A non-portable cluster
                                 size may only function on the specific SKUs the program is tested on. The launch might fail if the program is run on a different
                                 hardware platform.

CUDA API provides cudaOccupancyMaxActiveClusters to assist with checking whether the desired size can be launched on the current device.

Portable Cluster Size
A portable cluster size is guaranteed to be functional on all compute capabilities higher than the target compute capability.
                                 The portable cluster size for sm_90 is 8 blocks per cluster. This value may increase for future compute capabilities.

The specific hardware unit may support higher cluster sizes that’s not guaranteed to be portable. See cudaFuncSetAttribute

int  cudaFuncAttributes::numRegs [inherited]
The number of registers used by each thread of this function.

int  cudaFuncAttributes::preferredShmemCarveout [inherited]
On devices where the L1 cache and shared memory use the same hardware resources, this sets the shared memory carveout preference,
                                 in percent of the maximum shared memory. Refer to cudaDevAttrMaxSharedMemoryPerMultiprocessor. This is only a hint, and the driver can choose a different ratio if required to execute the function. See cudaFuncSetAttribute

int  cudaFuncAttributes::ptxVersion [inherited]
The PTX virtual architecture version for which the function was compiled. This value is the major PTX version * 10 + the
                                 minor PTX version, so a PTX version 1.3 function would return the value 13.

int  cudaFuncAttributes::requiredClusterWidth [inherited]
The required cluster width/height/depth in blocks. The values must either all be 0 or all be positive. The validity of the
                                 cluster dimensions is otherwise checked at launch time.

If the value is set during compile time, it cannot be set at runtime. Setting it at runtime should return cudaErrorNotPermitted.
                                 See cudaFuncSetAttribute

int  cudaFuncAttributes::reserved[16] [inherited]
Reserved for future use.

size_t  cudaFuncAttributes::sharedSizeBytes [inherited]
The size in bytes of statically-allocated shared memory per block required by this function. This does not include dynamically-allocated
                                 shared memory requested by the user at runtime.


---