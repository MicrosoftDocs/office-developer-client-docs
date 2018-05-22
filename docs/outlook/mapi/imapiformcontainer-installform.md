---
title: "IMAPIFormContainerInstallForm"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormContainer.InstallForm
api_type:
- COM
ms.assetid: b39ca52c-4dbe-41c0-9e1b-3998a9dc9742
description: "Last modified: March 09, 2015"
---

# IMAPIFormContainer::InstallForm

  
  
**Applies to**: Outlook 
  
Installs a form into a form library.
  
```cpp
HRESULT InstallForm(
  ULONG_PTR ulUIParam,
  ULONG ulFlags,
  LPCSTR szCfgPathName
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows that this method displays. The  _ulUIParam_ parameter is ignored unless the client application sets the MAPI_DIALOG flag in the  _ulFlags_ parameter. The  _ulUIParam_ parameter can be NULL if MAPI_DIALOG is not also passed. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the installation of the form. The following flags can be set:
    
MAPI_DIALOG 
  
> Displays a dialog box to provide progress information or prompt the user for more information. If this flag is not set, no dialog box is displayed.
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format.
    
MAPIFORM_INSTALL_OVERWRITEONCONFLICT 
  
> If another form already exists that handles the message class handled by this form, replace the existing form with this one. This flag is ignored if the MAPI_DIALOG flag is also present. 
    
 _szCfgPathName_
  
> [in] The path to the form's configuration file.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_EXTENDED_ERROR 
  
> An implementation error occurred. To get the [MAPIERROR](mapierror.md) structure that is associated with the error, call the [IMAPIFormContainer::GetLastError](imapiformcontainer-getlasterror.md) method. 
    
MAPI_E_USER_CANCEL 
  
> The user canceled the installation of the form, typically by clicking the **Cancel** button in a dialog box. 
    
## Notes to implementers

Form library providers should fill in a **MAPIERROR** structure and return MAPI_E_EXTENDED_ERROR if any of the following conditions occur: 
  
- The configuration file is not found.
    
- The configuration file is not readable.
    
- The configuration file is invalid.
    
## Notes to callers

Client applications call the **IMAPIFormContainer::InstallForm** method to install a form into a specific form container. The  _szCfgPathName_ parameter must contain the path of a form configuration file (that is, a file with the .cfg extension that describes the form and its implementation). The flags in the  _ulFlags_ parameter specify the following: 
  
- If the MAPI_DIALOG flag is set, a user interface is displayed, enabling the user who is installing the form to specify installation details.
    
- If the MAPIFORM_INSTALL_OVERWRITEONCONFLICT flag is set, any previous form for the same message class is replaced with the form being installed. Otherwise, the form installation is merged with the current form description, if one exists.
    
- If MAPI_DIALOG is set, MAPIFORM_INSTALL_OVERWRITEONCONFLICT is ignored.
    
- The absence of MAPIFORM_INSTALL_OVERWRITEONCONFLICT in the flag set means that a merge will be done. Any new platforms in the .cfg file that are not currently present in the form description will be installed and no other changes will occur.
    
- If the MAPI_UNICODE flag is set, the path of the form configuration file is a Unicode string. 
    
Clients should call [IMAPIFormContainer::GetLastError](imapiformcontainer-getlasterror.md) if **InstallForm** returns MAPI_E_EXTENDED_ERROR, and they should check the returned [MAPIERROR](mapierror.md) structure to determine the condition that raised the error. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|FormContainerDlg.cpp  <br/> |CFormContainerDlg::OnInstallForm  <br/> |MFCMAPI uses the **IMAPIFormContainer::InstallForm** method to install a form in a form container.  <br/> |
   
## See also



[MAPIERROR](mapierror.md)
  
[IMAPIFormContainer : IUnknown](imapiformcontaineriunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

