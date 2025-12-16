# CUDA Driver API

[< Previous](group__CUDA__LOGS.html) | [Next >](group__CUDA__PROFILER__DEPRECATED.html)  CUDA Driver API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Driver_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20CUDA%20Driver%20API)
## 6.37. CUDA Checkpointing


CUDA API versioning support


This sections describes the checkpoint and restore functions of the low-level CUDA driver application programming interface.


The CUDA checkpoint and restore API's provide a way to save and restore GPU state for full process checkpoints when used with CPU side process checkpointing solutions. They can also be used to pause GPU work and suspend a CUDA process to allow other applications to make use of GPU resources.


Checkpoint and restore capabilities are currently restricted to Linux.


### Functions


CUresult cuCheckpointProcessCheckpoint (  int  pid, CUcheckpointCheckpointArgs* args )
Checkpoint a CUDA process's GPU memory contents.

CUresult cuCheckpointProcessGetRestoreThreadId (  int  pid, int* tid )
Returns the restore thread ID for a CUDA process.

CUresult cuCheckpointProcessGetState (  int  pid, CUprocessState* state )
Returns the process state of a CUDA process.

CUresult cuCheckpointProcessLock (  int  pid, CUcheckpointLockArgs* args )
Lock a running CUDA process.

CUresult cuCheckpointProcessRestore (  int  pid, CUcheckpointRestoreArgs* args )
Restore a CUDA process's GPU memory contents from its last checkpoint.

CUresult cuCheckpointProcessUnlock (  int  pid, CUcheckpointUnlockArgs* args )
Unlock a CUDA process to allow CUDA API calls.


### Functions


CUresult cuCheckpointProcessCheckpoint (  int  pid, CUcheckpointCheckpointArgs* args )
Checkpoint a CUDA process's GPU memory contents.

                                 Parameters



pid
- The process ID of the CUDA process
args
- Optional checkpoint operation arguments

Returns
CUDA_SUCCESSCUDA_ERROR_INVALID_VALUECUDA_ERROR_NOT_INITIALIZEDCUDA_ERROR_ILLEGAL_STATECUDA_ERROR_NOT_SUPPORTED

Description
Checkpoints a CUDA process specified by pid that is in the LOCKED state. The GPU memory contents will be brought into host memory and all underlying references will
                                 be released. Process must be in the LOCKED state to checkpoint.

Upon successful return the process will be in the CHECKPOINTED state.

CUresult cuCheckpointProcessGetRestoreThreadId (  int  pid, int* tid )
Returns the restore thread ID for a CUDA process.

                                 Parameters



pid
- The process ID of the CUDA process
tid
- Returned restore thread ID

Returns
CUDA_SUCCESSCUDA_ERROR_INVALID_VALUECUDA_ERROR_NOT_INITIALIZEDCUDA_ERROR_NOT_SUPPORTED

Description
Returns in *tid the thread ID of the CUDA restore thread for the process specified by pid.

CUresult cuCheckpointProcessGetState (  int  pid, CUprocessState* state )
Returns the process state of a CUDA process.

                                 Parameters



pid
- The process ID of the CUDA process
state
- Returned CUDA process state

Returns
CUDA_SUCCESSCUDA_ERROR_INVALID_VALUECUDA_ERROR_NOT_INITIALIZEDCUDA_ERROR_NOT_SUPPORTED

Description
Returns in *state the current state of the CUDA process specified by pid.

CUresult cuCheckpointProcessLock (  int  pid, CUcheckpointLockArgs* args )
Lock a running CUDA process.

                                 Parameters



pid
- The process ID of the CUDA process
args
- Optional lock operation arguments

Returns
CUDA_SUCCESSCUDA_ERROR_INVALID_VALUECUDA_ERROR_NOT_INITIALIZEDCUDA_ERROR_ILLEGAL_STATECUDA_ERROR_NOT_SUPPORTEDCUDA_ERROR_NOT_READY

Description
Lock the CUDA process specified by pid which will block further CUDA API calls. Process must be in the RUNNING state in order to lock.

Upon successful return the process will be in the LOCKED state.
If timeoutMs is specified and the timeout is reached the process will be left in the RUNNING state upon return.

CUresult cuCheckpointProcessRestore (  int  pid, CUcheckpointRestoreArgs* args )
Restore a CUDA process's GPU memory contents from its last checkpoint.

                                 Parameters



pid
- The process ID of the CUDA process
args
- Optional restore operation arguments

Returns
CUDA_SUCCESSCUDA_ERROR_INVALID_VALUECUDA_ERROR_NOT_INITIALIZEDCUDA_ERROR_ILLEGAL_STATECUDA_ERROR_NOT_SUPPORTED

Description
Restores a CUDA process specified by pid from its last checkpoint. Process must be in the CHECKPOINTED state to restore.

GPU UUID pairs can be specified in args to remap the process old GPUs onto new GPUs. The GPU to restore onto needs to have enough memory and be of the same chip
                                 type as the old GPU. If an array of GPU UUID pairs is specified, it must contain every checkpointed GPU.

Upon successful return the process will be in the LOCKED state.
CUDA process restore requires persistence mode to be enabled or cuInit to have been called before execution.


See also:
cuInit

CUresult cuCheckpointProcessUnlock (  int  pid, CUcheckpointUnlockArgs* args )
Unlock a CUDA process to allow CUDA API calls.

                                 Parameters



pid
- The process ID of the CUDA process
args
- Optional unlock operation arguments

Returns
CUDA_SUCCESSCUDA_ERROR_INVALID_VALUECUDA_ERROR_NOT_INITIALIZEDCUDA_ERROR_ILLEGAL_STATECUDA_ERROR_NOT_SUPPORTED

Description
Unlocks a process specified by pid allowing it to resume making CUDA API calls. Process must be in the LOCKED state.

Upon successful return the process will be in the RUNNING state.


---