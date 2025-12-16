# 7.25. CUpti_ActivityExternalCorrelation


struct CUpti_ActivityExternalCorrelation
The activity record for correlation with external records.
This activity record correlates native CUDA records (e.g. CUDA Driver API, kernels, memcpys, …) with records from external APIs such as OpenACC. (CUPTI_ACTIVITY_KIND_EXTERNAL_CORRELATION).

See also
CUpti_ActivityKind

Public Members

CUpti_ActivityKind kind
The kind of this activity.

CUpti_ExternalCorrelationKind externalKind
The kind of external API this record correlated to.

uint64_t externalId
The correlation ID of the associated non-CUDA API record.
The exact field in the associated external record depends on that record’s activity kind (
See also
externalKind).

uint32_t correlationId
The correlation ID of the associated CUDA driver or runtime API record.

uint32_t reserved
Undefined.
Reserved for internal use.