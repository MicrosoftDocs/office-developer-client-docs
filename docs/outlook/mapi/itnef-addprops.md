---
title: "ITnefAddProps"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- ITnef.AddProps
api_type:
- COM
ms.assetid: e85641fb-6d3c-494a-981c-01781c7bf5bb
description: "Last modified: March 09, 2015"
---

# ITnef::AddProps

  
  
**Applies to**: Outlook 
  
Enables the calling service provider or gateway to add properties to the encapsulation of a message or an attachment. 
  
```cpp
HRESULT AddProps(
  ULONG ulFlags,
  ULONG ulElemID,
  LPVOID lpvData,
  LPSPropTagArray lpPropList
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls how properties are included in or excluded from encapsulation. The following flags can be set:
    
TNEF_PROP_ATTACHMENTS_ONLY 
  
> Encodes only the properties in the  _lpPropList_ parameter that are part of attachments in the message. 
    
TNEF_PROP_CONTAINED 
  
> Encodes only properties from the attachment specified by the  _ulElemID_ parameter. If the  _lpvData_ parameter is not NULL, the data pointed to is written into the attachment's encapsulation in the file indicated by the **PR_ATTACH_TRANSPORT_NAME** ([PidTagAttachTransportName](pidtagattachtransportname-canonical-property.md)) property.
    
TNEF_PROP_CONTAINED_TNEF 
  
> Encodes only properties from the message or attachment specified by the  _ulElemID_ parameter. If this flag is set, the value in  _lpvData_ must be an [IStream](http://msdn.microsoft.com/library/stg.istream%28Office.15%29.aspx) pointer. 
    
TNEF_PROP_EXCLUDE 
  
> Encodes all properties not specified in the  _lpPropList_ parameter. 
    
TNEF_PROP_INCLUDE 
  
> Encodes all properties specified in  _lpPropList_. 
    
TNEF_PROP_MESSAGE_ONLY 
  
> Encodes only those properties specified in  _lpPropList_ that are part of the message itself. 
    
 _ulElemID_
  
> [in] An attachment's **PR_ATTACH_NUM** ([PidTagAttachNumber](pidtagattachnumber-canonical-property.md)) property, which contains a number that uniquely identifies the attachment in its parent message. The  _ulElemID_ parameter is used when special handling is requested for an attachment. The  _ulElemID_ parameter should be 0 unless the TNEF_PROP_CONTAINED or TNEF_PROP_CONTAINED_TNEF flag is set in the  _ulFlags_ parameter. 
    
 _lpvData_
  
> [in] A pointer to attachment data used to replace the data of the attachment specified in  _ulElemID_. The  _lpvData_ parameter should be NULL unless TNEF_PROP_CONTAINED or TNEF_PROP_CONTAINED_TNEF is set in  _ulFlags_.
    
 _lpPropList_
  
> [in] A pointer to the list of properties to include in or exclude from encapsulation.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Transport providers, message store providers, and gateways call the **ITnef::AddProps** method to list properties to be included in or excluded from the Transport-Neutral Encapsulation Format (TNEF) processing of a message or an attachment. By using successive calls, the provider or gateway can specify a list of properties to add and encode or to exclude from being encoded. Providers and gateways can also use **AddProps** to provide information about any special handling attachments should be given. 
  
 **AddProps** is supported only for TNEF objects that are opened with the TNEF_ENCODE flag for the [OpenTnefStream](opentnefstream.md) or [OpenTnefStreamEx](opentnefstreamex.md) function. 
  
Note that no actual TNEF encoding happens for **AddProps** until the [ITnef::Finish](itnef-finish.md) method is called. This functionality means that pointers passed into **AddProps** must remain valid until after the call to **Finish** is made. At that point, all objects and data passed in with **AddProps** calls can be released or freed. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|File.cpp  <br/> |SaveToTNEF  <br/> |MFCMAPI uses the **ITnef::AddProps** method to copy properties from a message to a TNEF stream.  <br/> |
   
## See also



[ITnef::Finish](itnef-finish.md)
  
[OpenTnefStream](opentnefstream.md)
  
[OpenTnefStreamEx](opentnefstreamex.md)
  
[PidTagAttachTransportName Canonical Property](pidtagattachtransportname-canonical-property.md)
  
[ITnef : IUnknown](itnefiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

