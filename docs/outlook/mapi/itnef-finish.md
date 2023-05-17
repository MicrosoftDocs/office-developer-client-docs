---
title: "ITnefFinish"
description: "ITnefFinish finishes processing for all Transport-Neutral Encapsulation Format (TNEF) operations that are queued and waiting."
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- ITnef.Finish
api_type:
- COM
ms.assetid: 01a868f4-afda-43ba-bc17-c33ae56b7b7d
---

# ITnef::Finish

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Finishes processing for all Transport-Neutral Encapsulation Format (TNEF) operations that are queued and waiting. 
  
```cpp
HRESULT Finish(
  ULONG ulFlags,
  WORD FAR * lpKey,
  LPSTnefProblemArray FAR * lpProblem
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
 _lpKey_
  
> [out] A pointer to the **PR_ATTACH_NUM** ([PidTagAttachNumber](pidtagattachnumber-canonical-property.md)) key property of an attachment. The TNEF encapsulation object uses this key to match an attachment to its attachment placement tag in a message. This key should be unique to each attachment.
    
 _lpProblem_
  
> [out] A pointer to a pointer to a returned [STnefProblemArray](stnefproblemarray.md) structure. The **STnefProblemArray** structure indicates which properties, if any, were not encoded properly. If NULL is passed in the _lpProblem_ parameter, no property problem array is returned. 
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
## Remarks

Transport providers, message store providers, and gateways call the **ITnef::Finish** method to perform the encoding of all properties for which encoding was requested in calls to the [ITnef::AddProps](itnef-addprops.md) and [ITnef::SetProps](itnef-setprops.md) methods. If the TNEF object was opened with the TNEF_ENCODE flag for the [OpenTnefStream](opentnefstream.md) or [OpenTnefStreamEx](opentnefstreamex.md) function, the **Finish** method encodes the requested properties into the encapsulation stream passed to that object. If the TNEF object was opened with the TNEF_DECODE flag, the **Finish** method decodes the properties from the TNEF stream and writes them back to the message they belong to. 
  
After the **Finish** call, the pointer to the encapsulation stream points to the end of the TNEF data. If the provider or gateway needs to use the TNEF stream data after the **Finish** call, it must reset the stream pointer to the beginning of the TNEF stream data. 
  
The TNEF implementation reports TNEF stream encoding problems without stopping the **Finish** process. The [STnefProblemArray](stnefproblemarray.md) structure returned in the _lpProblem_ parameter indicates which TNEF attributes or MAPI properties, if any, could not be processed. The value returned in the **scode** member of the one of the **STnefProblem** structures contained in **STnefProblemArray** indicates the specific problem. The provider or gateway can work on the assumption that all properties or attributes for which **Finish** does not return a problem report were processed successfully. 
  
If a provider or gateway does not work with problem arrays, it can pass NULL in  _lpProblem_; in this case, no problem array is returned. 
  
The value returned in  _lpProblem_ is valid only if the call returns S_OK. When S_OK is returned, the provider or gateway should check the values returned in the **STnefProblemArray** structure. If an error occurs on the call, the **STnefProblemArray** structure is not filled in and the calling provider or gateway should not use or free the structure. If no error occurs on the call, the calling provider or gateway must release the memory for the **STnefProblemArray** by calling the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|File.cpp  <br/> |SaveToTNEF  <br/> |MFCMAPI uses the **ITnef::Finish** method to finish processing of the new TNEF stream. |
   
## See also



[ITnef::AddProps](itnef-addprops.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[OpenTnefStream](opentnefstream.md)
  
[OpenTnefStreamEx](opentnefstreamex.md)
  
[PidTagAttachNumber Canonical Property](pidtagattachnumber-canonical-property.md)
  
[STnefProblemArray](stnefproblemarray.md)
  
[ITnef : IUnknown](itnefiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

