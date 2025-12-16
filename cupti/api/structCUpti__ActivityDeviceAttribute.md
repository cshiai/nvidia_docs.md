# 7.20. CUpti_ActivityDeviceAttribute


struct CUpti_ActivityDeviceAttribute
The activity record for a device attribute.
This activity record represents information about a GPU device: either a CUpti_DeviceAttribute or CUdevice_attribute value (CUPTI_ACTIVITY_KIND_DEVICE_ATTRIBUTE).

Public Members

CUpti_ActivityKind kind
The activity record kind, must be CUPTI_ACTIVITY_KIND_DEVICE_ATTRIBUTE.

CUpti_ActivityFlag flags
The flags associated with the device.

See also
CUpti_ActivityFlag

uint32_t deviceId
The ID of the device that this attribute applies to.

union CUpti_ActivityDeviceAttribute::[anonymous] attribute
The attribute, either a CUpti_DeviceAttribute or CUdevice_attribute.
Flag CUPTI_ACTIVITY_FLAG_DEVICE_ATTRIBUTE_CUDEVICE is used to indicate what kind of attribute this is. If CUPTI_ACTIVITY_FLAG_DEVICE_ATTRIBUTE_CUDEVICE is 1 then CUdevice_attribute field is value, otherwise CUpti_DeviceAttribute field is valid.

union CUpti_ActivityDeviceAttribute::[anonymous] value
The value for the attribute.
See CUpti_DeviceAttribute and CUdevice_attribute for the type of the value for a given attribute.