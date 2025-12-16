# 7.120. CUpti_PCSamplingConfigurationInfoParams


struct CUpti_PCSamplingConfigurationInfoParams
PC sampling configuration structure.
This structure configures PC sampling using cuptiPCSamplingSetConfigurationAttribute and queries PC sampling default configuration using cuptiPCSamplingGetConfigurationAttribute

Public Members

size_t size
[w] Size of the data structure i.e.
CUpti_PCSamplingConfigurationInfoParamsSize CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

void *pPriv
[w] Assign to NULL

CUcontext ctx
[w] CUcontext

size_t numAttributes
[w] Number of attributes to configure using cuptiPCSamplingSetConfigurationAttribute or query using cuptiPCSamplingGetConfigurationAttribute

CUpti_PCSamplingConfigurationInfo *pPCSamplingConfigurationInfo
Refer CUpti_PCSamplingConfigurationInfo.