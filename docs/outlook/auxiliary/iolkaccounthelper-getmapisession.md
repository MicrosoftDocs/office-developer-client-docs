---
title: "IOlkAccountHelperGetMapiSession"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
 
localization_priority: Normal
ms.assetid: a431787c-6e9a-9be1-165f-98c778d12e3e
description: "Opens a MAPI session and maintains a reference to the session for the account manager."
---

# IOlkAccountHelper::GetMapiSession

Opens a MAPI session and maintains a reference to the session for the account manager.
  
## Quick Info

See [IOlkAccountHelper](iolkaccounthelper.md).
  
```
HRESULT IOlkAccountHelper::GetMapiSession(  
    LPUNKNOWN *ppmsess 
);
```

## Parameters

 _ppmsess_
  
> [out] The current MAPI session.
    
## Return Values

S_OK if the call succeeded; otherwise, an error code.
  
## Remarks

Because of circular reference problems, the account manager itself cannot maintain the reference for the MAPI session.
  
## See also

#### Concepts

[IOlkAccountHelper::HandsOffSession](iolkaccounthelper-handsoffsession.md)
#### Other resources

[IMAPISession : IUnknown](http://msdn.microsoft.com/library/5650fa2a-6e62-451c-964e-363f7bee2344%28Office.15%29.aspx)

