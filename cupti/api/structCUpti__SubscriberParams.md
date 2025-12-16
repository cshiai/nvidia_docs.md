# 7.204. CUpti_SubscriberParams


struct CUpti_SubscriberParams
Params for cuptiSubscribe_v2.

Public Members

size_t structSize
Size of the data structure.
CUPTI client should set the size of the structure. It will be used in CUPTI to check what fields are available in the structure. Used to preserve backward compatibility.

const char *subscriberName
Name given to the subscriber.
The subscriber name need not include the “CUPTI” prefix, as the CUPTI library automatically adds it as “CUPTI for <subscriberName>”. Can be NULL. An internal copy is created. Size must not exceed CUPTI_SUBSCRIBER_NAME_MAX_LEN to avoid truncation.

char *oldSubscriberName
In case of CUPTI_ERROR_MULTIPLE_SUBSCRIBERS_NOT_SUPPORTED return code, the name of the incompatible tool or the existing CUPTI subscriber will be written to this location.
Size should be greater than or equal to CUPTI_OLD_SUBSCRIBER_NAME_MIN_LEN to avoid truncation. Can be NULL.

size_t oldSubscriberSize
Size of oldSubscriberName.
Minimum size should be CUPTI_OLD_SUBSCRIBER_NAME_MIN_LEN to avoid truncation.