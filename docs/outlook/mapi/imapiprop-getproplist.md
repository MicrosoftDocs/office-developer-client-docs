---
title: "IMAPIPropGetPropList"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIProp.GetPropList
api_type:
- COM
ms.assetid: 0069c223-32bb-4286-b763-39fd45dc263b
description: "Last modified: March 09, 2015"
---

# IMAPIProp::GetPropList

  
  
**Applies to**: Outlook 
  
Returns property tags for all properties. 
  
```
HRESULT GetPropList(
  ULONG ulFlags,
  LPSPropTagArray FAR * lppPropTagArray
);
```

## Parameters

 _ulFlags_
  
> [in] A bitmask of flags that controls the format for the strings in the returned property tags. The following flag can be set:
    
MAPI_UNICODE 
  
> The returned strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 _lppPropTagArray_
  
> [out] A pointer to a pointer to the property tag array that contains tags for all of the object's properties.
    
## Return value

S_OK 
  
> All of the property tags were returned successfully.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
## Remarks

The **IMAPIProp::GetPropList** method retrieves the property tag for each property currently supported by an object. If the object does not currently support any properties, **GetPropList** returns a property tag array with the **cValues** member set to 0. 
  
The scope of properties returned by **GetPropList** varies from provider to provider. Some service providers exclude those properties for which the caller does not have access. All providers return properties of type **PT_OBJECT**.
  
If the object does not support Unicode, **GetPropList** returns MAPI_E_BAD_CHARWIDTH, even if there are no string properties defined for the object. 
  
## Notes to Implementers

Remote transport providers implement **GetPropList** exactly as specified here. There are no special concerns. Your implementation should, of course, return the same list of properties as supported by the [IMAPIProp::GetProps](imapiprop-getprops.md) method. 
  
## Notes to Callers

Call the [MAPIFreeBuffer](mapifreebuffer.md) function to free the property tag array pointed to by  _lppPropTagArray_. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFunctions.cpp  <br/> |GetPropsNULL  <br/> |MFCMAPI uses the **IMAPIProp::GetPropList** method to get a property list to pass to **GetProps**.  <br/> |
   
## See also

#### Reference

[IMAPIProp::GetProps](imapiprop-getprops.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMAPIProp : IUnknown](imapipropiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

