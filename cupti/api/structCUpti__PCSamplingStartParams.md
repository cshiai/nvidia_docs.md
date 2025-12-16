# 7.129. CUpti_PCSamplingStartParams


struct CUpti_PCSamplingStartParams
Params for cuptiPCSamplingStart.

Public Members

size_t size
[w] Size of the data structure i.e.
CUpti_PCSamplingStartParamsSize CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

void *pPriv
[w] Assign to NULL

CUcontext ctx
[w] CUcontext