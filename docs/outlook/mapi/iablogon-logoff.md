---
title: "IABLogonLogoff"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IABLogon.Logoff
api_type:
- COM
ms.assetid: a36465e2-7be9-4bd6-8091-685f0a045aa9
description: "Last modified: July 23, 2011"
---

# IABLogon::Logoff

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Initiates the logoff process.
  
```cpp
HRESULT Logoff(
  ULONG ulFlags
);
```

## Parameters

 _ulFlags_
  
> [in] Reserved; must be zero.
    
## Return value

S_OK 
  
> The logoff process was successfully initiated.
    
## Remarks

The logoff process is typically started when a client calls the [IMAPISession::Logoff](imapisession-logoff.md) method to end a session. MAPI then calls each address book provider's **IABLogon::Logoff** method to start the logoff process. 
  
The **IABLogon::Logoff** method does the following: 
  
- Releases all open objects, such as any subobjects or the status object.
    
- Releases the provider's support object.
    
For more information about the logoff process of address book providers, see [Shutting Down a Service Provider](shutting-down-a-service-provider.md).
  
## See also



[IABProvider::Logon](iabprovider-logon.md)
  
[IABLogon : IUnknown](iablogoniunknown.md)

