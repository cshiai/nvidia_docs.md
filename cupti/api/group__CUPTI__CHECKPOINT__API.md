# 6.3. CUPTI Checkpoint API


Functions, types, and enums that implement the CUPTI Checkpoint API.


## 6.3.1. Data Structures


NV::Cupti::Checkpoint::CUpti_Checkpoint
Configuration and handle for a CUPTI Checkpoint.


## 6.3.2. Macros


CUpti_Checkpoint_STRUCT_SIZE

## 6.3.3. Enumerations


NV::Cupti::Checkpoint::CUpti_CheckpointOptimizations
Specifies optimization options for a checkpoint, may be OR'd together to specify multiple options.


## 6.3.4. Functions


CUptiResult NV::Cupti::Checkpoint::cuptiCheckpointFree(CUpti_Checkpoint *const handle)
Free the backing data for a checkpoint.

CUptiResult NV::Cupti::Checkpoint::cuptiCheckpointRestore(CUpti_Checkpoint *const handle)
Restore a checkpoint to the device associated with its context.

CUptiResult NV::Cupti::Checkpoint::cuptiCheckpointSave(CUpti_Checkpoint *const handle)
Initialize and save a checkpoint of the device state associated with the handle context.


## 6.3.5. Macros


CUpti_Checkpoint_STRUCT_SIZE

## 6.3.6. Enumerations


enum NV::Cupti::Checkpoint::CUpti_CheckpointOptimizations
Specifies optimization options for a checkpoint, may be OR’d together to specify multiple options.
Values:

enumerator CUPTI_CHECKPOINT_OPT_NONE
Default behavior.

enumerator CUPTI_CHECKPOINT_OPT_TRANSFER
Determine which mem blocks have changed, and only restore those. This optimization is cached, which means cuptiCheckpointRestore must always be called at the same point in the application when this option is enabled, or the result may be incorrect.


## 6.3.7. Functions


CUptiResult NV::Cupti::Checkpoint::cuptiCheckpointFree(

CUpti_Checkpoint *const handle,

)
Free the backing data for a checkpoint.
Frees all associated device, host memory and filesystem storage used for this context. After freeing a handle, it may be re-used as if it was new - options may be re-configured and will take effect on the next call to cuptiCheckpointSave.

Parameters:
handle – A pointer to a previously saved CUpti_Checkpoint object

Return values:

CUPTI_SUCCESS – if the handle was successfully freed
CUPTI_ERROR_INVALID_PARAMETER – if the handle was already freed or appears invalid
CUPTI_ERROR_INVALID_CONTEXT – if the context is no longer valid


CUptiResult NV::Cupti::Checkpoint::cuptiCheckpointRestore(

CUpti_Checkpoint *const handle,

)
Restore a checkpoint to the device associated with its context.
Restores device, pinned, and allocated memory to the state when the checkpoint was saved

Parameters:
handle – A pointer to a previously saved CUpti_Checkpoint object

Return values:

CUTPI_SUCCESS – if the checkpoint was successfully restored
CUPTI_ERROR_NOT_INITIALIZED – if the checkpoint was not previously initialized
CUPTI_ERROR_INVALID_CONTEXT –
CUPTI_ERROR_INVALID_PARAMETER – if the handle appears invalid
CUPTI_ERROR_UNKNOWN – if the restore or optimization operation fails


CUptiResult NV::Cupti::Checkpoint::cuptiCheckpointSave(

CUpti_Checkpoint *const handle,

)
Initialize and save a checkpoint of the device state associated with the handle context.
Uses the handle options to configure and save a checkpoint of the device state associated with the specified context.

Parameters:
handle – A pointer to a CUpti_Checkpoint object

Return values:

CUPTI_SUCCESS – if a checkpoint was successfully initialized and saved
CUPTI_ERROR_INVALID_PARAMETER – if handle does not appear to refer to a valid CUpti_Checkpoint
CUPTI_ERROR_INVALID_CONTEXT –
CUPTI_ERROR_INVALID_DEVICE – if device associated with context is not compatible with checkpoint API
CUPTI_ERROR_INVALID_OPERATION – if Save is requested over an existing checkpoint, but allowOverwrite was not originally specified
CUPTI_ERROR_OUT_OF_MEMORY – if as configured, not enough backing storage space to save the checkpoint