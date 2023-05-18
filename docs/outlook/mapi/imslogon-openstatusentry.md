---
title: "IMSLogonOpenStatusEntry"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMSLogon.OpenStatusEntry
api_type:
- COM
ms.assetid: 850e256b-6b50-428c-aede-287edaf7b005
---

# IMSLogon::OpenStatusEntry

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens a status object.
  
```cpp
HRESULT OpenStatusEntry(
  LPCIID lpInterface,
  ULONG ulFlags,
  ULONG FAR * lpulObjType,
  LPVOID FAR * lppEntry
);
```

## Parameters

 _lpInterface_
  
> [in] A pointer to the interface identifier (IID) for the status object to open. Passing NULL indicates the standard interface for the object is returned (in this case, the [IMAPIStatus](imapistatusimapiprop.md) interface). The  _lpInterface_ parameter can also be set to an identifier for an appropriate interface for the object. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the status object is opened. The following flag can be set:
    
MAPI_MODIFY 
  
> Requests read/write permission. By default, objects are created with read-only permission, and client applications should not work on the assumption that read/write permission has been granted. 
    
 _lpulObjType_
  
> [out] A pointer to the type of the opened object.
    
 _lppEntry_
  
> [out] A pointer to the pointer to the opened object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Message store providers implement the **IMSLogon::OpenStatusEntry** method to open a status object. This status object is then used to enable clients to call [IMAPIStatus](imapistatusimapiprop.md) methods. For example, clients can use the [IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md) method to reconfigure the message store logon session or the [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method to validate the state of the message store logon session. 
  
## See also



[IMAPIStatus : IMAPIProp](imapistatusimapiprop.md)
  
[IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md)
  
[IMAPIStatus::ValidateState](imapistatus-validatestate.md)
  
[IMSLogon : IUnknown](imslogoniunknown.md)

