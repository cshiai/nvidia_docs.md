# 7.126. CUpti_PCSamplingGetStallReasonsParams


struct CUpti_PCSamplingGetStallReasonsParams
Params for cuptiPCSamplingGetStallReasons.

Public Members

size_t size
[w] Size of the data structure i.e.
CUpti_PCSamplingGetStallReasonsParamsSize CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

void *pPriv
[w] Assign to NULL

CUcontext ctx
[w] CUcontext

size_t numStallReasons
[w] Number of stall reasons

uint32_t *stallReasonIndex
[r] Stall reason index

char stallReasons
[r] Stall reasons name