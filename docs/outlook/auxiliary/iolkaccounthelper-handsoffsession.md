---
title: "IOlkAccountHelperHandsOffSession"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 9f71fdef-5df5-0892-b64c-293a2f22f5c3
description: "Releases the MAPI session object that was returned by IOlkAccountHelper::GetMapiSession."
---

# IOlkAccountHelper::HandsOffSession

Releases the MAPI session object that was returned by [IOlkAccountHelper::GetMapiSession](iolkaccounthelper-getmapisession.md).
  
## Quick Info

See [IOlkAccountHelper](iolkaccounthelper.md).
  
```
HRESULT IOlkAccountHelper::HandsOffSession( );
```

## Return Values

|**HRESULT**|**Description**|
|:-----|:-----|
|S_OK  <br/> |If your implementation of **IOlkAccountHelper** creates its own MAPI session that is returned in **IOlkAccountHelper::GetMapiSession**, you must release the session here and return S_OK.  <br/> |
|E_NOTIMPL  <br/> |If your implementation of **IOlkAccountHelper** did not create its own MAPI session, you must return only E_NOTIMPL. In this case, this is the only supported return value.  <br/> |
   
## See also

#### Concepts

[Constants (Account management API)](constants-account-management-api.md)
  
[IOlkAccountHelper::GetMapiSession](iolkaccounthelper-getmapisession.md)

