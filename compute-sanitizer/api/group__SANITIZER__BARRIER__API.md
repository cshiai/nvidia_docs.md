# Sanitizer Barrier API


Functions, types, and enums that implement the Sanitizer Barrier API.


## Functions


SanitizerResult sanitizerGetCudaBarrierCount(CUfunction kernel, uint32_t *numBarriers)
Get number of CUDA barriers used by a function.


## Functions


SanitizerResult sanitizerGetCudaBarrierCount(

CUfunction kernel,
uint32_t *numBarriers,

)
Get number of CUDA barriers used by a function.
The module where kernel resides must have been instrumented using sanitizerPatchModule prior to calling this function. This function is only available for modules built with nvcc 11.2 or newer, it will return 0 otherwise.

Note
Thread-safety: this function is thread safe.

Parameters:

kernel – [in] CUDA function.
numBarriers – [out] Number of CUDA barriers in the input CUDA function.