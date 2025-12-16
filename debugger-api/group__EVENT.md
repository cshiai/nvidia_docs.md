# Debugger API

[< Previous](group__DWARF.html) | [Next >](annotated.html)  Debugger API ([PDF](https://docs.nvidia.com/cuda/pdf/CUDA_Debugger_API.pdf)) - v13.1.0 ([older](https://developer.nvidia.com/cuda-toolkit-archive)) - Last updated December 4, 2025 - [Send Feedback](mailto:CUDAIssues@nvidia.com?subject=CUDA%20Toolkit%20Documentation%20Feedback:%20Debugger%20API)
## 3.10. Events


One of those events will create a [CUDBGEvent](structCUDBGEvent.html#structCUDBGEvent):


 - the elf image of the current kernel has been loaded and the addresses within its DWARF sections have been relocated (and can now be used to set breakpoints),
 - a device breakpoint has been hit,
 - a CUDA kernel is ready to be launched,
 - a CUDA kernel has terminated.

 When a [CUDBGEvent](structCUDBGEvent.html#structCUDBGEvent) is created, the debugger is notified by calling the callback functions registered with setNotifyNewEventCallback() after the API struct initialization. It is up to the debugger to decide what method is best to be notified. The debugger API routines cannot be called from within the callback function or the routine will return an error.
Upon notification the debugger is responsible for handling the CUDBGEvents in the event queue by using [CUDBGAPI_st::getNextEvent()](group__EVENT.html#group__EVENT_1g113afe93cd425b0ba69c96303354d130), and for acknowledging the debugger API that the event has been handled by calling CUDBGAPI_st::acknowledgeEvent(). In the case of an event raised by the device itself, such as a breakpoint being hit, the event queue will be empty. It is the responsibility of the debugger to inspect the hardware any time a [CUDBGEvent](structCUDBGEvent.html#structCUDBGEvent) is received.


Example:


```
‎CUDBGEvent event;
      CUDBGResult res;
      for (res = cudbgAPI->getNextEvent(&event);
           res == CUDBG_SUCCESS && event.kind != CUDBG_EVENT_INVALID;
           res = cudbgAPI->getNextEvent(&event)) {
          switch (event.kind)
              {
              case CUDBG_EVENT_ELF_IMAGE_LOADED:
                  //...
                  break;
              case CUDBG_EVENT_KERNEL_READY:
                  //...
                  break;
              case CUDBG_EVENT_KERNEL_FINISHED:
                  //...
                  break;
              default:
                  error(...);
              }
          }
```


See cuda-tdep.c and cuda-linux-nat.c files in the cuda-gdb source code for a more detailed example on how to use [CUDBGEvent](structCUDBGEvent.html#structCUDBGEvent).


### Classes


struct
CUDBGEvent
Event information container.

struct
CUDBGEventCallbackData
Event information passed to callback set with setNotifyNewEventCallback function.

struct
CUDBGEventCallbackData40
Event information passed to callback set with setNotifyNewEventCallback function.


### Typedefs


typedef
                           void
                            ( *CUDBGNotifyNewEventCallback )(  CUDBGEventCallbackData*
                            data )
function type of the function called to notify debugger of the presence of a new event in the event queue.

typedef
                           void
                            ( *CUDBGNotifyNewEventCallback31 )(  void*
                            data )
function type of the function called to notify debugger of the presence of a new event in the event queue.


### Enumerations


enum CUDBGEventKind
CUDA Kernel Events.


### Variables


CUDBGResult
                            ( *CUDBGAPI_st::acknowledgeEvent30 )(  CUDBGEvent30* event )
Inform the debugger API that the event has been processed.

CUDBGResult
                            ( *CUDBGAPI_st::acknowledgeEvents42 )(   )
Inform the debugger API that synchronous events have been processed.

CUDBGResult
                            ( *CUDBGAPI_st::acknowledgeSyncEvents )(   )
Inform the debugger API that synchronous events have been processed.

CUDBGResult
                            ( *CUDBGAPI_st::getErrorStringEx )(  char* buf, uint32_t bufSz, uint32_t* msgSz )
Fills a user-provided buffer with an error message encoded as a null-terminated ASCII string. The error message is specific
                           to the last failed API call and is invalidated after every API call.

CUDBGResult
                            ( *CUDBGAPI_st::getNextAsyncEvent50 )(  CUDBGEvent50* event )
Copies the next available event in the asynchronous event queue into 'event' and removes it from the queue. The asynchronous
                           event queue is held separate from the normal event queue, and does not require acknowledgement from the debug client.

CUDBGResult
                            ( *CUDBGAPI_st::getNextAsyncEvent55 )(  CUDBGEvent55* event )
Copies the next available event in the asynchronous event queue into 'event' and removes it from the queue. The asynchronous
                           event queue is held separate from the normal event queue, and does not require acknowledgement from the debug client.

CUDBGResult
                            ( *CUDBGAPI_st::getNextEvent )(  CUDBGEventQueueType type, CUDBGEvent* event )
Copies the next available event into 'event' and removes it from the queue.

CUDBGResult
                            ( *CUDBGAPI_st::getNextEvent30 )(  CUDBGEvent30* event )
Copies the next available event in the event queue into 'event' and removes it from the queue.

CUDBGResult
                            ( *CUDBGAPI_st::getNextEvent32 )(  CUDBGEvent32* event )
Copies the next available event in the event queue into 'event' and removes it from the queue.

CUDBGResult
                            ( *CUDBGAPI_st::getNextEvent42 )(  CUDBGEvent42* event )
Copies the next available event in the event queue into 'event' and removes it from the queue.

CUDBGResult
                            ( *CUDBGAPI_st::getNextSyncEvent50 )(  CUDBGEvent50* event )CUDBGResult
                            ( *CUDBGAPI_st::getNextSyncEvent55 )(  CUDBGEvent55* event )
Copies the next available event in the synchronous event queue into 'event' and removes it from the queue.

CUDBGResult
                            ( *CUDBGAPI_st::setNotifyNewEventCallback )(  CUDBGNotifyNewEventCallback callback, void* userData )
Provides the API with the function to call to notify the debugger of a new application or device event.

CUDBGResult
                            ( *CUDBGAPI_st::setNotifyNewEventCallback31 )(  CUDBGNotifyNewEventCallback31 callback, void* data )
Provides the API with the function to call to notify the debugger of a new application or device event.

CUDBGResult
                            ( *CUDBGAPI_st::setNotifyNewEventCallback40 )(  CUDBGNotifyNewEventCallback40 callback )
Provides the API with the function to call to notify the debugger of a new application or device event.

CUDBGResult
                            ( *CUDBGAPI_st::setNotifyNewEventCallback41 )(  CUDBGNotifyNewEventCallback41 callback )
Provides the API with the function to call to notify the debugger of a new application or device event.


### Typedefs


void
                              ( *CUDBGNotifyNewEventCallback )(  CUDBGEventCallbackData*
                               data )
function type of the function called to notify debugger of the presence of a new event in the event queue.

void
                              ( *CUDBGNotifyNewEventCallback31 )(  void*
                               data )
function type of the function called to notify debugger of the presence of a new event in the event queue.



Note:Deprecated in CUDA 3.2.


### Enumerations


enum CUDBGEventKind
Values



CUDBG_EVENT_INVALID = 0x000
Invalid event.
CUDBG_EVENT_ELF_IMAGE_LOADED = 0x001
The ELF image for a CUDA source module is available.
CUDBG_EVENT_KERNEL_READY = 0x002
A CUDA kernel is about to be launched.
CUDBG_EVENT_KERNEL_FINISHED = 0x003
A CUDA kernel has terminated.
CUDBG_EVENT_INTERNAL_ERROR = 0x004
An internal error occur. The debugging framework may be unstable.
CUDBG_EVENT_CTX_PUSH = 0x005
A CUDA context was pushed.
CUDBG_EVENT_CTX_POP = 0x006
A CUDA CTX was popped.
CUDBG_EVENT_CTX_CREATE = 0x007
A CUDA CTX was created.
CUDBG_EVENT_CTX_DESTROY = 0x008
A CUDA context was destroyed.
CUDBG_EVENT_TIMEOUT = 0x009
An timeout event is sent at regular interval. This event can safely ge ignored.
CUDBG_EVENT_ATTACH_COMPLETE = 0x00a
The attach process has completed and debugging of device code may start.
CUDBG_EVENT_DETACH_COMPLETE = 0x00b

CUDBG_EVENT_ELF_IMAGE_UNLOADED = 0x00c

CUDBG_EVENT_FUNCTIONS_LOADED = 0x00d

CUDBG_EVENT_ALL_DEVICES_SUSPENDED = 0x00e

CUDBG_EVENT_CUDA_LOGS_AVAILABLE = 0x00f

CUDBG_EVENT_CUDA_LOGS_THRESHOLD_REACHED = 0x010


### Variables


CUDBGResult
                              ( *CUDBGAPI_st::acknowledgeEvent30 )(  CUDBGEvent30* event )
Inform the debugger API that the event has been processed.  Since CUDA 3.0.

Note:Deprecated in CUDA 3.1.

                                 Parameters



event
- pointer to the event that has been processed

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::acknowledgeEvents42 )(   )
Inform the debugger API that synchronous events have been processed.  Since CUDA 3.1.

Note:Deprecated in CUDA 5.0.

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::acknowledgeSyncEvents )(   )
Inform the debugger API that synchronous events have been processed.  Since CUDA 5.0.

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::getErrorStringEx )(  char* buf, uint32_t bufSz, uint32_t* msgSz )
Fills a user-provided buffer with an error message encoded as a null-terminated ASCII string. The error message is specific
                                 to the last failed API call and is invalidated after every API call.  Since CUDA 12.2.


See also:
getErrorString

                                 Parameters



buf
- the destination buffer
bufSz
- the size of the destination buffer in bytes
msgSz
- the size of an error message including the terminating null character.

Returns
CUDBG_SUCCESS, CUDBG_ERROR_BUFFER_TOO_SMALL CUDBG_ERROR_INVALID_ARGS, CUDBG_ERROR_UNINITIALIZED

CUDBGResult
                              ( *CUDBGAPI_st::getNextAsyncEvent50 )(  CUDBGEvent50* event )
Copies the next available event in the asynchronous event queue into 'event' and removes it from the queue. The asynchronous
                                 event queue is held separate from the normal event queue, and does not require acknowledgement from the debug client.  Since
                                 CUDA 5.0.


Note:Deprecated in CUDA 5.5.

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextAsyncEvent55 )(  CUDBGEvent55* event )
Copies the next available event in the asynchronous event queue into 'event' and removes it from the queue. The asynchronous
                                 event queue is held separate from the normal event queue, and does not require acknowledgement from the debug client.  Since
                                 CUDA 5.5.


Note:Deprecated in CUDA 6.0.

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextEvent )(  CUDBGEventQueueType type, CUDBGEvent* event )
Copies the next available event into 'event' and removes it from the queue.  Since CUDA 6.0.

                                 Parameters



type
- application event queue type
event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextEvent30 )(  CUDBGEvent30* event )
Copies the next available event in the event queue into 'event' and removes it from the queue.  Since CUDA 3.0.

