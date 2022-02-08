---
title: "IMAPIFormUnadvise"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIForm.Unadvise
api_type:
- COM
ms.assetid: fdda45e2-631d-404c-8af4-bce68df0968b
description: "Last modified: July 23, 2011"
---

# IMAPIForm::Unadvise

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Cancels a registration for notifications with a form viewer previously established by calling [IMAPIForm::Advise](imapiform-advise.md).
  
```cpp
HRESULT Unadvise(
  ULONG ulConnection
);
```

## Parameters

 _ulConnection_
  
> [in] A connection number that identifies the notification registration to be canceled.
    
## Return value

S_OK 
  
> The registration was canceled.
    
E_INVALIDARG 
  
> The connection number passed in the _ulConnection_ parameter does not represent a valid registration. 
    
## Remarks

Form viewers call the **IMAPIForm::Unadvise** method to cancel a registration for notification that they first established by calling the **IMAPIForm::Advise** method. 
  
## Notes to implementers

Discard the pointer that you are holding to the form viewer's view advise sink by calling its [IUnknown::Release](https://msdn.microsoft.com/library/ms682317%28v=VS.85%29.aspx) method. Generally, **Release** is called during the **Unadvise** call. However, if another thread is in the process of calling one of the [IMAPIViewAdviseSink](imapiviewadvisesinkiunknown.md) methods for the view advise sink, delay the **Release** call until the **IMAPIViewAdviseSink** method returns. 
  
## See also



[IMAPIForm::Advise](imapiform-advise.md)
  
[IMAPIViewAdviseSink : IUnknown](imapiviewadvisesinkiunknown.md)
  
[IMAPIForm : IUnknown](imapiformiunknown.md)

