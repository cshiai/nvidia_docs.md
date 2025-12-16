# 7.117. CUpti_NvtxData


struct CUpti_NvtxData
Data passed into a NVTX callback function.
Data passed into a NVTX callback function as the cbdata argument to CUpti_CallbackFunc. The cbdata will be this type for domain equal to CUPTI_CB_DOMAIN_NVTX. Unless otherwise notes, the callback data is valid only within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of that data.

Public Members

const char *functionName
Name of the NVTX API function which issued the callback.
This string is a global constant and so may be accessed outside of the callback.

const void *functionParams
Pointer to the arguments passed to the NVTX API call.
See generated_nvtx_meta.h for structure definitions for the parameters for each NVTX API function.

const void *functionReturnValue
Pointer to the return value of the NVTX API call.
See nvToolsExt.h for each NVTX API function’s return value.