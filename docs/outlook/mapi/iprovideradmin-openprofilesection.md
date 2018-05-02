---
title: "IProviderAdminOpenProfileSection"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IProviderAdmin.OpenProfileSection
api_type:
- COM
ms.assetid: b73cf770-8817-4a23-bd14-7b76fedef214
description: "Last modified: March 09, 2015"
---

# IProviderAdmin::OpenProfileSection

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Opens a profile section from the current profile and returns an [IProfSect](iprofsectimapiprop.md) pointer for further access. 
  
```
HRESULT OpenProfileSection(
  LPMAPIUID lpUID,
  LPCIID lpInterface,
  ULONG ulFlags,
  LPPROFSECT FAR * lppProfSect
);
```

## Parameters

 _lpUID_
  
> [in] A pointer to the [MAPIUID](mapiuid.md) structure that contains the unique identifier for the profile section to be opened. Clients must not pass NULL for the  _lpUID_ parameter. Service providers can pass NULL to retrieve the **MAPIUID** when they call from their message service entry point functions. 
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the profile section. Passing NULL results in the profile section's standard interface ( **IProfSect**) being returned. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the profile section is opened. The following flags can be set:
    
MAPI_DEFERRED_ERRORS 
  
> Enables **OpenProfileSection** to return successfully, possibly before the profile section is fully available to the caller. If the profile section is not available, making a subsequent call to it can raise an error. 
    
MAPI_MODIFY 
  
> Requests read/write permission. By default, objects are opened with read-only permission, and callers should not work on the assumption that read/write permission has been granted. Clients are not allowed read/write permission to provider sections of the profile.
    
MAPI_FORCE_ACCESS
  
> Allows access to all profile sections, even those owned by individual service providers.
    
 _lppProfSect_
  
> [out] A pointer to a pointer to the profile section.
    
## Return value

S_OK 
  
> The profile section was successfully opened.
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to modify a read-only profile section or to access an object for which the user has insufficient permissions.
    
MAPI_E_NOT_FOUND 
  
> The requested profile section does not exist.
    
## Remarks

The **IProviderAdmin::OpenProfileSection** method opens a profile section, enabling the caller to read information from and possibly write information to the active profile. 
  
Clients cannot open profile sections that belong to providers by using the **OpenProfileSection** method. 
  
Multiple clients or service providers can simultaneously open a profile section with read-only permission. However, when a profile section is open with read/write permission, no other calls can be made to open the section, regardless of the type of access. If a profile section is open with read-only permission, a subsequent call to request read/write permission will fail with MAPI_E_NO_ACCESS. Likewise, if a section is open with read/write permission, a subsequent call to request read-only permission will also fail. 
  
## Notes to Callers

If you request that **OpenProfileSection** open a nonexistent profile section by passing MAPI_MODIFY in  _ulFlags_ and an unknown **MAPIUID** in  _lpUID_, the profile section will be created. 
  
If you request that **OpenProfileSection** open a nonexistent section with read-only permission, it returns MAPI_E_NOT_FOUND. 
  
## MFCMAPI Reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIProfileFunctions.cpp  <br/> |OpenProfileSection  <br/> |MFCMAPI uses the **IProviderAdmin::OpenProfileSection** method to open a profile section from the current profile.  <br/> |
   
## See also

#### Reference

[IMAPIProp : IUnknown](imapipropiunknown.md)
  
[IProfSect : IMAPIProp](iprofsectimapiprop.md)
  
[MAPIUID](mapiuid.md)
  
[IProviderAdmin : IUnknown](iprovideradminiunknown.md)
#### Concepts

[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

