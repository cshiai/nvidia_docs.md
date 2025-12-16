# Sanitizer_CallbackData


struct Sanitizer_CallbackData
Data passed into a runtime or driver API callback function.
Data passed into a runtime or driver API callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_DRIVER_API or SANITIZER_CB_DOMAIN_RUNTIME_API. The callback data is valid only within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make of a copy of that data. For example, if you make a shallow copy of Sanitizer_CallbackData within a callback, you cannot dereference functionParams outside of that callback to access the function parameters. functionName is an exception: the string pointed to by functionName is a global constant and so may be accessed outside of the callback.

Public Members

Sanitizer_ApiCallbackSite callbackSite
Point in the runtime or driver function from where the callback was issued.

CUcontext context
Driver context current to the thread, or null if no context is current.
This value can change from the entry to exit callback of a runtime API function if the runtime initialized a context.

const char *functionName
Name of the runtime or driver API function which issued the callback.
This string is a global constant and so may be accessed outside of the callback.

const void *functionParams
Pointer to the arguments passed to the runtime or driver API call.
See generated_cuda_runtime_api_meta.h and generated_cuda_meta.h for structure definitions for the parameters for each runtime and driver API function.

const void *functionReturnValue
Pointer to the return value of the runtime or driver API call.
This field is only valid within the SANITIZER_API_EXIT callback. For a runtime API functionReturnValue points to a cudaError_t. For a driver API functionReturnValue points to a CUresult.

const char *symbolName
Name of the symbol operated on by the runtime or driver API function which issued the callback.
This entry is valid only for driver and runtime launch callbacks, where it returns the name of the kernel.