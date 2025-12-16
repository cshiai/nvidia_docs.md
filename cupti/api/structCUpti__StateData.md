# 7.202. CUpti_StateData


struct CUpti_StateData
Data passed into a State callback function.
Data passed into a State callback function as the cbdata argument to CUpti_CallbackFunc. The cbdata will be this type for domain equal to CUPTI_CB_DOMAIN_STATE and callback Ids belonging to CUpti_CallbackIdState. Unless otherwise noted, the callback data is valid only within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of that data.

Public Members

CUptiResult result
Error code.

const char *message
String containing more details.
It can be NULL.

struct CUpti_StateData::[anonymous]::[anonymous] notification
Data passed along with the callback Ids Enum CUpti_CallbackIdState used to denote callback ids.