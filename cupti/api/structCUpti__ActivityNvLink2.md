# 7.83. CUpti_ActivityNvLink2


struct CUpti_ActivityNvLink2
NVLink information.
(deprecated in CUDA 10.0)
This structure gives capabilities of each logical NVLink connection between two devices, gpu<->gpu or gpu<->CPU which can be used to understand the topology. NvLink information are now reported using the CUpti_ActivityNvLink4 activity record.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_NVLINK.

uint32_t nvlinkVersion
NvLink version.

CUpti_DevType typeDev0
Type of device 0 CUpti_DevType.

CUpti_DevType typeDev1
Type of device 1 CUpti_DevType.

uint32_t index
Index of the NPU.
First index will always be zero.

uint32_t domainId
Domain ID of NPU.
On Linux, this can be queried using lspci.

union CUpti_ActivityNvLink2::[anonymous] idDev0
If typeDev0 is CUPTI_DEV_TYPE_GPU, UUID for device 0.
CUpti_ActivityDevice5. If typeDev0 is CUPTI_DEV_TYPE_NPU, struct npu for NPU.

union CUpti_ActivityNvLink2::[anonymous] idDev1
If typeDev1 is CUPTI_DEV_TYPE_GPU, UUID for device 1.
CUpti_ActivityDevice5. If typeDev1 is CUPTI_DEV_TYPE_NPU, struct npu for NPU.

uint32_t flag
Flag gives capabilities of the link.

See also
CUpti_LinkFlag

uint32_t physicalNvLinkCount
Number of physical NVLinks present between two devices.

int8_t portDev0[CUPTI_MAX_NVLINK_PORTS]
Port numbers for maximum 16 NVLinks connected to device 0.
If typeDev0 is CUPTI_DEV_TYPE_NPU, ignore this field. In case of invalid/unknown port number, this field will be set to value CUPTI_NVLINK_INVALID_PORT. This will be used to correlate the metric values to individual physical link and attribute traffic to the logical NVLink in the topology.

int8_t portDev1[CUPTI_MAX_NVLINK_PORTS]
Port numbers for maximum 16 NVLinks connected to device 1.
If typeDev1 is CUPTI_DEV_TYPE_NPU, ignore this field. In case of invalid/unknown port number, this field will be set to value CUPTI_NVLINK_INVALID_PORT. This will be used to correlate the metric values to individual physical link and attribute traffic to the logical NVLink in the topology.

uint64_t bandwidth
Bandwidth of NVLink in kbytes/sec.