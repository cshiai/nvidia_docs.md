# 7.7. CUpti_ActivityComputeEngineCtxSwitch


struct CUpti_ActivityComputeEngineCtxSwitch
The activity record for trace of CUDA context switch events.
The corresponding activity kind is CUPTI_ACTIVITY_KIND_COMPUTE_ENGINE_CTX_SWITCH.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_COMPUTE_ENGINE_CTX_SWITCH.

uint32_t contextId
The ID of the CUDA context.

uint64_t timestamp
The timestamp at which the CUpti_ComputeEngineCtxSwitchOperationType occurs.

CUpti_ComputeEngineCtxSwitchOperationType operationType
The type of the Compute Engine Context switch operation.
CUPTI_COMPUTE_ENGINE_CTX_SWITCH_OPERATION_START indicates the start of the context switch operation. CUPTI_COMPUTE_ENGINE_CTX_SWITCH_OPERATION_END indicates the end of the context switch operation.