---
title: "IMAPIFormInfoSaveForm"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIFormInfo.SaveForm
api_type:
- COM
ms.assetid: 18a10f14-0795-4d4d-b590-f4cef4f2902a
description: "Last modified: July 23, 2011"
---

# IMAPIFormInfo::SaveForm

  
  
**Applies to**: Outlook 
  
Saves a description of a particular form in a configuration file.
  
```cpp
HRESULT SaveForm(
  LPCSTR szFileName
);
```

## Parameters

 _szFileName_
  
> [in] A string that names the form's description message file where its description is saved. This file name must have the .fdm extension.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_EXTENDED_ERROR 
  
> The configuration file could not be written. To get the [MAPIERROR](mapierror.md) structure that is associated with the error, call the [IMAPIProp::GetLastError](imapiprop-getlasterror.md) method. 
    
MAPI_E_NO_SUPPORT 
  
> **SaveForm** was probably called to save a form in the local form container. **SaveForm** is not supported on the local form container. 
    
## Remarks

Client applications call the **IMAPIFormInfo::SaveForm** method to save a description of the current form in the file that has the given file name. **SaveForm** creates a configuration file. 
  
## Notes to callers

You can reinstall forms by selecting them from a list of form descriptor messages in a dialog box that form library providers display. The recommended extension for form descriptor messages is .fdm.
  
Call the [IMAPIProp::GetLastError](imapiprop-getlasterror.md) method if **SaveForm** returns MAPI_E_EXTENDED_ERROR, and check the returned **MAPIERROR** structure to determine the condition that caused the error. 
  
## See also



[IMAPIProp::GetLastError](imapiprop-getlasterror.md)
  
[MAPIERROR](mapierror.md)
  
[IMAPIFormInfo : IMAPIProp](imapiforminfoimapiprop.md)

