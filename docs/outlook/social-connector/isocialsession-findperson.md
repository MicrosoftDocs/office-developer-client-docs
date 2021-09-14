---
title: "ISocialSessionFindPerson"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: a86cb847-5d49-44b8-b2bc-0e35e70395b4
description: "Gets a string that represents one or more persons who match the userID parameter."
---

# ISocialSession::FindPerson

Gets a string that represents one or more persons who match the  _userID_ parameter. 
  
```cpp
HRESULT _stdcall FindPerson([in] BSTR userId, [out, retval] BSTR* result);
```

## Parameters

_userId_
  
> [in] A social network user ID, SMTP address, or display name of a person.
    
_result_
  
> [out] An XML string that represents one or more persons who match the identification information specified by the  _userId_ parameter. 
    
## Remarks

If one or more persons match the **FindPerson** request, this method returns the information for those persons in the  _result_ parameter. The  _result_ XML string must comply with the schema definition for **friends**, as defined in the schema for Outlook Social Connector (OSC) provider extensibility. 
  
## See also

- [ISocialSession : IUnknown](isocialsessioniunknown.md)

