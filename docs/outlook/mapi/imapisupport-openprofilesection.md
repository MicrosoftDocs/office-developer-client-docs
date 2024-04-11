---
title: "IMAPISupportOpenProfileSection"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPISupport.OpenProfileSection
api_type:
- COM
ms.assetid: cd1fa994-9531-46c4-94e5-505e7f90b884
---

# IMAPISupport::OpenProfileSection

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens a section of the current profile and returns an [IProfSect](iprofsectimapiprop.md) pointer for further access. 
  
```cpp
HRESULT OpenProfileSection(
LPMAPIUID lpUid,
ULONG ulFlags,
LPPROFSECT FAR * lppProfileObj
);
```

## Parameters

 _lpUid_
  
> [in] A pointer to the [MAPIUID](mapiuid.md) structure that identifies the profile section to be opened. Passing NULL for the  _lpUid_ parameter opens the caller's profile section. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the profile section is opened. The following flags can be set:
    
MAPI_DEFERRED_ERRORS 
  
> Allows **OpenProfileSection** to return successfully, possibly before the profile section is fully accessible to the caller. If the profile section is not accessible, making a subsequent object call can result in an error. 
    
MAPI_MODIFY 
  
> Requests read/write permission. By default, objects are opened as read-only, and callers should not work on the assumption that read/write permission has been granted. 
    
 _lppProfileObj_
  
> [out] A pointer to a pointer to the opened profile section.
    
## Return value

S_OK 
  
> The profile section was successfully opened.
    
MAPI_E_NO_ACCESS 
  
> An attempt was made to modify a read-only profile section or to access an object for which the caller has insufficient permissions.
    
MAPI_E_NOT_FOUND 
  
> There is not a profile section associated with the entry identifier passed in  _lpEntryID_.
    
MAPI_E_UNKNOWN_FLAGS 
  
> Reserved or unsupported flags were used and, therefore, the operation did not complete.
    
## Remarks

The **IMAPISupport::OpenProfileSection** method is implemented for all support objects. Service providers and message services call **OpenProfileSection** to open a profile section and retrieve a pointer to its **IProfSect** interface implementation. 
  
## Notes to callers

 **OpenProfileSection** opens profile sections as read-only, unless you set the MAPI_MODIFY flag in the _ulFlags_ parameter and your permission is sufficient. Setting this flag does not guarantee read/write permission; the permissions that you are granted depend on your access level and the object. 
  
If **OpenProfileSection** attempts to open a nonexistent profile section as read-only, it returns MAPI_E_NOT_FOUND. If **OpenProfileSection** attempts to open a nonexistent profile section as read/write, it creates the profile section and returns the **IProfSect** pointer. 
  
## See also



[IMAPIProp : IUnknown](imapipropiunknown.md)
  
[IProfSect : IMAPIProp](iprofsectimapiprop.md)
  
[MAPIUID](mapiuid.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

