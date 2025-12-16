# CUDA Runtime API

[< Previous](structcudaExternalSemaphoreSignalNodeParams.html) | [Next >](structcudaExternalSemaphoreSignalParams.html)  CUDA Runtime API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Runtime_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Runtime%20API)
## 7.25. cudaExternalSemaphoreSignalNodeParamsV2 Struct Reference


## [[Data types used by CUDA Runtime](group__CUDART__TYPES.html)]


External semaphore signal node parameters


### Public Variables


cudaExternalSemaphore_t extSemArrayunsigned int  numExtSemscudaExternalSemaphoreSignalParams
                           * paramsArray

### Variables


cudaExternalSemaphore_t cudaExternalSemaphoreSignalNodeParamsV2::extSemArray [inherited]
Array of external semaphore handles.

unsigned int  cudaExternalSemaphoreSignalNodeParamsV2::numExtSems [inherited]
Number of handles and parameters supplied in extSemArray and paramsArray.

cudaExternalSemaphoreSignalParams
                              * cudaExternalSemaphoreSignalNodeParamsV2::paramsArray [inherited]
Array of external semaphore signal parameters.


---