# Sanitizer_ResourceMempoolData


struct Sanitizer_ResourceMempoolData
Data passed into a mempool resource callback function.
Data passed into a mempool resource callback function as the cbdata argument to Sanitizer_CallbackFunc. The cbdata will be this type for domain equal to SANITIZER_CB_DOMAIN_RESOURCE and cbid equal to SANITIZER_CBID_RESOURCE_MEMPOOL_CREATED, SANITIZER_CBID_RESOURCE_MEMPOOL_DESTROYING, SANITIZER_CBID_RESOURCE_MEMPOOL_PEER_ACCESS_ENABLED or SANITIZER_CBID_RESOURCE_MEMPOOL_PEER_ACCESS_DISABLING. The callback data is only valid within the invocation of the callback function that is passed the data. If you need to retain some data for use outside of the callback, you must make a copy of it.

Public Members

CUdevice device
Device that owns the memory pool.

CUmemoryPool memoryPool
Memory pool being created or destroyed.

CUdevice peerDevice
Device that access type changed.
Available if cbid is SANITIZER_CBID_RESOURCE_MEMPOOL_PEER_ACCESS_ENABLED or SANITIZER_CBID_RESOURCE_MEMPOOL_PEER_ACCESS_DISABLING.