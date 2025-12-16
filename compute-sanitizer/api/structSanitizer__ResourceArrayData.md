# Sanitizer_ResourceArrayData


struct Sanitizer_ResourceArrayData
Data passed into a CUDA array callback function.
Data passed into a CUDA array callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal tp SANITIZER_CB_DOMAIN_RESOURCE and cbid equal to SANITIZER_CBID_RESOURCE_ARRAY_CREATED or SANITIZER_CBID_RESOURCE_ARRAY_DESTROYED. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

CUcontext context
The context containing the array being created or destroyed.

uint64_t depth

CUarray hArray
The CUDA array being created or destroyed.

uint64_t height

uint64_t width
The CUDA array size.