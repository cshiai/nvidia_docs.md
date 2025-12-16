# 7.1. CUpti_Activity


struct CUpti_Activity
The base activity record.
The activity API uses a CUpti_Activity as a generic representation for any activity. The ‘kind’ field is used to determine the specific activity kind, and from that the CUpti_Activity object can be cast to the specific activity record type appropriate for that kind.
Note that all activity record types are padded and aligned to ensure that each member of the record is naturally aligned.

See also
CUpti_ActivityKind

Public Members

CUpti_ActivityKind kind
The kind of this activity.