# 8.1.1. PcSamplingUtil


Fully qualified name: `CUPTI::PcSamplingUtil`


namespace PcSamplingUtil

## 8.1.1.9. Data Structures


BufferInfo
BufferInfo will be stored in the file for every buffer i.e for every call of UtilDumpPcSamplingBufferInFile() API.

CUptiUtil_GetBufferInfoParams
Params for CuptiUtilGetBufferInfo .

CUptiUtil_GetHeaderDataParams
Params for CuptiUtilGetHeaderData .

CUptiUtil_GetPcSampDataParams
Params for CuptiUtilGetPcSampData .

CUptiUtil_MergePcSampDataParams
Params for CuptiUtilMergePcSampData .

CUptiUtil_PutPcSampDataParams
Params for CuptiUtilPutPcSampData .

Header
Header info will be stored in file.

PcSamplingStallReasons
All available stall reasons name and respective indexes will be stored in it.


## 8.1.1.10. Enumerations


CUptiUtilResult
CUPTI PC sampling utility API result codes.

PcSamplingBufferType
CUPTI PC sampling buffer types.


## 8.1.1.11. Functions


CUptiUtilResult CuptiUtilGetBufferInfo(CUptiUtil_GetBufferInfoParams *pParams)
Get buffer info data of file.

CUptiUtilResult CuptiUtilGetHeaderData(CUptiUtil_GetHeaderDataParams *pParams)
Get header data of file.

CUptiUtilResult CuptiUtilGetPcSampData(CUptiUtil_GetPcSampDataParams *pParams)
Retrieve PC sampling data from file into allocated buffer.

CUptiUtilResult CuptiUtilMergePcSampData(CUptiUtil_MergePcSampDataParams *pParams)
Merge PC sampling data range id wise.

CUptiUtilResult CuptiUtilPutPcSampData(CUptiUtil_PutPcSampDataParams *pParams)
Dump PC sampling data into the file.