# 7.22. CUpti_ActivityEnvironment


struct CUpti_ActivityEnvironment
The activity record for CUPTI environmental data.
This activity record provides CUPTI environmental data, include power, clocks, and thermals. This information is sampled at various rates and returned in this activity record. The consumer of the record needs to check the environmentKind field to figure out what kind of environmental record this is.

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_ENVIRONMENT.

uint32_t deviceId
The ID of the device.

uint64_t timestamp
The timestamp when this sample was retrieved, in ns.
A value of 0 indicates that timestamp information could not be collected for the marker.

CUpti_ActivityEnvironmentKind environmentKind
The kind of data reported in this record.

uint32_t smClock
The SM frequency in MHz.

uint32_t memoryClock
The memory frequency in MHz.

uint32_t pcieLinkGen
The PCIe link generation.

uint32_t pcieLinkWidth
The PCIe link width.

CUpti_EnvironmentClocksThrottleReason clocksThrottleReasons
The clocks throttle reasons.

struct CUpti_ActivityEnvironment::[anonymous]::[anonymous] speed
Data returned for CUPTI_ACTIVITY_ENVIRONMENT_SPEED environment kind.

uint32_t gpuTemperature
The GPU temperature in degrees C.

struct CUpti_ActivityEnvironment::[anonymous]::[anonymous] temperature
Data returned for CUPTI_ACTIVITY_ENVIRONMENT_TEMPERATURE environment kind.

struct CUpti_ActivityEnvironment::[anonymous]::[anonymous] power
Data returned for CUPTI_ACTIVITY_ENVIRONMENT_POWER environment kind.
The power in milliwatts consumed by GPU and associated circuitry. The power in milliwatts that will trigger power management algorithm.

uint32_t fanSpeed
The fan speed as percentage of maximum.

struct CUpti_ActivityEnvironment::[anonymous]::[anonymous] cooling
Data returned for CUPTI_ACTIVITY_ENVIRONMENT_COOLING environment kind.