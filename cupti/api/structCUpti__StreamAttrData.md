# 7.203. CUpti_StreamAttrData


struct CUpti_StreamAttrData
Stream attribute data passed into a resource callback function for CUPTI_CBID_RESOURCE_STREAM_ATTRIBUTE_CHANGED callback.
Data passed into a resource callback function as the cbdata argument to CUpti_CallbackFunc. The cbdata will be this type for domain equal to CUPTI_CB_DOMAIN_RESOURCE. The stream attribute data is valid only within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of that data.

Public Members

CUstream stream
The CUDA stream handle for the attribute.

CUstreamAttrID attr
The type of the CUDA stream attribute.

const CUstreamAttrValue *value
The value of the CUDA stream attribute.