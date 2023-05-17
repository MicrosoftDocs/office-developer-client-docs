---
title: "ITnefSetProps"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- ITnef.SetProps
api_type:
- COM
ms.assetid: 09e4b427-316b-4630-9f3d-81e74f040d7b
---

# ITnef::SetProps

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets the value of one or more properties for an encapsulated message or attachment without modifying the original message or attachment. 
  
```cpp
HRESULT SetProps(
  ULONG ulFlags,
  ULONG ulElemID,
  ULONG cValues,
  LPSPropValue lpProps
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls how property values are set. The following flag can be set:
    
TNEF_PROP_CONTAINED 
  
> Encodes only properties from the message or attachment specified by the  _ulElemID_ parameter. 
    
 _ulElemID_
  
> [in] An attachment's **PR_ATTACH_NUM** ([PidTagAttachNumber](pidtagattachnumber-canonical-property.md)) property, which contains a number that uniquely identifies the attachment in its parent message.
    
 _cValues_
  
> [in] The number of property values in the [SPropValue](spropvalue.md) structure pointed to by the  _lpProps_ parameter. 
    
 _lpProps_
  
> [in] A pointer to an **SPropValue** structure that contains the property values of the properties to set. 
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
## Remarks

Transport providers, message store providers, and gateways call the **ITnef::SetProps** method to set properties to include in the encapsulation of a message or an attachment without modifying the original message or attachment. Any properties set with this call override existing properties in the encapsulated message. 
  
 **SetProps** is supported only for TNEF objects that are opened with the TNEF_ENCODE flag for the [OpenTnefStream](opentnefstream.md) or [OpenTnefStreamEx](opentnefstreamex.md) function. Any number of properties can be set with this call. 
  
> [!NOTE]
> No actual TNEF encoding for **SetProps** happens until after the [ITnef::Finish](itnef-finish.md) method is called. This functionality means that pointers passed into **SetProps** must remain valid until after the call to **Finish** is made. At that point, all objects and data passed into **SetProps** calls can be released or freed. 
  
## See also



[ITnef::Finish](itnef-finish.md)
  
[OpenTnefStream](opentnefstream.md)
  
[OpenTnefStreamEx](opentnefstreamex.md)
  
[PidTagAttachNumber Canonical Property](pidtagattachnumber-canonical-property.md)
  
[SPropValue](spropvalue.md)
  
[ITnef : IUnknown](itnefiunknown.md)

