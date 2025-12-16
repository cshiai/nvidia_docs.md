# 7.80. CUpti_ActivityModule


struct CUpti_ActivityModule
The activity record for a CUDA module.
This activity record represents a CUDA module (CUPTI_ACTIVITY_KIND_MODULE). This activity record kind is not produced by the activity API but is included for completeness and ease-of-use. Profile frameworks built on top of CUPTI that collect module data from the module callback may choose to use this type to store the collected module data.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_MODULE.

uint32_t contextId
The ID of the context where the module is loaded.

uint32_t id
The module ID.

uint32_t cubinSize
The cubin size.

const void *cubin
The pointer to cubin.