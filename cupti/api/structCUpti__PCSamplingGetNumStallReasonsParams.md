# 7.125. CUpti_PCSamplingGetNumStallReasonsParams


struct CUpti_PCSamplingGetNumStallReasonsParams
Params for cuptiPCSamplingGetNumStallReasons.

Public Members

size_t size
[w] Size of the data structure i.e.
CUpti_PCSamplingGetNumStallReasonsParamsSize CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

void *pPriv
[w] Assign to NULL

CUcontext ctx
[w] CUcontext

size_t *numStallReasons
[r] Number of stall reasons