# CUDA Runtime API

[< Previous](structcudaLaunchConfig__t.html) | [Next >](structcudaMemAccessDesc.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.45. cudaLaunchMemSyncDomainMap Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


Memory Synchronization Domain map


See [cudaLaunchMemSyncDomain](group__CUDART__TYPES.html#group__CUDART__TYPES_1gafb98f7ea7b0397ed6503780f3e672d5).


By default, kernels are launched in domain 0. Kernel launched with [cudaLaunchMemSyncDomainRemote](group__CUDART__TYPES.html#group__CUDART__TYPES_1ggafb98f7ea7b0397ed6503780f3e672d5ac477b14c4ce022e029a4c2523eaeec2) will have a different domain ID. User may also alter the domain ID with [cudaLaunchMemSyncDomainMap](structcudaLaunchMemSyncDomainMap.html#structcudaLaunchMemSyncDomainMap) for a specific stream / graph node / kernel launch. See [cudaLaunchAttributeMemSyncDomainMap](group__CUDART__TYPES.html#group__CUDART__TYPES_1ggfc5ed48085f05863b1aeebb14934b056fef6b4fb87bd2e289180c2ca5805094d).


Domain ID range is available through [cudaDevAttrMemSyncDomainCount](group__CUDART__TYPES.html#group__CUDART__TYPES_1gg49e2f8c2c0bd6fe264f2fc970912e5cd82ae431cc82ee71d008b4e8e9cac06ab).


### Public Variables


unsigned char  default_unsigned char  remote

### Variables


unsigned char  cudaLaunchMemSyncDomainMap::default_ [inherited]
The default domain ID to use for designated kernels

unsigned char  cudaLaunchMemSyncDomainMap::remote [inherited]
The remote domain ID to use for designated kernels


---