---
title: "IMAPIFormMgrSelectMultipleForms"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormMgr.SelectMultipleForms
api_type:
- COM
ms.assetid: 172f8f53-b837-4286-9236-3f72806d7f1f
description: "Last modified: July 23, 2011"
---

# IMAPIFormMgr::SelectMultipleForms

  
  
**Applies to**: Outlook 
  
Presents a dialog box that enables the user to select multiple forms, and returns an array of form information objects that describe those forms.
  
```cpp
HRESULT SelectMultipleForms(
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  LPCSTR pszTitle,
  LPMAPIFOLDER pfld,
  LPMAPIFORMINFOARRAY pfrminfoarray,
  LPMAPIFORMINFOARRAY FAR * ppfrminfoarray
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of the displayed dialog box. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the passed-in strings. The following flag can be set:
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
 _pszTitle_
  
> [in] A pointer to a string that contains the caption of the dialog box. If the  _pszTitle_ parameter is NULL, the form library provider that provides the forms supplies a default caption. 
    
 _pfld_
  
> [in] A pointer to the folder from which to select the forms. If the  _pfld_ parameter is NULL, the forms are selected from the local, personal, or organization form container. 
    
 _pfrminfoarray_
  
> [in] A pointer to an array of form information objects that are preselected for the user.
    
 _ppfrminfoarray_
  
> [out] A pointer to a pointer to the returned array of form information objects.
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in the dialog box. 
    
## Remarks

Form viewers call the **IMAPIFormMgr::SelectMultipleForms** method to first present a dialog box that enables the user to select multiple forms and then to retrieve an array of form information objects that describe the selected forms. The **SelectMultipleForms** dialog box displays all forms, whether or not they are hidden (that is, whether or not their hidden properties are clear). 
  
## Notes to implementers

If a form viewer passes the MAPI_UNICODE flag in the  _ulFlags_ parameter, all strings are Unicode. Form library providers that do not support Unicode strings should return MAPI_E_BAD_CHARWIDTH if MAPI_UNICODE is passed. 
  
## See also



[IMAPIFormMgr : IUnknown](imapiformmgriunknown.md)

