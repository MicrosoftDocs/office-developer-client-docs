---
title: "IMAPIGetSessionGetMAPISession"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IMAPIGetSession.GetMAPISession
api_type:
- COM
ms.assetid: 581db5d9-35f7-43ad-aef3-a5d5da310150
description: "Last modified: July 23, 2011"
---

# IMAPIGetSession::GetMAPISession

  
  
**Applies to**: Outlook 
  
Returns a pointer to the MAPI session associated with the MAPI support object.
  
```
HRESULT GetMAPISession(
  LPUNKNOWN *  lppSession
);
```

## Parameters

 _lppSession_
  
> [out] A pointer to the current MAPI session.
    
## See also

#### Reference

[IMAPIGetSession : IUnknown](imapigetsessioniunknown.md)
#### Concepts

[Support Object Overview](support-object-overview.md)

