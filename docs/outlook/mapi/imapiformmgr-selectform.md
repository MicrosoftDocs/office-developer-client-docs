---
title: "IMAPIFormMgrSelectForm"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormMgr.SelectForm
api_type:
- COM
ms.assetid: c1cfe71b-01f3-429a-8b4c-73191a2ffea0
description: "Last modified: March 09, 2015"
---

# IMAPIFormMgr::SelectForm

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Presents a dialog box that enables the user to select a form, and returns a form information object that describes that form.
  
```
HRESULT SelectForm(
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  LPCSTR pszTitle,
  LPMAPIFOLDER pfld,
  LPMAPIFORMINFO FAR * ppfrminfoReturned
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
  
> [in] A pointer to a string that contains the caption of the dialog box. If the  _pszTitle_ parameter is NULL, the form library provider supplies a default caption. 
    
 _pfld_
  
> [in] A pointer to the folder from which to select the form. If the  _pfld_ parameter is NULL, the form can be selected from the local, personal, or organization form container. 
    
 _ppfrminfoReturned_
  
> [out] A pointer to a pointer to the returned form information object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_BAD_CHARWIDTH 
  
> Either the MAPI_UNICODE flag was set and the implementation does not support Unicode, or MAPI_UNICODE was not set and the implementation supports only Unicode.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in the dialog box. 
    
## Remarks

Form viewers call the **IMAPIFormMgr::SelectForm** method to first present a dialog box that enables the user to select a form and then to retrieve a form information object that describes the selected form. The dialog box constrains the user to select a single form. 
  
## Notes to Callers

The **SelectForm** dialog box displays only forms that are not hidden (that is, forms that have their hidden properties clear). If a form viewer passes the MAPI_UNICODE flag in the  _ulFlags_ parameter, all strings are Unicode. Form library providers that do not support Unicode strings should return MAPI_E_BAD_CHARWIDTH if MAPI_UNICODE is passed. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|FolderDlg.cpp  <br/> |CFolderDlg::OnSelectForm  <br/> |MFCMAPI uses the **IMAPIFormMgr::SelectForm** method to select a form and send information about the form to one or more logs.  <br/> |
   
## See also

#### Reference

[IMAPIFormMgr : IUnknown](imapiformmgriunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

