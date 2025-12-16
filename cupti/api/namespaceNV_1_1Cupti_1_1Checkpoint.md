# 8.2.1.1. Checkpoint


Fully qualified name: `NV::Cupti::Checkpoint`


namespace Checkpoint

## 8.2.1.1.2. Data Structures


CUpti_Checkpoint
Configuration and handle for a CUPTI Checkpoint.


## 8.2.1.1.3. Enumerations


CUpti_CheckpointOptimizations
Specifies optimization options for a checkpoint, may be OR'd together to specify multiple options.


## 8.2.1.1.4. Functions


CUptiResult cuptiCheckpointFree(CUpti_Checkpoint *const handle)
Free the backing data for a checkpoint.

CUptiResult cuptiCheckpointRestore(CUpti_Checkpoint *const handle)
Restore a checkpoint to the device associated with its context.

CUptiResult cuptiCheckpointSave(CUpti_Checkpoint *const handle)
Initialize and save a checkpoint of the device state associated with the handle context.