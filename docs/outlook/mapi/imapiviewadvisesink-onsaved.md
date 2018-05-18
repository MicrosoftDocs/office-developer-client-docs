---
title: "IMAPIViewAdviseSinkOnSaved"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIViewAdviseSink.OnSaved
api_type:
- COM
ms.assetid: c327e31a-7b62-4e21-9b69-b27442f1eaca
description: "Last modified: July 23, 2011"
---

# IMAPIViewAdviseSink::OnSaved

  
  
**Applies to**: Outlook 
  
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

