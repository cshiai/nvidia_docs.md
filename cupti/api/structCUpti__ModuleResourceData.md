# 7.116. CUpti_ModuleResourceData


struct CUpti_ModuleResourceData
Module data passed into a resource callback function.
CUDA module data passed into a resource callback function as the cbdata argument to CUpti_CallbackFunc. The cbdata will be this type for domain equal to CUPTI_CB_DOMAIN_RESOURCE. The module data is valid only within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of that data.

Public Members

uint32_t moduleId
Identifier to associate with the CUDA module.

size_t cubinSize
The size of the cubin.

const char *pCubin
Pointer to the associated cubin.