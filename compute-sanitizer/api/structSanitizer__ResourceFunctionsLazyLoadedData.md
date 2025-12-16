# Sanitizer_ResourceFunctionsLazyLoadedData


struct Sanitizer_ResourceFunctionsLazyLoadedData
Data passed into a CUDA function callback function.
Data passed into a CUDA function callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal tp SANITIZER_CB_DOMAIN_RESOURCE and cbid equal to SANITIZER_CBID_RESOURCE_FUNCTIONS_LAZY_LOADED or SANITIZER_CBID_RESOURCE_FUNCTIONS_LAZY_PATCHED. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

CUcontext context
The context containing the functions.

const CUfunction *functions
An array containing the functions.

CUmodule module
The module containing the functions.

uint32_t numFunctions
The size of the function array.