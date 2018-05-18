---
title: "IMAPISessionUnadvise"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISession.Unadvise
api_type:
- COM
ms.assetid: 5e608cb0-808d-4418-8521-71dcbce8cdff
description: "Last modified: July 23, 2011"
---

# IMAPISession::Unadvise

  
  
**Applies to**: Outlook 
  
Cancels the sending of notifications previously set up with a call to the [IMAPISession::Advise](imapisession-advise.md) method. 
  
```cpp
HRESULT Unadvise(
  ULONG_PTR ulConnection
);
```

## Parameters

 _ulConnection_
  
> [in] A connection number associated with an active notification registration. The value of  _ulConnection_ must have been returned by a previous call to **IMAPISession::Advise**.
    
## Return value

S_OK 
  
> The registration was successfully canceled.
    
## Remarks

The **IMAPISession::Unadvise** method cancels a registration for notification. **Unadvise** releases its pointer to the caller's advise sink, which it received in the **Advise** call used for registration. 
  
Generally, **Unadvise** calls the advise sink's [IUnknown::Release](http://msdn.microsoft.com/en-us/library/ms682317%28v=VS.85%29.aspx) method during the **Unadvise** call. However, if another thread is in the process of calling the advise sink's [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method, the **Release** call is delayed until the **OnNotify** method returns. 
  
## See also

#### Reference

[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[IMAPISession::Advise](imapisession-advise.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)

