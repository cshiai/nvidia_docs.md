# 8.1.1.5. CUptiUtil_MergePcSampDataParams


Fully qualified name: `CUPTI::PcSamplingUtil::CUptiUtil_MergePcSampDataParams`


struct CUptiUtil_MergePcSampDataParams
Params for CuptiUtilMergePcSampData.

Public Members

size_t size
Size of the data structure i.e.
CUpti_PCSamplingDisableParamsSize CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

size_t numberOfBuffers
Number of buffers to merge.

CUpti_PCSamplingData *PcSampDataBuffer
Pointer to array of buffers to merge.

CUpti_PCSamplingData MergedPcSampDataBuffers
Pointer to array of merged buffers as per the range id.

size_t *numMergedBuffer
Number of merged buffers.