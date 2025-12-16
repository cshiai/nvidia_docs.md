# Sanitizer_ResourceVirtualRange


struct Sanitizer_ResourceVirtualRange
Data passed into a VA reservation callback function.
Data passed into a VA reservation callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal tp SANITIZER_CB_DOMAIN_RESOURCE and cbid equal to SANITIZER_CBID_RESOURCE_VIRTUAL_RESERVE. or SANITIZER_CBID_RESOURCE_VIRTUAL_RELEASE. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it. Available with a driver version of 535 or newer.

Public Members

uint64_t address
Address of the VA range being reserved or released.

uint64_t size
Size of the VA range being reserved or released.