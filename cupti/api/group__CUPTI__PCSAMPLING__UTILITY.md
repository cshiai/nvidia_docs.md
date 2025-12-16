# 6.5. CUPTI PC Sampling Utility API


Functions, types, and enums that implement the CUPTI PC Sampling Utility API.


## 6.5.1. Data Structures


CUPTI::PcSamplingUtil::BufferInfo
BufferInfo will be stored in the file for every buffer i.e for every call of UtilDumpPcSamplingBufferInFile() API.

CUPTI::PcSamplingUtil::CUptiUtil_GetBufferInfoParams
Params for CuptiUtilGetBufferInfo .

CUPTI::PcSamplingUtil::CUptiUtil_GetHeaderDataParams
Params for CuptiUtilGetHeaderData .

CUPTI::PcSamplingUtil::CUptiUtil_GetPcSampDataParams
Params for CuptiUtilGetPcSampData .

CUPTI::PcSamplingUtil::CUptiUtil_MergePcSampDataParams
Params for CuptiUtilMergePcSampData .

CUPTI::PcSamplingUtil::CUptiUtil_PutPcSampDataParams
Params for CuptiUtilPutPcSampData .

CUPTI::PcSamplingUtil::Header
Header info will be stored in file.

CUPTI::PcSamplingUtil::PcSamplingStallReasons
All available stall reasons name and respective indexes will be stored in it.


## 6.5.2. Macros


CUptiUtil_GetBufferInfoParamsSizeCUptiUtil_GetHeaderDataParamsSizeCUptiUtil_GetPcSampDataParamsSizeCUptiUtil_MergePcSampDataParamsSizeCUptiUtil_PutPcSampDataParamsSize

## 6.5.3. Enumerations


CUPTI::PcSamplingUtil::CUptiUtilResult
CUPTI PC sampling utility API result codes.

CUPTI::PcSamplingUtil::PcSamplingBufferType
CUPTI PC sampling buffer types.


## 6.5.4. Functions


CUptiUtilResult CUPTI::PcSamplingUtil::CuptiUtilGetBufferInfo(CUptiUtil_GetBufferInfoParams *pParams)
Get buffer info data of file.

CUptiUtilResult CUPTI::PcSamplingUtil::CuptiUtilGetHeaderData(CUptiUtil_GetHeaderDataParams *pParams)
Get header data of file.

CUptiUtilResult CUPTI::PcSamplingUtil::CuptiUtilGetPcSampData(CUptiUtil_GetPcSampDataParams *pParams)
Retrieve PC sampling data from file into allocated buffer.

CUptiUtilResult CUPTI::PcSamplingUtil::CuptiUtilMergePcSampData(CUptiUtil_MergePcSampDataParams *pParams)
Merge PC sampling data range id wise.

CUptiUtilResult CUPTI::PcSamplingUtil::CuptiUtilPutPcSampData(CUptiUtil_PutPcSampDataParams *pParams)
Dump PC sampling data into the file.


## 6.5.5. Macros


CUptiUtil_GetBufferInfoParamsSizeCUptiUtil_GetHeaderDataParamsSizeCUptiUtil_GetPcSampDataParamsSizeCUptiUtil_MergePcSampDataParamsSizeCUptiUtil_PutPcSampDataParamsSize

## 6.5.6. Enumerations


enum CUPTI::PcSamplingUtil::CUptiUtilResult
CUPTI PC sampling utility API result codes.
Error and result codes returned by CUPTI PC sampling utility API.
Values:

enumerator CUPTI_UTIL_SUCCESS
No error.

enumerator CUPTI_UTIL_ERROR_INVALID_PARAMETER
One or more of the parameters are invalid.

enumerator CUPTI_UTIL_ERROR_UNABLE_TO_CREATE_FILE
Unable to create a new file.

enumerator CUPTI_UTIL_ERROR_UNABLE_TO_OPEN_FILE
Unable to open a file.

enumerator CUPTI_UTIL_ERROR_READ_WRITE_OPERATION_FAILED
Read or write operation failed.

enumerator CUPTI_UTIL_ERROR_FILE_HANDLE_CORRUPTED
Provided file handle is corrupted.

enumerator CUPTI_UTIL_ERROR_SEEK_OPERATION_FAILED
seek operation failed.

enumerator CUPTI_UTIL_ERROR_OUT_OF_MEMORY
Unable to allocate enough memory to perform the requested operation.

enumerator CUPTI_UTIL_ERROR_UNKNOWN
An unknown internal error has occurred.

enumerator CUPTI_UTIL_ERROR_FORCE_INT


enum CUPTI::PcSamplingUtil::PcSamplingBufferType
CUPTI PC sampling buffer types.
Values:

