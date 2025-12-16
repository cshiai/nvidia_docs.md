# 7.114. CUpti_GetSassToSourceCorrelationParams


struct CUpti_GetSassToSourceCorrelationParams
Params for cuptiGetSassToSourceCorrelation.

Public Members

size_t size
[w] Size of the data structure i.e.
CUpti_GetSassToSourceCorrelationParamsSize CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

const void *cubin
[w] Pointer to cubin binary where function belongs.

const char *functionName
[w] Function name to which PC belongs.

size_t cubinSize
[w] Size of cubin binary.

uint32_t lineNumber
[r] Line number in the source code.

uint64_t pcOffset
[w] PC offset

char *fileName
[r] Path for the source file.

char *dirName
[r] Path for the directory of source file.