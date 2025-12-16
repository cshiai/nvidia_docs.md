# 7.113. CUpti_GetCubinCrcParams


struct CUpti_GetCubinCrcParams
Params for cuptiGetCubinCrc.

Public Members

size_t size
[w] Size of configuration structure.
CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

size_t cubinSize
[w] Size of cubin binary.

const void *cubin
[w] Pointer to cubin binary

uint64_t cubinCrc
[r] Computed CRC will be stored in it.