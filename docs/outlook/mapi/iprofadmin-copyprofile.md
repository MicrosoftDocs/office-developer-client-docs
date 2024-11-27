---
title: "IProfAdminCopyProfile"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IProfAdmin.CopyProfile
api_type:
- COM
ms.assetid: f4846dc3-0236-44ed-a1b1-8c13d48fb58a
---

# IProfAdmin::CopyProfile

**Applies to**: Outlook 2013 | Outlook 2016
  
Copies a profile.
  
```cpp
HRESULTCopyProfile(
  LPSTR lpszOldProfileName,
  LPSTR lpszOldPassword,
  LPSTR lpszNewProfileName,
  ULONG_PTR ulUIParam,
  ULONG ulFlags
);
```

## Parameters

 _lpszOldProfileName_
  
> [in] A pointer to the name of the profile to copy.

 _lpszOldPassword_
  
> [in] A pointer to the password of the profile to copy.

 _lpszNewProfileName_
  
> [in] A pointer to the new name of the copied profile.

 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows that this method displays.

 _ulFlags_
  
> [in] A bitmask of flags that controls how the profile is copied. The following flags can be set:

MAPI_DIALOG
  
> Displays a dialog box that prompts the user for the correct password of the profile to copy. If this flag is not set, no dialog box is displayed.

MAPI_APP_PROFILE

> Allows copying an "app" profile.  This flag must be set if the existing profile is an "app" profile.

## Return value

S_OK
  
> The profile was successfully copied.

MAPI_E_ACCESS_DENIED
  
> The new profile name is the same as that of an existing profile.

MAPI_E_LOGON_FAILED
  
> The password for the profile to copy is incorrect, and a dialog box could not be displayed to the user to request the correct password because MAPI_DIALOG was not set in the _ulFlags_ parameter.

MAPI_E_NO_ACCESS

> The existing profile is an "app" profile, and the MAPI_APP_PROFILE flag was not set.

MAPI_E_NOT_FOUND
  
> The specified profile does not exist.

MAPI_E_USER_CANCEL
  
> The user canceled the operation, typically by clicking the **Cancel** button in a dialog box.

## Remarks

The **IProfAdmin::CopyProfile** method makes a copy of the profile pointed to by _lpszOldProfileName_, giving it the name pointed to by _lpszNewProfileName_. Copying a profile leaves the copy with the same password as the original.
  
The name of the original profile, its password, and the copy can be up to 64 characters in length and can include the following characters:
  
- All alphanumeric characters, including accent characters and the underscore character.
- Embedded spaces, but not leading or trailing spaces.

Profile passwords are not supported on all operating systems. On operating systems that do not support profile passwords, _lpszOldPassword_ can be NULL or a pointer to a zero-length string.
  
If  _lpszOldPassword_ is set to NULL, the profile to be copied requires a password, and the MAPI_DIALOG flag is set; a dialog box that prompts the user to provide the password is displayed. If a password is required, but  _lpszOldPassword_ is set to NULL and the MAPI_DIALOG flag is not set, **CopyProfile** returns MAPI_E_LOGON_FAILED.

If the existing profile is an "app" profile, and the MAPI_APP_PROFILE flag is not set, **CopyProfile** returns MAPI_E_NO_ACCESS.  If the existing profile is an "app" profile, and the MAPI_APP_PROFILE is set, the new profile will also be an "app" profile.  If the existing profile is not an "app" profile, the new profile will not be an "app" profile regardless of the MAPI_APP_PROFILE flag.

## Notes to callers

> [!CAUTION]
> The MAPI_APP_PROFILE flag is only supported in versions 2405 and newer.  Using this flag in earlier versions may fail.

## See also

[IProfAdmin : IUnknown](iprofadminiunknown.md)
