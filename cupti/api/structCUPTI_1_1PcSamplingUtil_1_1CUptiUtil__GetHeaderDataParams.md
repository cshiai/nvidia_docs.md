# 8.1.1.3. CUptiUtil_GetHeaderDataParams


Fully qualified name: `CUPTI::PcSamplingUtil::CUptiUtil_GetHeaderDataParams`


struct CUptiUtil_GetHeaderDataParams
Params for CuptiUtilGetHeaderData.

Public Members

size_t size
Size of the data structure i.e.
CUpti_PCSamplingDisableParamsSize CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

std::ifstream *fileHandler
File handle.

Header headerInfo
Header Info.