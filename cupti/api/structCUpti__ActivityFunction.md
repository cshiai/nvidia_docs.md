# 7.26. CUpti_ActivityFunction


struct CUpti_ActivityFunction
The activity record for global/device functions.
This activity records function name and corresponding module information. (CUPTI_ACTIVITY_KIND_FUNCTION).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_FUNCTION.

uint32_t id
ID to uniquely identify the record.

uint32_t contextId
The ID of the context where the function is launched.

uint32_t moduleId
The module ID in which this global/device function is present.

uint32_t functionIndex
The function’s unique symbol index in the module.

uint32_t pad
Undefined.
Reserved for internal use.

const char *name
The name of the function.
This name is shared across all activity records representing the same kernel, and so should not be modified.