---
title: "IMAPIViewAdviseSinkOnNewMessage"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIViewAdviseSink.OnNewMessage
api_type:
- COM
ms.assetid: 0a2fb371-90ea-41dc-b2ab-051cf790e85a
description: "Last modified: July 23, 2011"
---

# IMAPIViewAdviseSink::OnNewMessage

  
  
**Applies to**: Outlook 
  
Notifies the form viewer that a new or an existing message has been loaded in a form.
  
```cpp
HRESULT OnNewMessage( void );
```

## Parameters

None
  
## Return value

S_OK 
  
> The notification succeeded.
    
## Remarks

Form objects call the **IMAPIViewAdviseSink::OnNewMessage** method whenever a message is loaded in a form using either the [IPersistMessage::InitNew](ipersistmessage-initnew.md) or [IPersistMessage::Load](ipersistmessage-load.md) method. 
  
## Notes to Implementers

Release your active pointer to the form object because it no longer points to the message your viewer was formerly viewing. 
  
For more information about form notifications, see [Sending and Receiving Form Notifications](sending-and-receiving-form-notifications.md).
  
## See also

#### Reference

[IMAPIForm : IUnknown](imapiformiunknown.md)
  
[IPersistMessage::InitNew](ipersistmessage-initnew.md)
  
[IPersistMessage::Load](ipersistmessage-load.md)
  
[IMAPIViewAdviseSink : IUnknown](imapiviewadvisesinkiunknown.md)

