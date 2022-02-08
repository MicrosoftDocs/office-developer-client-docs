---
title: "ITnefFinishComponent"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- ITnef.FinishComponent
api_type:
- COM
ms.assetid: bcdd0688-0897-47d7-9601-f592ba453b39
description: "Last modified: July 23, 2011"
---

# ITnef::FinishComponent

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Processes individual components from a message one at a time into a Transport-Neutral Encapsulation Format (TNEF) stream.
  
```cpp
HRESULT FinishComponent(
  ULONG ulFlags,
  ULONG ulComponentID,
  LPSPropTagArray lpCustomPropList,
  LPSPropValue lpCustomProps,
  LPSPropTagArray lpPropList,
  LPSTnefProblemArray FAR * lppProblems
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls which component will be finished. One or the other of the following flags must be set:
    
TNEF_COMPONENT_ATTACHMENT 
  
> Processing will be finished for an attachment object; the  _ulComponentID_ parameter contains the **PR_ATTACH_NUM** ([PidTagAttachNumber](pidtagattachnumber-canonical-property.md)) property of the attachment. 
    
TNEF_COMPONENT_MESSAGE 
  
> Processing will be finished for a message object. 
    
 _ulComponentID_
  
> [in] 0 to indicate processing for a message, or the **PR_ATTACH_NUM** property of an attachment to be processed. If the TNEF_COMPONENT_MESSAGE flag is set in the _ulFlags_ parameter,  _ulComponentID_ must be 0. 
    
 _lpCustomPropList_
  
> [in] A pointer to an [SPropTagArray](sproptagarray.md) structure that contains property tags that identify the properties passed in the _lpCustomProps_ parameter. There must be a one-to-one correspondence between each property value in  _lpCustomProps_ and a property tag in the _lpCustomPropList_ parameter. 
    
 _lpCustomProps_
  
> [in] A pointer to an [SPropValue](spropvalue.md) structure that contains property values for the properties to encode. 
    
 _lpPropList_
  
> [in] A pointer to an **SPropTagArray** structure that contains property tags for the properties to encode. 
    
 _lppProblems_
  
> [out] A pointer to a pointer to a returned [STnefProblemArray](stnefproblemarray.md) structure. The **STnefProblemArray** structure indicates which properties, if any, were not encoded properly. If NULL is passed in the _lppProblems_ parameter, no property problem array is returned. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Transport providers, message store providers, and gateways call the **ITnef::FinishComponent** method to perform TNEF processing for one component, either a message or an attachment, as indicated by the flag set in the _ulFlags_ parameter. 
  
For component processing to be enabled, the calling provider or gateway pass the TNEF_COMPONENT_ENCODING flag in  _ulFlags_ for the [OpenTnefStream](opentnefstream.md) or [OpenTnefStreamEx](opentnefstreamex.md) function that opened the object to receive encoding. 
  
Passing values in the _lpCustomPropList_ and  _lpCustomProps_ parameters performs component encoding equivalent to that done by the [ITnef::SetProps](itnef-setprops.md) method. Passing a value in the _lpPropList_ parameter performs component encoding equivalent to that done by the [ITnef::AddProps](itnef-addprops.md) method with the TNEF_PROP_INCLUDE flag set in  _ulFlags_. Passing these values enables you to perform encodings with a single call instead of multiple calls.
  
The TNEF implementation reports TNEF stream encoding problems without stopping the **FinishComponent** process. The **STnefProblemArray** structure returned in  _lppProblems_ indicates which TNEF attributes or MAPI properties, if any, could not be processed. The value returned in the **scode** member of the one of the **STnefProblem** structures contained in **STnefProblemArray** indicates the specific problem. The provider or gateway can work on the assumption that all properties or attributes for which **FinishComponent** does not return a problem report were processed successfully. 
  
If a provider or gateway does not work with problem arrays, it can pass NULL in  _lppProblems_; in this case, no problem array is returned.
  
The value returned in  _lppProblems_ is valid only if the call returns S_OK. When S_OK is returned, the provider or gateway should check the values returned in the [STnefProblemArray](stnefproblemarray.md) structure. If an error occurs on the call, the **STnefProblemArray** structure is not filled in, and the calling provider or gateway should not use or free the structure. If no error occurs on the call, the calling provider or gateway must release the memory for the **STnefProblemArray** by calling the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
## See also



[ITnef::AddProps](itnef-addprops.md)
  
[ITnef::SetProps](itnef-setprops.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[OpenTnefStream](opentnefstream.md)
  
[OpenTnefStreamEx](opentnefstreamex.md)
  
[SPropTagArray](sproptagarray.md)
  
[STnefProblemArray](stnefproblemarray.md)
  
[ITnef : IUnknown](itnefiunknown.md)

