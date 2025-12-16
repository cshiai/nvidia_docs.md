# CUDA Driver API

[< Previous](structCUDA__EVENT__WAIT__NODE__PARAMS.html) | [Next >](structCUDA__EXT__SEM__SIGNAL__NODE__PARAMS__v2.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.22. CUDA_EXT_SEM_SIGNAL_NODE_PARAMS_v1 Struct Reference


## [[Data types used by CUDA driver](group__CUDA__TYPES.html)]


Semaphore signal node parameters


### Public Variables


CUexternalSemaphore extSemArrayunsigned int  numExtSemsconst
                           CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS
                           * paramsArray

### Variables


CUexternalSemaphore CUDA_EXT_SEM_SIGNAL_NODE_PARAMS_v1::extSemArray [inherited]
Array of external semaphore handles.

unsigned int  CUDA_EXT_SEM_SIGNAL_NODE_PARAMS_v1::numExtSems [inherited]
Number of handles and parameters supplied in extSemArray and paramsArray.

const

                              CUDA_EXTERNAL_SEMAPHORE_SIGNAL_PARAMS
                              * CUDA_EXT_SEM_SIGNAL_NODE_PARAMS_v1::paramsArray [inherited]
Array of external semaphore signal parameters.


---