Note:Deprecated in CUDA 3.1.

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextEvent32 )(  CUDBGEvent32* event )
Copies the next available event in the event queue into 'event' and removes it from the queue.  Since CUDA 3.1.

Note:Deprecated in CUDA 4.0

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextEvent42 )(  CUDBGEvent42* event )
Copies the next available event in the event queue into 'event' and removes it from the queue.  Since CUDA 4.0.

Note:Deprecated in CUDA 5.0

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextSyncEvent50 )(  CUDBGEvent50* event )
Since CUDA 5.0.

Note:Deprecated in CUDA 5.5.

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::getNextSyncEvent55 )(  CUDBGEvent55* event )
Copies the next available event in the synchronous event queue into 'event' and removes it from the queue.  Since CUDA 5.5.

Note:Deprecated in CUDA 6.0.

                                 Parameters



event
- pointer to an event container where to copy the event parameters

Returns
CUDBG_SUCCESS, CUDBG_ERROR_NO_EVENT_AVAILABLE, CUDBG_ERROR_INVALID_ARGS

CUDBGResult
                              ( *CUDBGAPI_st::setNotifyNewEventCallback )(  CUDBGNotifyNewEventCallback callback, void* userData )
Provides the API with the function to call to notify the debugger of a new application or device event.  Since CUDA 13.0.

                                 Parameters



callback
- the callback function
userData
- user data to be passed to the callback

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::setNotifyNewEventCallback31 )(  CUDBGNotifyNewEventCallback31 callback, void* data )
Provides the API with the function to call to notify the debugger of a new application or device event.  Since CUDA 3.0.

Note:Deprecated in CUDA 3.2.

                                 Parameters



callback
- the callback function
data
- a pointer to be passed to the callback when called

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::setNotifyNewEventCallback40 )(  CUDBGNotifyNewEventCallback40 callback )
Provides the API with the function to call to notify the debugger of a new application or device event.  Since CUDA 3.2.

Note:Deprecated in CUDA 4.1.

                                 Parameters



callback
- the callback function

Returns
CUDBG_SUCCESS

CUDBGResult
                              ( *CUDBGAPI_st::setNotifyNewEventCallback41 )(  CUDBGNotifyNewEventCallback41 callback )
Provides the API with the function to call to notify the debugger of a new application or device event.  Since CUDA 4.1.

Note:Deprecated in CUDA 13.0.

                                 Parameters



callback
- the callback function

Returns
CUDBG_SUCCESS


---