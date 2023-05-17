---
title: "ISocialSessionGetPerson"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
ms.assetid: 2d0a2945-54d7-417f-b5c6-2647c70263cf
description: "Gets an ISocialPerson interface based on the userID parameter."
---

# ISocialSession::GetPerson

Gets an [ISocialPerson](isocialpersoniunknown.md) interface based on the  _userID_ parameter. 
  
```cpp
HRESULT _stdcall GetPerson([in] BSTR userId, [out, retval] ISocialPerson** result);
```

## Parameters

_userId_
  
> [in] A string that contains a user ID or SMTP address of a person.
    
_result_
  
> [out] An **ISocialPerson** interface. 
    
## Remarks

The  _userID_ parameter must be a user ID or SMTP address. 
  
## See also

- [ISocialSession : IUnknown](isocialsessioniunknown.md)

