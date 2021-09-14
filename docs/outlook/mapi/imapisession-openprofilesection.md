---
title: "IMAPISessionOpenProfileSection"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISession.OpenProfileSection
api_type:
- COM
ms.assetid: e2757028-27e7-4fc0-9674-e8e30737ef1d
description: "Last modified: July 23, 2011"
---

# IMAPISession::OpenProfileSection

  
  
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
  
> [in] A pointer to the [MAPIUID](mapiuid.md) structure that identifies the profile section. 
    
 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the profile section. Passing NULL causes the  _lppProfSect_ parameter to return a pointer to the profile section's standard interface, **IProfSect**.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls access to the profile section. The following flags can be set:
    
MAPI_DEFERRED_ERRORS 
  
> Allows **OpenProfileSection** to return successfully, possibly before the profile section is fully available to the calling client. If the profile section is not available, making a subsequent call to it can cause an error. 
    
MAPI_FORCE_ACCESS
  
> Allows access to a profile section that does not belong to the provider.
    
MAPI_MODIFY 
  
> Requests read/write permission. By default, profile sections are opened with read-only permission, and clients should not work on the assumption that read/write permission has been granted. 
    
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

The **IMAPISession::OpenProfileSection** method opens a profile section or object that supports the **IProfSect** interface. Profile sections are used for reading information from and writing information to the session profile. 
  
You cannot use **OpenProfileSection** to open profile sections that individual service providers own unless you specify MAPI_FORCE_ACCESS in the  _ulFlags_ parameter. 
  
## Notes to callers

Multiple clients can open a profile section with read-only permission, but only one client can open a profile section with read/write permission. If another client has a profile section open that you attempt to open by calling **OpenProfileSection** with the MAPI_MODIFY flag set, the call will fail, returning MAPI_E_NO_ACCESS. 
  
A read-only open operation fails if the section is open for writing. 
  
You can create a profile section by calling **OpenProfileSection** with the MAPI_MODIFY flag and a nonexistent **MAPIUID** structure in the  _lpUID_ parameter. Be sure that you specify MAPI_MODIFY. If you set  _lpUID_ to point to a nonexistent **MAPIUID** and **OpenProfileSection** is set to use the default access mode of read-only, the call will fail with MAPI_E_NOT_FOUND. 
  
## See also



[IMAPIProp : IUnknown](imapipropiunknown.md)
  
[IProfSect : IMAPIProp](iprofsectimapiprop.md)
  
[MAPIUID](mapiuid.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)

