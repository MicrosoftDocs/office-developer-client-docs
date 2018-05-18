---
title: "IMAPIViewAdviseSinkOnSubmitted"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIViewAdviseSink.OnSubmitted
api_type:
- COM
ms.assetid: a2401662-1ddc-40d8-a5a7-ceca24442bd4
description: "Last modified: July 23, 2011"
---

# IMAPIViewAdviseSink::OnSubmitted

  
  
**Applies to**: Outlook 
  
Notifies the form viewer that the current message has been submitted to the MAPI spooler.
  
```cpp
HRESULT OnSubmitted( void );
```

## Parameters

None
  
## Return value

S_OK 
  
> The notification succeeded.
    
## Remarks

A form object calls the **IMAPIViewAdviseSink::OnSubmitted** method after a call to [IMAPIMessageSite::SubmitMessage](imapimessagesite-submitmessage.md) has returned successfully. 
  
## Notes to implementers

After **OnSubmitted** is called, you can continue on the assumption that the message has been updated. Update your windows to reflect any changes that have occurred. 
  
For more information about form notifications, see [Sending and Receiving Form Notifications](sending-and-receiving-form-notifications.md).
  
## See also



[IMAPIMessageSite::SubmitMessage](imapimessagesite-submitmessage.md)
  
[IMAPIViewAdviseSink : IUnknown](imapiviewadvisesinkiunknown.md)

