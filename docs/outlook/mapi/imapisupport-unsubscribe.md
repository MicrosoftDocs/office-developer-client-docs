---
title: "IMAPISupportUnsubscribe"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPISupport.Unsubscribe
api_type:
- COM
ms.assetid: 3f2870f7-1c08-4d0f-b9d8-7644f5e55b78
description: "Last modified: July 23, 2011"
---

# IMAPISupport::Unsubscribe

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Cancels the responsibility for sending notifications that was previously established with a call to the [IMAPISupport::Subscribe](imapisupport-subscribe.md) method. 
  
```cpp
HRESULT Unsubscribe(
ULONG ulConnection
);
```

## Parameters

 _ulConnection_
  
> [in] The nonzero connection number that represents the notification registration previously established through **IMAPISupport::Subscribe**.
    
## Return value

S_OK 
  
> The notification registration was canceled.
    
MAPI_E_NOT_FOUND 
  
> The connection number passed in the  _ulConnection_ parameter does not exist. 
    
## Remarks

The **IMAPISupport::Unsubscribe** method is implemented for all service provider support objects. Service providers call **Unsubscribe** to cancel a notification registration previously set up by **Subscribe**. **Unsubscribe** cancels the registration by releasing the advise sink pointer passed in the **Subscribe** call. 
  
Generally, the advise sink's **IUnknown::Release** method is called during the **Unsubscribe** call. However, if another thread is in the process of calling the [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method for the advise sink object, the **Release** call is delayed until the **OnNotify** method returns. 
  
## See also



[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[IMAPISupport::Subscribe](imapisupport-subscribe.md)
  
[IMAPISupport : IUnknown](imapisupportiunknown.md)

