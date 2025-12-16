# Sanitizer Result Codes


Error and result codes returned by Sanitizer functions.


## Enumerations


SanitizerResult
Sanitizer result codes.


## Functions


SanitizerResult sanitizerGetResultString(SanitizerResult result, const char str)
Get the descriptive string for a SanitizerResult.


## Enumerations


enum SanitizerResult
Sanitizer result codes.
Error and result codes returned by Sanitizer functions.
Values:

enumerator SANITIZER_SUCCESS
No error.

enumerator SANITIZER_ERROR_INVALID_PARAMETER
One or more of the parameters is invalid.

enumerator SANITIZER_ERROR_INVALID_DEVICE
The device does not correspond to a valid CUDA device.

enumerator SANITIZER_ERROR_INVALID_CONTEXT
The context is NULL or not valid.

enumerator SANITIZER_ERROR_INVALID_DOMAIN_ID
The domain ID is invalid.

enumerator SANITIZER_ERROR_INVALID_CALLBACK_ID
The callback ID is invalid.

enumerator SANITIZER_ERROR_INVALID_OPERATION
The current operation cannot be performed due to dependency on other factors.

enumerator SANITIZER_ERROR_OUT_OF_MEMORY
Unable to allocate enough memory to perform the requested operation.

enumerator SANITIZER_ERROR_PARAMETER_SIZE_NOT_SUFFICIENT
The output buffer size is not sufficient to return all requested data.

enumerator SANITIZER_ERROR_API_NOT_IMPLEMENTED
API is not implemented.

enumerator SANITIZER_ERROR_MAX_LIMIT_REACHED
The maximum limit is reached.

enumerator SANITIZER_ERROR_NOT_READY
The object is not ready to perform the requested operation.

enumerator SANITIZER_ERROR_NOT_COMPATIBLE
The current operation is not compatible with the current state of the object.

enumerator SANITIZER_ERROR_NOT_INITIALIZED
Sanitizer is unable to initialize its connection to the CUDA driver.

enumerator SANITIZER_ERROR_NOT_SUPPORTED
The attempted operation is not supported on the current system or device.

enumerator SANITIZER_ERROR_ADDRESS_NOT_IN_DEVICE_MEMORY
The attempted device operation has a parameter not in device memory.

enumerator SANITIZER_ERROR_UNKNOWN
An unknown internal error has occurred.

enumerator SANITIZER_ERROR_FORCE_INT


## Functions


SanitizerResult sanitizerGetResultString(

SanitizerResult result,
const char str,

)
Get the descriptive string for a SanitizerResult.
Return the descriptive string for a SanitizerResult in *str.

Note
Thread-safety: this function is thread-safe.

Parameters:

result – The result to get the string for.
str – Returns the string.

Return values:

SANITIZER_SUCCESS – on success.
SANITIZER_ERROR_INVALID_PARAMETER – if str is NULL or result is not a valid SanitizerResult.