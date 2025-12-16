# 7.104. CUpti_ActivitySourceLocator


struct CUpti_ActivitySourceLocator
The activity record for source locator.
This activity record represents a source locator (CUPTI_ACTIVITY_KIND_SOURCE_LOCATOR).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_SOURCE_LOCATOR.

uint32_t id
The ID for the source path, will be used in all the source level results.

uint32_t lineNumber
The line number in the source .

uint32_t pad
Undefined.
Reserved for internal use.

const char *fileName
The path for the file.