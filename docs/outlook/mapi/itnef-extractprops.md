---
title: "ITnefExtractProps"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- ITnef.ExtractProps
api_type:
- COM
ms.assetid: 9169a5be-21dd-4938-8db3-522bea165c92
description: "Last modified: July 23, 2011"
---

# ITnef::ExtractProps

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Extracts the properties from a TNEF encapsulation. 
  
```cpp
HRESULT ExtractProps(
  ULONG ulFlags,
  LPSPropTagArray lpPropList,
  LPSTnefProblemArray FAR * lpProblems
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls how properties are decoded. The following flags can be set:
    
TNEF_PROP_EXCLUDE 
  
> Decodes all properties not specified in the _lpPropList_ parameter. 
    
TNEF_PROP_INCLUDE 
  
> Decodes all properties specified in  _lpPropList_.
    
 _lpPropList_
  
> [in] A pointer to the list of properties to include in or exclude from the decoding operation.
    
 _lpProblems_
  
> [out] A pointer to a pointer to a returned [STnefProblemArray](stnefproblemarray.md) structure. The **STnefProblemArray** structure indicates which properties, if any, were not encoded properly. If NULL is passed in the _lpProblems_ parameter, no property problem array is returned. 
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
MAPI_E_CORRUPT_DATA 
  
> Data being decoded into a stream is corrupted.
    
## Remarks

Transport providers, message store providers, and gateways call the **ITnef::ExtractProps** method to extract (that is, decode) properties from the encapsulation of a message or an attachment that was passed to the [OpenTnefStream](opentnefstream.md) function. The calling provider or gateway can specify a list of properties to decode. Providers and gateways can also use **ExtractProps** to provide information about any special handling for attachments. 
  
 **ExtractProps** populates the original message passed into **OpenTnefStream** with the decoded properties. Subsequent **ExtractProps** calls go back to the message and extract the new list of properties. 
  
Unlike the [ITnef::AddProps](itnef-addprops.md) method, which queues requested actions until the **ITnef::Finish** method is called, the **ExtractProps** method decodes the encapsulated properties immediately when it is called. For that reason, the target message for encapsulation decoding should be relatively empty. Existing properties in the target message are overwritten by encapsulated properties. 
  
 **ExtractProps** is supported only for objects that are opened with the TNEF_DECODE flag for the **OpenTnefStream** or [OpenTnefStreamEx](opentnefstreamex.md) function. 
  
The TNEF implementation reports TNEF stream encoding problems without stopping the **ExtractProps** process. The [STnefProblemArray](stnefproblemarray.md) structure returned in  _lpProblems_ indicates which TNEF attributes or MAPI properties, if any, could not be processed. The value returned in the **scode** member of the one of the **STnefProblem** structures contained in **STnefProblemArray** indicates the specific problem. The provider or gateway can work on the assumption that all properties or attributes for which **ExtractProps** does not return a problem report were processed successfully. 
  
> [!NOTE]
> If a property in the MAPI encapsulation block cannot be processed and leaves the stream unreliable during the decoding of a TNEF stream, decoding of the encapsulation block is stopped and a problem is reported. The problem array for this type of problem contains 0L for the **ulPropTag** member,  `attMAPIProps` or  `attAttachment` for the **ulAttribute** member, and MAPI_E_UNABLE_TO_COMPLETE for the **scode** member. Note that the decoding of the stream is not halted, just the decoding of the MAPI encapsulation block. The stream decoding continues with the next attribute block. 
  
If a provider or gateway does not work with problem arrays, it can pass NULL in  _lppProblems_; in this case, no problem array is returned. 
  
The value returned in  _lpProblems_ is valid only if the call returns S_OK. When S_OK is returned, the provider or gateway should check the values returned in the **STnefProblemArray** structure. If an error occurs on the call, the **STnefProblemArray** structure is not filled in and the calling provider or gateway should not use or free the structure. If no error occurs on the call, the calling provider or gateway must release the memory for the **STnefProblemArray** structure by calling the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
## See also



[ITnef::AddProps](itnef-addprops.md)
  
[ITnef::Finish](itnef-finish.md)
  
[ITnef::SetProps](itnef-setprops.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[OpenTnefStream](opentnefstream.md)
  
[OpenTnefStreamEx](opentnefstreamex.md)
  
[STnefProblemArray](stnefproblemarray.md)
  
[ITnef : IUnknown](itnefiunknown.md)

