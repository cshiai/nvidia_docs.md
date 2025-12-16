# 8.1.1.2. CUptiUtil_GetBufferInfoParams


Fully qualified name: `CUPTI::PcSamplingUtil::CUptiUtil_GetBufferInfoParams`


struct CUptiUtil_GetBufferInfoParams
Params for CuptiUtilGetBufferInfo.

Public Members

size_t size
Size of the data structure i.e.
CUpti_PCSamplingDisableParamsSize CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

std::ifstream *fileHandler
File handle.

BufferInfo bufferInfoData
Buffer Info.