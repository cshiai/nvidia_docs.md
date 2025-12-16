# 7.101. CUpti_ActivityPcie


struct CUpti_ActivityPcie
PCI devices information required to construct topology.
This structure gives capabilities of GPU and PCI bridge connected to the PCIE bus which can be used to understand the topology.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_PCIE.

CUpti_PcieDeviceType type
Type of device in topology, CUpti_PcieDeviceType.
If type is CUPTI_PCIE_DEVICE_TYPE_GPU use devId for id and gpuAttr and if type is CUPTI_PCIE_DEVICE_TYPE_BRIDGE use bridgeId for id and bridgeAttr.

CUdevice devId
GPU device ID.

uint32_t bridgeId
A unique identifier for Bridge in the Topology.

union CUpti_ActivityPcie::[anonymous] id
A unique identifier for GPU or Bridge in Topology.

uint32_t domain
Domain for the GPU or Bridge, required to identify which PCIE bus it belongs to in multiple NUMA systems.

uint16_t pcieGeneration
PCIE Generation of GPU or Bridge.

uint16_t linkRate
Link rate of the GPU or bridge in gigatransfers per second (GT/s)

uint16_t linkWidth
Link width of the GPU or bridge.

uint16_t upstreamBus
Upstream bus ID for the GPU or PCI bridge.
Required to identify which bus it is connected to in the topology.

CUuuid uuidDev
UUID for the device.
CUpti_ActivityDevice5.

CUdevice peerDev[32]
CUdevice with which this device has P2P capability.
This can also be obtained by querying cuDeviceCanAccessPeer or cudaDeviceCanAccessPeer APIs

uint16_t secondaryBus
The downstream bus number, used to search downstream devices/bridges connected to this bridge.

uint16_t deviceId
Device ID of the bridge.

uint16_t vendorId
Vendor ID of the bridge.

uint16_t pad0
Padding for alignment.

union CUpti_ActivityPcie::[anonymous] attr
Attributes for more information about GPU (gpuAttr) or PCI Bridge (bridgeAttr)