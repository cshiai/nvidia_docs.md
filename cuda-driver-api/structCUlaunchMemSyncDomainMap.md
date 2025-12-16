# CUDA Driver API

[< Previous](structCUlaunchConfig.html) | [Next >](structCUmemAccessDesc__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.69. CUlaunchMemSyncDomainMap Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Memory Synchronization Domain map


See [cudaLaunchMemSyncDomain](https://docs.nvidia.com/cuda/cuda-runtime-api/group__CUDART__TYPES.html#group__CUDART__TYPES_1gafb98f7ea7b0397ed6503780f3e672d5).


By default, kernels are launched in domain 0. Kernel launched with [CU_LAUNCH_MEM_SYNC_DOMAIN_REMOTE](group__CUDA__TYPES.html#group__CUDA__TYPES_1gg471f645fa24df354626fe8107358e05fd06c15e0689a9ec3b9393a32646f5417) will have a different domain ID. User may also alter the domain ID with [CUlaunchMemSyncDomainMap](structCUlaunchMemSyncDomainMap.html#structCUlaunchMemSyncDomainMap) for a specific stream / graph node / kernel launch. See [CU_LAUNCH_ATTRIBUTE_MEM_SYNC_DOMAIN_MAP](group__CUDA__TYPES.html#group__CUDA__TYPES_1gg6f6565b334be6bb3134868e10bbdd331b05f66cedd0038b77034a8c62127a09d).


Domain ID range is available through [CU_DEVICE_ATTRIBUTE_MEM_SYNC_DOMAIN_COUNT](group__CUDA__TYPES.html#group__CUDA__TYPES_1gge12b8a782bebe21b1ac0091bf9f4e2a3e21f4ac335f51cc411f8059a1348274c).


### Public Variables


unsigned char  default_unsigned char  remote

### Variables


unsigned char  CUlaunchMemSyncDomainMap::default_ [inherited]
The default domain ID to use for designated kernels

unsigned char  CUlaunchMemSyncDomainMap::remote [inherited]
The remote domain ID to use for designated kernels


---