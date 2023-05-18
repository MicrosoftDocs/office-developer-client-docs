---
title: "IProfAdminSetDefaultProfile"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IProfAdmin.SetDefaultProfile
api_type:
- COM
ms.assetid: 58f50535-b0ed-4097-bda8-fd3ccc2d4b49
---

# IProfAdmin::SetDefaultProfile

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sets or clears a client's default profile.
  
```cpp
HRESULT SetDefaultProfile(
  LPSTR lpszProfileName,
  ULONG ulFlags
);
```

## Parameters

 _lpszProfileName_
  
> [in] A pointer to the name of the profile that will become the default, or NULL. Setting  _lpszProfileName_ to NULL indicates that **SetDefaultProfile** should remove the existing default profile, leaving the client without a default. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls the type of the string pointed to by  _lpszProfileName_. The following flag can be set:
    
MAPI_UNICODE 
  
> The profile name is in Unicode format. If the MAPI_UNICODE flag is not set, the profile name is in ANSI format.
    
## Return value

S_OK 
  
> A default profile was successfully established or removed.
    
MAPI_E_NOT_FOUND 
  
> The specified profile does not exist.
    
## Remarks

The **IProfAdmin::SetDefaultProfile** method either establishes a particular profile as the client's default profile or clears the current default profile. The default profile is the profile that is automatically used whenever the client begins a MAPI session. **SetDefaultProfile** also sets the new default profile's **PR_DEFAULT_PROFILE** ([PidTagDefaultProfile](pidtagdefaultprofile-canonical-property.md)) property to TRUE.
  
## Notes to callers

To start a session with the default profile, pass the MAPI_USE_DEFAULT flag to the [MAPILogonEx](mapilogonex.md) function. 
  
## See also



[IProfAdmin::GetProfileTable](iprofadmin-getprofiletable.md)
  
[MAPILogonEx](mapilogonex.md)
  
[PidTagDefaultProfile Canonical Property](pidtagdefaultprofile-canonical-property.md)
  
[IProfAdmin : IUnknown](iprofadminiunknown.md)

