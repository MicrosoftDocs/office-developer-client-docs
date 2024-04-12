---
title: "IMAPIViewAdviseSinkOnSaved"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIViewAdviseSink.OnSaved
api_type:
- COM
ms.assetid: c327e31a-7b62-4e21-9b69-b27442f1eaca
---

# IMAPIViewAdviseSink::OnSaved

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Notifies the form viewer that the current message in a form has been saved.
  
```cpp
HRESULT OnSaved( void );
```

## Parameters

None
  
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
## Remarks

A form object calls the **IMAPIViewAdviseSink::OnSaved** method after the current message in a form has been successfully saved. Doing so permits viewers to update their windows to reflect changes to the message. 
  
For more information about form notifications, see [Sending and Receiving Form Notifications](sending-and-receiving-form-notifications.md).
  
## See also



[IMAPIViewAdviseSink : IUnknown](imapiviewadvisesinkiunknown.md)

