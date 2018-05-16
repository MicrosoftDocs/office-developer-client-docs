---
title: "IXPLogonIdle"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IXPLogon.Idle
api_type:
- COM
ms.assetid: 8f600db6-f6a6-44f9-aef7-c1309f61eb12
description: "Last modified: July 23, 2011"
---

# IXPLogon::Idle

  
  
**Applies to**: Outlook 
  
Indicates that the system is idle, enabling the transport provider to perform low-priority operations.
  
```
HRESULT Idle(
  ULONG ulFlags
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
## Remarks

The MAPI spooler periodically calls the **IXPLogon::Idle** method, if requested, during times when the system is idle by passing the XP_LOGON_SP flag in the call to the [IXPProvider::TransportLogon](ixpprovider-transportlogon.md) method that opened the current session. At times when the system is idle, the transport provider can perform background operations that are not appropriate during other calls, or that need to occur on a regular basis. 
  
## See also

#### Reference

[IXPProvider::TransportLogon](ixpprovider-transportlogon.md)
  
[IXPLogon : IUnknown](ixplogoniunknown.md)

