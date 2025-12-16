# 8.2.1.1.1. CUpti_Checkpoint


Fully qualified name: `NV::Cupti::Checkpoint::CUpti_Checkpoint`


struct CUpti_Checkpoint
Configuration and handle for a CUPTI Checkpoint.
A CUptiCheckpoint object should be initialized with desired options prior to passing into any CUPTI Checkpoint API function. The first call into a Checkpoint API function will initialize internal state based on these options. Subsequent changes to these options will not have any effect.
Checkpoint data is saved in device, host, and filesystem space. There are options to reserve memory at each level (device, host, filesystem) which are intended to allow a guarantee that a certain amount of memory will remain free for use after the checkpoint is saved. Note, however, that falling back to slower levels of memory (host, and then filesystem) to save the checkpoint will result in performance degradation. Currently, the filesystem limitation is not implemented. Note that falling back to filesystem storage may significantly impact the performance for saving and restoring a checkpoint.

Public Members

size_t structSize
[in] Must be set to CUpti_Checkpoint_STRUCT_SIZE

CUcontext ctx
[in] Set to context to save from, or will use current context if NULL

size_t reserveDeviceMB
[in] Restrict checkpoint from using last N MB of device memory (-1 = use no device memory)

size_t reserveHostMB
[in] Restrict checkpoint from using last N MB of host memory (-1 = use no host memory)

uint8_t allowOverwrite
[in] Boolean, Allow checkpoint to save over existing checkpoint

uint8_t optimizations
[in] Mask of CUpti_CheckpointOptimizations flags for this checkpoint

void *pPriv
[in] Assign to NULL