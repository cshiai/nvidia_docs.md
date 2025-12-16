# 8.1.1.4. CUptiUtil_GetPcSampDataParams


Fully qualified name: `CUPTI::PcSamplingUtil::CUptiUtil_GetPcSampDataParams`


struct CUptiUtil_GetPcSampDataParams
Params for CuptiUtilGetPcSampData.

Public Members

size_t size
Size of the data structure i.e.
CUpti_PCSamplingDisableParamsSize CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

std::ifstream *fileHandler
File handle.

PcSamplingBufferType bufferType
Type of buffer to store in file.

BufferInfo *pBufferInfoData
Pointer to collected buffer info using CuptiUtilGetBufferInfo.

void *pSamplingData
Pointer to allocated memory to store retrieved data from file.

size_t numAttributes
Number of configuration attributes.

CUpti_PCSamplingConfigurationInfo *pPCSamplingConfigurationInfo
Refer CUpti_PCSamplingConfigurationInfo.

PcSamplingStallReasons *pPcSamplingStallReasons
Refer PcSamplingStallReasons.
For stallReasons field of PcSamplingStallReasons it is expected to allocate memory for each string element of array.