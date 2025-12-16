# 7.205. CUpti_SynchronizeData


struct CUpti_SynchronizeData
Data passed into a synchronize callback function.
Data passed into a synchronize callback function as the cbdata argument to CUpti_CallbackFunc. The cbdata will be this type for domain equal to CUPTI_CB_DOMAIN_SYNCHRONIZE. The callback data is valid only within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of that data.

Public Members

CUcontext context
The context of the stream being synchronized.

CUstream stream
The stream being synchronized.