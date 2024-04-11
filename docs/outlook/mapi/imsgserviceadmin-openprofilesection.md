---
title: "IMsgServiceAdminOpenProfileSection"
description: "IMsgServiceAdmin OpenProfileSection opens a section of the current profile and returns an IProfSect pointer for further access."
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMsgServiceAdmin.OpenProfileSection
api_type:
- COM
ms.assetid: 7f24910a-e14e-44a1-8477-d8968130ba74
---

# IMsgServiceAdmin::OpenProfileSection

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens a section of the current profile and returns an [IProfSect](iprofsectimapiprop.md) pointer for further access. 
  
```cpp
HRESULT OpenProfileSection(
  LPMAPIUID lpUID,
  LPCIID lpInterface,
  ULONG ulFlags,
  LPPROFSECT FAR * lppProfSect
);
```

## Parameters

 _lpUID_
  
> A pointer to the [MAPIUID](mapiuid.md) structure that identifies the profile section. 
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the profile section. Passing NULL results in a pointer to its standard interface being returned in the _lppProfSect_ parameter. The standard interface for a profile section is **IProfSect**.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls access to the profile section. The following flags can be set:
    
MAPI_DEFERRED_ERRORS 
  
> Allows **OpenProfileSection** to return successfully, possibly before the profile section is fully available to the calling client. If the profile section is not available, making a subsequent call to it can raise an error. 
    
MAPI_MODIFY 
  
> Requests read/write permission. By default, profile sections are opened with read-only permission, and clients should not work on the assumption that read/write permission has been granted. 
    
MAPI_FORCE_ACCESS
  
> Allows access to all profile sections, even those owned by individual service providers.
    
 _lppProfSect_
  
> [out] A pointer to a pointer to the profile section.
    
## Return value

S_OK 
  
> The profile section was successfully opened.
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to access a profile section for which the caller has insufficient permissions.
    
MAPI_E_NOT_FOUND 
  
> The requested profile section does not exist.
    
## Remarks

The **IMsgServiceAdmin::OpenProfileSection** method opens a profile section, an object that supports the [IProfSect](iprofsectimapiprop.md) interface. Profile sections are used for reading information from and writing information to the session profile. 
  
 **OpenProfileSection** cannot be used to open profile sections owned by individual service providers unless MAPI_FORCE_ACCESS is used. 
  
## Notes to callers

Multiple clients can open a profile section with read-only permission, but only one client can open a profile section with read/write permission. If another client has a profile section open that you attempt to open by calling **OpenProfileSection** with the MAPI_MODIFY flag set, the call will fail, returning MAPI_E_NO_ACCESS. 
  
A read-only open operation fails if the section is open for writing. 
  
You can create a profile section by calling **OpenProfileSection** with the MAPI_MODIFY flag and a nonexistent [MAPIUID](mapiuid.md) structure in the _lpUID_ parameter. Be sure you specify MAPI_MODIFY. If you set  _lpUID_ to point to a nonexistent **MAPIUID** and **OpenProfileSection** is set to use the default access mode of read-only, the call will fail with MAPI_E_NOT_FOUND. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIProfileFunctions.cpp  <br/> |OpenProfileSection  <br/> |MFCMAPI uses the **IMsgServiceAdmin::OpenProfileSection** method to open a profile section. |
   
## See also



[IMAPIProp : IUnknown](imapipropiunknown.md)
  
[IMAPISession::OpenProfileSection](imapisession-openprofilesection.md)
  
[IProfSect : IMAPIProp](iprofsectimapiprop.md)
  
[MAPIUID](mapiuid.md)
  
[IMsgServiceAdmin : IUnknown](imsgserviceadminiunknown.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

