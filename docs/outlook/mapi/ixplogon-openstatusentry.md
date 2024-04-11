---
title: "IXPLogonOpenStatusEntry"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IXPLogon.OpenStatusEntry
api_type:
- COM
ms.assetid: 261d5f7c-bb61-4e1d-aa41-cca224c63f8e
---

# IXPLogon::OpenStatusEntry

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Opens the transport provider's status object.
  
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
  
> [in] A pointer to an interface identifier (IID) for the transport logon object. Passing NULL returns the [IMAPIStatus](imapistatusimapiprop.md) interface. The  _lpInterface_ parameter can also be set to an identifier for an interface for the object. 
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the status object is opened. The following flag can be set:
    
MAPI_MODIFY 
  
> Requests read/write permission. The default interface is read-only. 
    
 _lpulObjType_
  
> [out] A pointer to the type of the opened object.
    
 _lppEntry_
  
> [out] A pointer to the pointer to the opened status object.
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
## Remarks

The MAPI spooler calls the **IXPLogon::OpenStatusEntry** method when a client application calls an **OpenEntry** method for the entry identifier in the transport provider's status table row. **OpenStatusEntry** opens an object with the **IMAPIStatus** interface associated with this particular transport provider logon. This object is then used to enable client applications to call **IMAPIStatus** methods (for example, to reconfigure the logon session by using the [IMAPIStatus::SettingsDialog](imapistatus-settingsdialog.md) method, or to validate the state of the logon session by using the [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method). 
  
## See also



[IMAPIStatus : IMAPIProp](imapistatusimapiprop.md)
  
[IXPLogon : IUnknown](ixplogoniunknown.md)

