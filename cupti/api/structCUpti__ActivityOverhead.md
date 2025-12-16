# 7.92. CUpti_ActivityOverhead


struct CUpti_ActivityOverhead
The kinds of activity records.
Each activity record kind represents information about a GPU or an activity occurring on a CPU or GPU. Each kind is associated with a activity record structure that holds the information associated with the kind.
The activity record for CUPTI and driver overheads. (Deprecated in CUDA 12.2)

See also
CUpti_ActivityOverhead

See also
CUpti_ActivityOverhead2

See also
CUpti_ActivityDevice

See also
CUpti_ActivityDevice2

See also
CUpti_ActivityDevice3

See also
CUpti_ActivityDevice4

See also
CUpti_ActivityKernel

See also
CUpti_ActivityKernel2

See also
CUpti_ActivityKernel3

See also
CUpti_ActivityKernel4

See also
CUpti_ActivityKernel5

See also
CUpti_ActivityKernel6

See also
CUpti_ActivityKernel7

See also
CUpti_ActivityKernel8

See also
CUpti_ActivityKernel9

See also
CUpti_ActivityKernel10

See also
CUpti_ActivityMemcpy

See also
CUpti_ActivityMemcpy3

See also
CUpti_ActivityMemcpy4

See also
CUpti_ActivityMemcpyPtoP

See also
CUpti_ActivityMemcpyPtoP2

See also
CUpti_ActivityMemcpyPtoP3

See also
CUpti_ActivityMemset

See also
CUpti_ActivityMemset2

See also
CUpti_ActivityMemset3

See also
CUpti_ActivityMemory2

See also
CUpti_ActivityMemory3

See also
CUpti_ActivityMemoryPool

See also
CUpti_ActivityMarker

See also
CUpti_ActivityGlobalAccess

See also
CUpti_ActivityGlobalAccess2

See also
CUpti_ActivityBranch

See also
CUpti_ActivityPCSampling

See also
CUpti_ActivityPCSampling2

See also
CUpti_ActivityUnifiedMemoryCounter

See also
CUpti_ActivityUnifiedMemoryCounter2

See also
CUpti_ActivityNvLink

See also
CUpti_ActivityNvLink2

See also
CUpti_ActivityNvLink3

This activity record provides CUPTI and driver overhead information (CUPTI_ACTIVITY_OVERHEAD). These records are now reported using CUpti_ActivityOverhead3

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_OVERHEAD.

CUpti_ActivityOverheadKind overheadKind
The kind of overhead, CUPTI, DRIVER, COMPILER etc.

CUpti_ActivityObjectKind objectKind
The kind of activity object that the overhead is associated with.

CUpti_ActivityObjectKindId objectId
The identifier for the activity object.
‘objectKind’ indicates which ID is valid for this record.

uint64_t start
The start timestamp for the overhead, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the overhead.

uint64_t end
The end timestamp for the overhead, in ns.
A value of 0 for both the start and end timestamps indicates that timestamp information could not be collected for the overhead.