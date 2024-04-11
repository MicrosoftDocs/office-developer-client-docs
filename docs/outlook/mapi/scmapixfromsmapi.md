---
title: "ScMAPIXFromSMAPI"
manager: lindalu
ms.date: 04/10/2024
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- ScMAPIXFromSMAPI
api_type:
- HeaderDef
ms.assetid: a3b98bcd-e4dd-4143-9ca6-0fe3bf5eafe6
description: "Converts a simply MAPI session to an extended MAPI session"
---

# ScMAPIXFromSMAPI
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Converts a simply MAPI session to an extended MAPI session. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapi.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```cpp
SCODE ScMAPIXFromSMAPI(
  LHANDLE lhSimpleSession, 
  ULONG ulFlags, 
  LPCIID lpInterface, 
  LPMAPISESSION FAR * lppMAPISession 
); 
```

## Parameters

 _lhSimpleSession_ 
 
> [in] The Simple MAPI session that was created by a call to MAPILOGON. <br/>

_ulFlags_ 

> [in] must be zero. <br/>

_lpInterface_ <br/>
