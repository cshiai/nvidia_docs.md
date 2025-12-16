# 7.95. CUpti_ActivityOverheadCommandBufferFullData


struct CUpti_ActivityOverheadCommandBufferFullData
The structure to provide additional data for CUPTI_ACTIVITY_OVERHEAD_COMMAND_BUFFER_FULL.

Public Members

uint32_t commandBufferLength
The remaining space in the command buffer.
This field will always be zero when the command buffer is full, making it not useful in such cases.

uint32_t channelID
The channel ID of the command buffer.

uint32_t channelType
The channel type of the command buffer.