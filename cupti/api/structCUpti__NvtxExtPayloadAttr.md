# 7.118. CUpti_NvtxExtPayloadAttr


struct CUpti_NvtxExtPayloadAttr
Public Members

uint32_t structSize
Size of the struct in bytes.

uint32_t type
The payload type.
CUpti_NvtxExtPayloadType

void *attributes
The attributes of the payload.
Depending on the type, typecast the pointer: CUPTI_NVTX_EXT_PAYLOAD_TYPE_SCHEMA: nvtxPayloadSchemaAttr_t CUPTI_NVTX_EXT_PAYLOAD_TYPE_ENUM: nvtxPayloadEnumAttr_t