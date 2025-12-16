# 7.124. CUpti_PCSamplingGetDataParams


struct CUpti_PCSamplingGetDataParams
Params for cuptiPCSamplingEnable.

Public Members

size_t size
[w] Size of the data structure i.e.
CUpti_PCSamplingGetDataParamsSize CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

void *pPriv
[w] Assign to NULL

CUcontext ctx
[w] CUcontext

void *pcSamplingData

Param pcSamplingData:
Data buffer to hold collected PC Sampling data PARSED_DATA Buffer type is void * which can point to PARSED_DATA Refer CUpti_PCSamplingData for buffer format for PARSED_DATA