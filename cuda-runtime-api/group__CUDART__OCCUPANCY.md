# CUDA Runtime API

[< Previous](group__CUDART__EXECUTION__DEPRECATED.html) | [Next >](group__CUDART__MEMORY.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 6.9. Occupancy


This section describes the occupancy calculation functions of the CUDA runtime application programming interface.


Besides the occupancy calculator functions ([cudaOccupancyMaxActiveBlocksPerMultiprocessor](group__CUDART__HIGHLEVEL.html#group__CUDART__HIGHLEVEL_1g5a5d67a3c907371559ba692195e8a38c) and [cudaOccupancyMaxActiveBlocksPerMultiprocessorWithFlags](group__CUDART__HIGHLEVEL.html#group__CUDART__HIGHLEVEL_1g603b86b20b37823253ff89fe8688ba83)), there are also C++ only occupancy-based launch configuration functions documented in [C++ API Routines](group__CUDART__HIGHLEVEL.html#group__CUDART__HIGHLEVEL) module.


See [cudaOccupancyMaxPotentialBlockSize ( C++ API)](group__CUDART__HIGHLEVEL.html#group__CUDART__HIGHLEVEL_1gee5334618ed4bb0871e4559a77643fc1), [cudaOccupancyMaxPotentialBlockSize ( C++ API)](group__CUDART__HIGHLEVEL.html#group__CUDART__HIGHLEVEL_1gd0524825c5c01bbc9a5e29e890745800), [cudaOccupancyMaxPotentialBlockSizeVariableSMem ( C++ API)](group__CUDART__HIGHLEVEL.html#group__CUDART__HIGHLEVEL_1g77b3bfb154b86e215a5bc01509ce8ea6), [cudaOccupancyMaxPotentialBlockSizeVariableSMem ( C++ API)](group__CUDART__HIGHLEVEL.html#group__CUDART__HIGHLEVEL_1g76975517a048cc199bc9e3ea6396ef26) cudaOccupancyAvailableDynamicSMemPerBlock (C++ API),


### Functions


__host__
                           ​cudaError_t cudaOccupancyAvailableDynamicSMemPerBlock (  size_t* dynamicSmemSize, const void* func, int  numBlocks, int  blockSize )
Returns dynamic shared memory available per block when launching numBlocks blocks on SM.

__host__
                           ​
                           __device__
                           ​cudaError_t cudaOccupancyMaxActiveBlocksPerMultiprocessor (  int* numBlocks, const void* func, int  blockSize, size_t dynamicSMemSize )
Returns occupancy for a device function.

__host__
                           ​cudaError_t cudaOccupancyMaxActiveBlocksPerMultiprocessorWithFlags (  int* numBlocks, const void* func, int  blockSize, size_t dynamicSMemSize, unsigned int  flags )
Returns occupancy for a device function with the specified flags.

__host__
                           ​cudaError_t cudaOccupancyMaxActiveClusters (  int* numClusters, const void* func, const cudaLaunchConfig_t* launchConfig )
Given the kernel function (func) and launch configuration (config), return the maximum number of clusters that could co-exist on the target device in *numClusters.

__host__
                           ​cudaError_t cudaOccupancyMaxPotentialClusterSize (  int* clusterSize, const void* func, const cudaLaunchConfig_t* launchConfig )
Given the kernel function (func) and launch configuration (config), return the maximum cluster size in *clusterSize.


### Functions


__host__
                              ​cudaError_t cudaOccupancyAvailableDynamicSMemPerBlock (  size_t* dynamicSmemSize, const void* func, int  numBlocks, int  blockSize )
Returns dynamic shared memory available per block when launching numBlocks blocks on SM.


                                 Parameters



dynamicSmemSize
- Returned maximum dynamic shared memory
func
- Kernel function for which occupancy is calculated
numBlocks
- Number of blocks to fit on SM
blockSize
- Size of the block

Returns
cudaSuccess, cudaErrorInvalidDevice, cudaErrorInvalidDeviceFunction, cudaErrorInvalidValue, cudaErrorUnknown,


Description
Returns in *dynamicSmemSize the maximum size of dynamic shared memory to allow numBlocks blocks per SM.


Note:

Note that this function may also return error codes from previous, asynchronous launches.

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


The API can also be used with a kernel cudaKernel_t by querying the handle using cudaLibraryGetKernel() or cudaGetKernel and then passing it to the API by casting to void*. The symbol entryFuncAddr passed to cudaGetKernel should be a symbol that is registered with the same CUDA Runtime instance.


Passing a symbol that belongs that belongs to a different runtime instance will result in undefined behavior. The only type
                                             that can be reliably passed to a different runtime instance is cudaKernel_t

See also:
cudaOccupancyMaxActiveBlocksPerMultiprocessorWithFlags, cudaOccupancyMaxPotentialBlockSize ( C++ API), cudaOccupancyMaxPotentialBlockSizeWithFlags ( C++ API), cudaOccupancyMaxPotentialBlockSizeVariableSMem ( C++ API), cudaOccupancyMaxPotentialBlockSizeVariableSMemWithFlags ( C++ API), cudaOccupancyAvailableDynamicSMemPerBlock

__host__
                              ​
                              __device__
                              ​cudaError_t cudaOccupancyMaxActiveBlocksPerMultiprocessor (  int* numBlocks, const void* func, int  blockSize, size_t dynamicSMemSize )
Returns occupancy for a device function.

                                 Parameters



numBlocks
- Returned occupancy
func
- Kernel function for which occupancy is calculated
blockSize
- Block size the kernel is intended to be launched with
dynamicSMemSize
- Per-block dynamic shared memory usage intended, in bytes

Returns
cudaSuccess, cudaErrorInvalidDevice, cudaErrorInvalidDeviceFunction, cudaErrorInvalidValue, cudaErrorUnknown,


Description
Returns in *numBlocks the maximum number of active blocks per streaming multiprocessor for the device function.


Note:

Note that this function may also return error codes from previous, asynchronous launches.

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


The API can also be used with a kernel cudaKernel_t by querying the handle using cudaLibraryGetKernel() or cudaGetKernel and then passing it to the API by casting to void*. The symbol entryFuncAddr passed to cudaGetKernel should be a symbol that is registered with the same CUDA Runtime instance.


Passing a symbol that belongs that belongs to a different runtime instance will result in undefined behavior. The only type
                                             that can be reliably passed to a different runtime instance is cudaKernel_t

See also:
cudaOccupancyMaxActiveBlocksPerMultiprocessorWithFlags, cudaOccupancyMaxPotentialBlockSize ( C++ API), cudaOccupancyMaxPotentialBlockSizeWithFlags ( C++ API), cudaOccupancyMaxPotentialBlockSizeVariableSMem ( C++ API), cudaOccupancyMaxPotentialBlockSizeVariableSMemWithFlags ( C++ API), cudaOccupancyAvailableDynamicSMemPerBlock (C++ API), cuOccupancyMaxActiveBlocksPerMultiprocessor

__host__
                              ​cudaError_t cudaOccupancyMaxActiveBlocksPerMultiprocessorWithFlags (  int* numBlocks, const void* func, int  blockSize, size_t dynamicSMemSize, unsigned int  flags )
Returns occupancy for a device function with the specified flags.

                                 Parameters



numBlocks
- Returned occupancy
func
- Kernel function for which occupancy is calculated
blockSize
- Block size the kernel is intended to be launched with
dynamicSMemSize
- Per-block dynamic shared memory usage intended, in bytes
flags
- Requested behavior for the occupancy calculator

Returns
cudaSuccess, cudaErrorInvalidDevice, cudaErrorInvalidDeviceFunction, cudaErrorInvalidValue, cudaErrorUnknown,


Description
Returns in *numBlocks the maximum number of active blocks per streaming multiprocessor for the device function.

The flags parameter controls how special cases are handled. Valid flags include:


cudaOccupancyDefault: keeps the default behavior as cudaOccupancyMaxActiveBlocksPerMultiprocessor

cudaOccupancyDisableCachingOverride: This flag suppresses the default behavior on platform where global caching affects occupancy. On such platforms, if caching
                                          is enabled, but per-block SM resource usage would result in zero occupancy, the occupancy calculator will calculate the occupancy
                                          as if caching is disabled. Setting this flag makes the occupancy calculator to return 0 in such cases. More information can
                                          be found about this feature in the "Unified L1/Texture Cache" section of the Maxwell tuning guide.


Note:

Note that this function may also return error codes from previous, asynchronous launches.

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


The API can also be used with a kernel cudaKernel_t by querying the handle using cudaLibraryGetKernel() or cudaGetKernel and then passing it to the API by casting to void*. The symbol entryFuncAddr passed to cudaGetKernel should be a symbol that is registered with the same CUDA Runtime instance.


Passing a symbol that belongs that belongs to a different runtime instance will result in undefined behavior. The only type
                                             that can be reliably passed to a different runtime instance is cudaKernel_t

See also:
cudaOccupancyMaxActiveBlocksPerMultiprocessor, cudaOccupancyMaxPotentialBlockSize ( C++ API), cudaOccupancyMaxPotentialBlockSizeWithFlags ( C++ API), cudaOccupancyMaxPotentialBlockSizeVariableSMem ( C++ API), cudaOccupancyMaxPotentialBlockSizeVariableSMemWithFlags ( C++ API), cudaOccupancyAvailableDynamicSMemPerBlock (C++ API), cuOccupancyMaxActiveBlocksPerMultiprocessorWithFlags

__host__
                              ​cudaError_t cudaOccupancyMaxActiveClusters (  int* numClusters, const void* func, const cudaLaunchConfig_t* launchConfig )
Given the kernel function (func) and launch configuration (config), return the maximum number of clusters that could co-exist on the target device in *numClusters.


                                 Parameters



numClusters
- Returned maximum number of clusters that could co-exist on the target device
func
- Kernel function for which maximum number of clusters are calculated
launchConfig

Returns
cudaSuccess, cudaErrorInvalidDeviceFunction, cudaErrorInvalidValue, cudaErrorInvalidClusterSize, cudaErrorUnknown,


Description
If the function has required cluster size already set (see cudaFuncGetAttributes), the cluster size from config must either be unspecified or match the required size. Without required sizes, the cluster
                                 size must be specified in config, else the function will return an error.

Note that various attributes of the kernel function may affect occupancy calculation. Runtime environment may affect how the
                                 hardware schedules the clusters, so the calculated occupancy is not guaranteed to be achievable.


Note:

Note that this function may also return error codes from previous, asynchronous launches.

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


The API can also be used with a kernel cudaKernel_t by querying the handle using cudaLibraryGetKernel() or cudaGetKernel and then passing it to the API by casting to void*. The symbol entryFuncAddr passed to cudaGetKernel should be a symbol that is registered with the same CUDA Runtime instance.


Passing a symbol that belongs that belongs to a different runtime instance will result in undefined behavior. The only type
                                             that can be reliably passed to a different runtime instance is cudaKernel_t

See also:
cudaFuncGetAttributes cudaOccupancyMaxActiveClusters (C++ API), cuOccupancyMaxActiveClusters

__host__
                              ​cudaError_t cudaOccupancyMaxPotentialClusterSize (  int* clusterSize, const void* func, const cudaLaunchConfig_t* launchConfig )
Given the kernel function (func) and launch configuration (config), return the maximum cluster size in *clusterSize.


                                 Parameters



clusterSize
- Returned maximum cluster size that can be launched for the given kernel function and launch configuration
func
- Kernel function for which maximum cluster size is calculated
launchConfig

Returns
cudaSuccess, cudaErrorInvalidDeviceFunction, cudaErrorInvalidValue, cudaErrorUnknown,


Description
The cluster dimensions in config are ignored. If func has a required cluster size set (see cudaFuncGetAttributes),*clusterSize will reflect the required cluster size.

By default this function will always return a value that's portable on future hardware. A higher value may be returned if
                                 the kernel function allows non-portable cluster sizes.

This function will respect the compile time launch bounds.

Note:

Note that this function may also return error codes from previous, asynchronous launches.

Note that this function may also return cudaErrorInitializationError, cudaErrorInsufficientDriver or cudaErrorNoDevice if this call tries to initialize internal CUDA RT state.


Note that as specified by cudaStreamAddCallback no CUDA function may be called from callback. cudaErrorNotPermitted may, but is not guaranteed to, be returned as a diagnostic in such case.


The API can also be used with a kernel cudaKernel_t by querying the handle using cudaLibraryGetKernel() or cudaGetKernel and then passing it to the API by casting to void*. The symbol entryFuncAddr passed to cudaGetKernel should be a symbol that is registered with the same CUDA Runtime instance.


Passing a symbol that belongs that belongs to a different runtime instance will result in undefined behavior. The only type
                                             that can be reliably passed to a different runtime instance is cudaKernel_t

See also:
cudaFuncGetAttributes cudaOccupancyMaxPotentialClusterSize (C++ API), cuOccupancyMaxPotentialClusterSize


---