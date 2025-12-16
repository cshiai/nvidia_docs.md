# 8.1.1.1. BufferInfo


Fully qualified name: `CUPTI::PcSamplingUtil::BufferInfo`


struct BufferInfo
BufferInfo will be stored in the file for every buffer i.e for every call of UtilDumpPcSamplingBufferInFile() API.

Public Members

uint64_t recordCount
Total number of PC records.

size_t numStallReasons
Count of all stall reasons supported on the GPU.

uint64_t numSelectedStallReasons
Total number of stall reasons in single record.

uint64_t bufferByteSize
Buffer size in Bytes.