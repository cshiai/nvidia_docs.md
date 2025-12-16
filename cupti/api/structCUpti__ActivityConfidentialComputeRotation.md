# 7.8. CUpti_ActivityConfidentialComputeRotation


struct CUpti_ActivityConfidentialComputeRotation
Event related to confidential compute encryption rotation.
This structure gives timestamps for stages of encryption rotation

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_CONFIDENTIAL_COMPUTE_ROTATION.

CUpti_ConfidentialComputeRotationEventType eventType
Type of event CUpti_ConfidentialComputeRotationEventType.

uint32_t deviceId
Device ID.

uint32_t contextId
Context ID.

uint32_t channelId
Channel ID.

CUpti_ChannelType channelType
Channel Type CUpti_ChannelType.

uint64_t timestamp
Timestamp in ns.