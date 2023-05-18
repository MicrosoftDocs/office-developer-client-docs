---
title: "IABLogonOpenStatusEntry"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IABLogon.OpenStatusEntry
api_type:
- COM
ms.assetid: 66f1e246-a67a-4f8a-ae3a-6a8ec8c2b367
---

# IABLogon::OpenStatusEntry

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens the provider's status object.
  
```cpp
HRESULT OpenStatusEntry(
  LPCIID lpInterface,
  ULONG ulFlags,
  ULONG FAR * lpulObjType,
  LPMAPISTATUS FAR * lppEntry
);
```

## Parameters

 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) that represents the interface that must be used to access the status object. Passing NULL returns the object's standard interface, [IMAPIStatus : IMAPIProp](imapistatusimapiprop.md).
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the status object is opened. The following flag can be set:
    
MAPI_MODIFY 
  
> Requests read/write permission. By default, objects are opened with read-only access, and callers should not assume that read/write permission has been granted.
    
 _lpulObjType_
  
> [out] A pointer to the type of the opened object.
    
 _lppEntry_
  
> [out] A pointer to a pointer to the opened object.
    
## Return value

S_OK 
  
> The call succeeded and the status object has been opened.
    
## Remarks

Address book providers implement the **OpenStatusEntry** method to grant access to their status object. All address book providers are required to implement a status object that supports, at a minimum, the [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method. For more information, see [Status Object Implementation](status-object-implementation.md).
  
## See also



[IMAPIStatus : IMAPIProp](imapistatusimapiprop.md)
  
[IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md)
  
[IMAPIStatus::ValidateState](imapistatus-validatestate.md)
  
[IABLogon : IUnknown](iablogoniunknown.md)

