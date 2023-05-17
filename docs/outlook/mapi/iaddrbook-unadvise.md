---
title: "IAddrBookUnadvise"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IAddrBook.Unadvise
api_type:
- COM
ms.assetid: e0db9e86-9528-43de-b8ba-a5af8b7bda4b
---

# IAddrBook::Unadvise

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Cancels a notification registration previously established for an address book entry.
  
```cpp
HRESULT Unadvise(
  ULONG_PTR ulConnection
);
```

## Parameters

 _ulConnection_
  
> [in] A connection number that represents the registration to be canceled. The  _ulConnection_ parameter should contain a value returned by a prior call to the [IAddrBook::Advise](iaddrbook-advise.md) method. 
    
## Return value

S_OK 
  
> The registration was successfully canceled.
    
## Remarks

Clients call the **Unadvise** method to stop receiving notifications about changes to a particular address book entry. When a notification registration is canceled, the address book provider releases its pointer to the caller's advise sink. However, the release can occur during the **Unadvise** call or at some later point, if another thread is in the process of calling the [IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md) method. When a notification is in progress, the release is delayed until the **OnNotify** method returns. 
  
## See also



[IAddrBook::Advise](iaddrbook-advise.md)
  
[IMAPIAdviseSink::OnNotify](imapiadvisesink-onnotify.md)
  
[IAddrBook : IMAPIProp](iaddrbookimapiprop.md)