enumerator PC_SAMPLING_BUFFER_INVALID
Invalid buffer type.

enumerator PC_SAMPLING_BUFFER_PC_TO_COUNTER_DATA
Refers to CUpti_PCSamplingData buffer.


## 6.5.7. Functions


CUptiUtilResult CUPTI::PcSamplingUtil::CuptiUtilGetBufferInfo(

CUptiUtil_GetBufferInfoParams *pParams,

)
Get buffer info data of file.
This API must be called every time before calling CuptiUtilGetPcSampData API. BufferInfo structure, it gives info about recordCount and stallReasonCount of every record in the buffer. This will help to allocate exact buffer to retrieve data into it.

Return values:

CUPTI_UTIL_SUCCESS –
CUPTI_UTIL_ERROR_INVALID_PARAMETER – error out if either of pParam or fileHandle is NULL or param struct size is incorrect.
CUPTI_UTIL_ERROR_FILE_HANDLE_CORRUPTED – file handle is not in good state to read data from file.
CUPTI_UTIL_ERROR_READ_WRITE_OPERATION_FAILED – failed to read data from file.


CUptiUtilResult CUPTI::PcSamplingUtil::CuptiUtilGetHeaderData(

CUptiUtil_GetHeaderDataParams *pParams,

)
Get header data of file.
This API must be called once initially while retrieving data from file. Header structure, it gives info about total number of buffers present in the file.

Return values:

CUPTI_UTIL_SUCCESS –
CUPTI_UTIL_ERROR_INVALID_PARAMETER – error out if either of pParam or fileHandle is NULL or param struct size is incorrect.
CUPTI_UTIL_ERROR_FILE_HANDLE_CORRUPTED – file handle is not in good state to read data from file
CUPTI_UTIL_ERROR_READ_WRITE_OPERATION_FAILED – failed to read data from file.


CUptiUtilResult CUPTI::PcSamplingUtil::CuptiUtilGetPcSampData(

CUptiUtil_GetPcSampDataParams *pParams,

)
Retrieve PC sampling data from file into allocated buffer.
This API must be called after CuptiUtilGetBufferInfo API. It will retrieve data from file into allocated buffer.

Return values:

CUPTI_UTIL_SUCCESS –
CUPTI_UTIL_ERROR_INVALID_PARAMETER – error out if buffer type is invalid or if either of pSampData, pParams is NULL. If pPcSamplingStallReasons is not NULL then error out if either of stallReasonIndex, stallReasons or stallReasons array element pointer is NULL. or filename is empty.
CUPTI_UTIL_ERROR_READ_WRITE_OPERATION_FAILED –
CUPTI_UTIL_ERROR_FILE_HANDLE_CORRUPTED – file handle is not in good state to read data from file.


CUptiUtilResult CUPTI::PcSamplingUtil::CuptiUtilMergePcSampData(

CUptiUtil_MergePcSampDataParams *pParams,

)
Merge PC sampling data range id wise.
This API merge PC sampling data range id wise. It allocates memory for merged data and fill data in it and provide buffer pointer in MergedPcSampDataBuffers field. It is expected from user to free merge data buffers after use.

Return values:

CUPTI_UTIL_SUCCESS –
CUPTI_UTIL_ERROR_INVALID_PARAMETER – error out if param struct size is invalid or count of buffers to merge is invalid i.e less than 1 or either of PcSampDataBuffer, MergedPcSampDataBuffers, numMergedBuffer is NULL
CUPTI_UTIL_ERROR_OUT_OF_MEMORY – Unable to allocate memory for merged buffer.


CUptiUtilResult CUPTI::PcSamplingUtil::CuptiUtilPutPcSampData(

CUptiUtil_PutPcSampDataParams *pParams,

)
Dump PC sampling data into the file.
This API can be called multiple times. It will append buffer in the file. For every buffer it will store BufferInfo so that before retrieving data it will help to allocate buffer to store retrieved data. This API creates file if file does not present. If stallReasonIndex or stallReasons pointer of CUptiUtil_PutPcSampDataParams is NULL then stall reasons data will not be stored in file. It is expected to store all available stall reason data at least once to refer it during offline correlation.

Return values:

CUPTI_UTIL_SUCCESS –
CUPTI_UTIL_ERROR_INVALID_PARAMETER – error out if buffer type is invalid or if either of pSamplingData, pParams pointer is NULL or stall reason configuration details not provided or filename is empty.
CUPTI_UTIL_ERROR_UNABLE_TO_CREATE_FILE –
CUPTI_UTIL_ERROR_UNABLE_TO_OPEN_FILE –
CUPTI_UTIL_ERROR_READ_WRITE_OPERATION_FAILED –