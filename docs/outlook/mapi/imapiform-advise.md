---
title: "IMAPIFormAdvise"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIForm.Advise
api_type:
- COM
ms.assetid: 961318d6-bebe-4f4b-98ff-921cafc68d24
---

# IMAPIForm::Advise

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Registers a form viewer for notifications about events that affect the form.
  
```cpp
HRESULT Advise(
  LPMAPIVIEWADVISESINK pAdvise,
  ULONG FAR * pulConnection
);
```

## Parameters

 _pAdvise_
  
> [in] A pointer to a view advise sink object to receive the subsequent notifications. 
    
 _pulConnection_
  
> [out] A pointer to a nonzero value that represents a successful notification registration.
    
## Return value

S_OK 
  
> The registration was successful.
    
E_OUTOFMEMORY 
  
> The registration was unsuccessful because of insufficient memory.
    
## Remarks

Form viewers call a form's **IMAPIForm::Advise** method to register for notification when changes occur to the form. 
  
## Notes to implementers

Keep a copy of the view advise sink pointer passed in the _pAdvise_ parameter so that you can use it to call the appropriate [IMAPIViewAdviseSink](imapiviewadvisesinkiunknown.md) method when an event occurs. Call the view advise sink's [IUnknown::AddRef](https://msdn.microsoft.com/library/ms691379%28VS.85%29.aspx) method to retain the pointer until notification registration is canceled. Set the contents of the  _pulConnection_ parameter to a nonzero number. 
  
Many forms implement a helper object to handle the registration and subsequent notification of events. 
  
For more information about the notification process in general, see [Event Notification in MAPI](event-notification-in-mapi.md). 
  
For more information about notification and forms, see [Sending and Receiving Form Notifications](sending-and-receiving-form-notifications.md).
  
## See also



[IMAPIForm::Unadvise](imapiform-unadvise.md)
  
[IMAPIViewAdviseSink : IUnknown](imapiviewadvisesinkiunknown.md)
  
[IMAPIForm : IUnknown](imapiformiunknown.md)


[Event Notification in MAPI](event-notification-in-mapi.md)
  
[Sending and Receiving Form Notifications](sending-and-receiving-form-notifications.md)

