# 8.1.1.6. CUptiUtil_PutPcSampDataParams


Fully qualified name: `CUPTI::PcSamplingUtil::CUptiUtil_PutPcSampDataParams`


struct CUptiUtil_PutPcSampDataParams
Params for CuptiUtilPutPcSampData.

Public Members

size_t size
Size of the data structure i.e.
CUpti_PCSamplingDisableParamsSize CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

PcSamplingBufferType bufferType
Type of buffer to store in file.

void *pSamplingData
PC sampling buffer.

size_t numAttributes
Number of configured attributes.

CUpti_PCSamplingConfigurationInfo *pPCSamplingConfigurationInfo
Refer CUpti_PCSamplingConfigurationInfo It is expected to provide configuration details of at least CUPTI_PC_SAMPLING_CONFIGURATION_ATTR_TYPE_STALL_REASON attribute.

PcSamplingStallReasons *pPcSamplingStallReasons
Refer PcSamplingStallReasons.

const char *fileName
File name to store buffer into it.