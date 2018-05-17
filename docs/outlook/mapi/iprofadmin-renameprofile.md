---
title: "IProfAdminRenameProfile"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProfAdmin.RenameProfile
api_type:
- COM
ms.assetid: 2a575cac-dbfd-4f42-9c10-4b7e355a065e
description: "Last modified: July 23, 2011"
---

# IProfAdmin::RenameProfile

  
  
**Applies to**: Outlook 
  
Assigns a new name to a profile.
  
```
HRESULT RenameProfile(
  LPSTR lpszOldProfileName,
  LPSTR lpszOldPassword,
  LPSTR lpszNewProfileName,
  ULONG_PTR ulUIParam,
  ULONG ulFlags
);
```

## Parameters

 _lpszOldProfileName_
  
> [in] A pointer to the current name of the profile to rename.
    
 _lpszOldPassword_
  
> [in] Always NULL.
    
 _lpszNewProfileName_
  
> [in] A pointer to the new name of the profile to rename.
    
 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows that this method displays. 
    
 _ulFlags_
  
> [in] Always NULL.
    
## Return value

S_OK 
  
> The profile was successfully renamed.
    
MAPI_E_LOGON_FAILED 
  
> The profile password is incorrect.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in a dialog box. 
    
## Remarks

The **IProfAdmin::RenameProfile** method assigns a new name to a profile, if it has one. If the profile to rename is in use by a client when **RenameProfile** is called, **RenameProfile** marks the profile and returns S_OK instead of attempting the rename operation while the profile is in use. When the profile is no longer being used, **RenameProfile** assigns it the new name. 
  
The old and new names of the profile can be up to 64 characters in length and can include the following characters:
  
- All alphanumeric characters, including accent characters and the underscore character.
    
- Embedded spaces, but not leading or trailing spaces.
    
The  _lpszPassword_ should always be NULL or a pointer to a zero-length string. 
  
## See also

#### Reference

[IProfAdmin : IUnknown](iprofadminiunknown.md)

