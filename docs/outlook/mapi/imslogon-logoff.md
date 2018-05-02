---
title: "IMSLogonLogoff"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMSLogon.Logoff
api_type:
- COM
ms.assetid: 1b0d1b52-6651-4de3-9381-86772d9d52a1
description: "Last modified: July 23, 2011"
---

# IMSLogon::Logoff

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Logs off a message store provider. 
  
```
HRESULT Logoff(
  ULONG FAR * lpulFlags
);
```

## Parameters

 _lpulFlags_
  
> [in] Reserved; must be a pointer to zero.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Message store providers implement the **IMSLogon::Logoff** method to forcibly shut down a message store provider. **IMSLogon::Logoff** is called in the following situations: 
  
- While MAPI is logging off a client after a call to the [IMAPISession::Logoff](imapisession-logoff.md) method. 
    
- While MAPI is logging off a message store provider. In this case, **IMSLogon::Logoff** is called as part of MAPI processing the [IUnknown::Release](http://msdn.microsoft.com/en-us/library/ms682317%28v=VS.85%29.aspx) method of the support object that the message store provider creates while it is processing an [IMsgStore::StoreLogoff](imsgstore-storelogoff.md) or **IUnknown::Release** method call on a message store object. 
    
## See also

#### Reference

[IMAPISession::Logoff](imapisession-logoff.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)
  
[IMsgStore::StoreLogoff](imsgstore-storelogoff.md)
  
[IMSProvider::Logon](imsprovider-logon.md)
  
[MAPIFreeBuffer](mapifreebuffer.md)
  
[IMSLogon : IUnknown](imslogoniunknown.md)

