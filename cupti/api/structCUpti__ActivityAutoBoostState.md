# 7.3. CUpti_ActivityAutoBoostState


struct CUpti_ActivityAutoBoostState
Device auto boost state structure.
This structure defines auto boost state for a device. See function cuptiGetAutoBoostState

Public Members

uint32_t enabled
Returned auto boost state.
1 is returned in case auto boost is enabled, 0 otherwise

uint32_t pid
Id of process that has set the current boost state.
The value will be CUPTI_AUTO_BOOST_INVALID_CLIENT_PID if the user does not have the permission to query process ids or there is an error in querying the process id.