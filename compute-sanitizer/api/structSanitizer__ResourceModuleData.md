# Sanitizer_ResourceModuleData


struct Sanitizer_ResourceModuleData
Data passed into a module resource callback function.
Data passed into a module resource callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_RESOURCE and cbid equal to SANITIZER_CBID_RESOURCE_MODULE_LOADED or SANITIZER_CBID_RESOURCE_MODULE_UNLOAD_STARTING. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

CUcontext context
The context containing the module being loaded or unloaded.

size_t cubinSize
The size of the cubin.

CUlibrary library
Library associated with the module.

CUmodule module
The module being loaded or unloaded.

const char *pCubin
Pointer to the associated cubin.