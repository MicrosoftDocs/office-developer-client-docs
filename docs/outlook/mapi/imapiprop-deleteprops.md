---
title: "IMAPIPropDeleteProps"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIProp.DeleteProps
api_type:
- COM
ms.assetid: 5cc642de-21f0-4826-bf21-aac4bcfc1328
description: "Last modified: March 09, 2015"
---

# IMAPIProp::DeleteProps

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Deletes one or more properties from an object. 
  
```cpp
HRESULT DeleteProps(
  LPSPropTagArray lpPropTagArray,
  LPSPropProblemArray FAR * lppProblems
);
```

## Parameters

 _lpPropTagArray_
  
> [in] A pointer to an array of property tags that indicate the properties to delete. The **cValues** member of the [SPropTagArray](sproptagarray.md) structure pointed to by  _lpPropTagArray_ must not be zero, and the  _lpPropTagArray_ parameter itself must not be NULL. 
    
 _lppProblems_
  
> [in, out] On input, a pointer to a pointer to an [SPropProblemArray](spropproblemarray.md) structure; otherwise, NULL, which indicates that there is no need for error information. If  _lppProblems_ is a valid pointer on input, **DeleteProps** returns detailed information about errors in deleting one or more properties. 
    
## Return value

S_OK 
  
> Properties were successfully deleted.
    
MAPI_E_NO_ACCESS 
  
> The caller has insufficient permissions to delete properties.
    
## Remarks

The **IMAPIProp::DeleteProps** method removes one or more properties from the current object. 
  
## Notes to implementers

You do not have to allow properties to be deleted from all objects. If the object is not modifiable, return MAPI_E_NO_ACCESS from the **DeleteProps** method. 
  
## Notes to callers

You do not have to set the property type for each property tag in the property tag array pointed to by the  _lpPropTagArray_ parameter. Property types are ignored; only the property identifiers are used. 
  
Be aware that some objects do not allow modification and that these objects return MAPI_E_NO_ACCESS from the **DeleteProps** method. Other objects allow some properties to be deleted, but not others. When there is a problem deleting only some of the properties, **DeleteProps** returns S_OK. If you have passed a valid pointer in the _lppProblems_ parameter, **DeleteProps** will set the pointer to an **SPropProblemArray** structure that contains detailed information about the problems with each property. For example, if you are deleting all of the properties of a message and there is a problem with one or more of its attachments, the **SPropProblemArray** structure will contain an entry for the **PR_MESSAGE_ATTACHMENTS** ([PidTagMessageAttachments](pidtagmessageattachments-canonical-property.md)) property. 
  
The structure pointed to by  _lppProblems_ is only valid if **DeleteProps** returns S_OK. If **DeleteProps** returns an error, do not attempt to use the **SPropProblemArray** structure. Instead, call the object's [IMAPIProp::GetLastError](imapiprop-getlasterror.md) method to obtain more information about the error. 
  
Free the returned **SPropProblemArray** structure by calling the [MAPIFreeBuffer](mapifreebuffer.md) function. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIFunctions.cpp  <br/> |DeleteProperty  <br/> |MFCMAPI uses the **IMAPIProp::DeleteProps** method to delete a property from an object. |
   
## See also



[IMAPIProp::GetLastError](imapiprop-getlasterror.md)
  
[IMAPIProp::GetProps](imapiprop-getprops.md)
  
[IMAPIProp::SaveChanges](imapiprop-savechanges.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[SPropProblemArray](spropproblemarray.md)
  
[SPropTagArray](sproptagarray.md)
  
[IMAPIProp : IUnknown](imapipropiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

