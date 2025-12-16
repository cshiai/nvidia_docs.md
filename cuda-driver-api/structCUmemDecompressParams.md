# CUDA Driver API

[< Previous](structCUmemcpyAttributes__v1.html) | [Next >](structCUmemFabricHandle__v1.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.91 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 7.74. CUmemDecompressParams Struct Reference


## [[Memory Management](group__CUDA__MEM.html#group__CUDA__MEM)]




### Public Variables


CUmemDecompressAlgorithm algovoid
                           * dstcuuint32_t
                           * dstActBytessize_t  dstNumBytesconst
                           void
                           * srcsize_t  srcNumBytes

### Variables


CUmemDecompressAlgorithmCUmemDecompressParams::algo [inherited]
The decompression algorithm to use.

void
                              * CUmemDecompressParams::dst [inherited]
Pointer to a buffer where the decompressed data will be written. The number of bytes written to this location will be recorded
                                 in the memory pointed to by CUmemDecompressParams_st.dstActBytes

cuuint32_t
                              * CUmemDecompressParams::dstActBytes [inherited]
After the decompression operation has completed, the actual number of bytes written to CUmemDecompressParams.dst will be recorded as a 32-bit unsigned integer in the memory at this address.

size_t  CUmemDecompressParams::dstNumBytes [inherited]
The number of bytes that the decompression operation will be expected to write to CUmemDecompressParams_st.dst. This value
                                 is optional; if present, it may be used by the CUDA driver as a heuristic for scheduling the individual decompression operations.

const

                              void
                              * CUmemDecompressParams::src [inherited]
Pointer to a buffer of at least CUmemDecompressParams_st.srcNumBytes compressed bytes.

size_t  CUmemDecompressParams::srcNumBytes [inherited]
The number of bytes to be read and decompressed from CUmemDecompressParams_st.src.


---