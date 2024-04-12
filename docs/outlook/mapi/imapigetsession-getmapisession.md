---
title: "IMAPIGetSessionGetMAPISession"
 
 
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- IMAPIGetSession.GetMAPISession
api_type:
- COM
ms.assetid: 581db5d9-35f7-43ad-aef3-a5d5da310150
---

# IMAPIGetSession::GetMAPISession

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns a pointer to the MAPI session associated with the MAPI support object.
  
```cpp
HRESULT GetMAPISession(
  LPUNKNOWN *  lppSession
);
```

## Parameters

 _lppSession_
  
> [out] A pointer to the current MAPI session.
    
## See also



[IMAPIGetSession : IUnknown](imapigetsessioniunknown.md)


[Support Object Overview](support-object-overview.md)

