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
description: "Converts a simple MAPI session to a MAPI session"
---

# ScMAPIXFromSMAPI
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Converts a simple MAPI session to a MAPI session. 
  
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
 
> [in] The simple MAPI session that was created by a call to MAPILOGON. 

_ulFlags_ 

> [in] Reserved; must be zero. 

_lpInterface_ 

> [in] A pointer to the interface identifier (IID) that represents the interface to be used to access the session. Passing NULL causes the lppMAPISession parameter to return a pointer to the standard interface for a MAPI session (IMAPISession).

_lppMAPISession_

> [out] Pointer to a pointer to the MAPI session interface.

## Return value

_S_OK_

> The simple MAPI session was successfully converted to a MAPI session. 

_MAPI_E_INVALID_PARAMETER_

> lhSimpleSession could not be converted to a MAPI session. 

_MAPI_E_UNKNOWN_FLAGS_ 

> ulFlags contained invalid flags. 

_E_NOINTERFACE_

> The session could not be converted into the interface specified by lpInterface.

## Remarks

There are no inverse functions for **ScMAPIXFromSMAPI** function, that is, a client cannot convert to a simple MAPI session from a MAPI session.

## See also 

[MAPILOGON](/windows/win32/api/mapi/nc-mapi-mapilogon)

[MAPILogonEx](/office/client-developer/outlook/mapi/mapilogonex)  
