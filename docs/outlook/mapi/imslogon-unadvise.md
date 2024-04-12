---
title: "IMSLogonUnadvise"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMSLogon.Unadvise
api_type:
- COM
ms.assetid: 440d61c4-b69a-4010-a22b-0c9c5c376fbc
---

# IMSLogon::Unadvise

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Removes an object's registration for notification of message store changes previously established by using a call to the [IMSLogon::Advise](imslogon-advise.md) method. 
  
```cpp
HRESULT Unadvise(
  ULONG ulConnection
);
```

## Parameters

 _ulConnection_
  
> [in] The number of the registration connection returned by a call to **IMSLogon::Advise**.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

Message store providers implement the **IMSLogon::Unadvise** method to release the pointer to the advise sink object passed in the _lpAdviseSink_ parameter in the previous call to **IMSLogon::Advise**, thereby canceling a notification registration. As part of discarding the pointer to the advise sink object, the object's [IUnknown::Release](https://msdn.microsoft.com/library/ms682317%28v=VS.85%29.aspx) method is called. Generally, **Release** is called during the **Unadvise** call. However, if another thread is in the process of calling the [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method for the advise sink object, the **Release** call is delayed until the **OnNotify** method returns. 
  
## See also



[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[IMSLogon::Advise](imslogon-advise.md)
  
[IMSLogon : IUnknown](imslogoniunknown.md)

