---
title: "ISocialSessionUnFollowPerson"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 66c83041-ee83-41d5-b9dc-a4dc4c670f82
description: "Removes the person identified by the userID parameter as a friend on the social network."
---

# ISocialSession::UnFollowPerson

Removes the person identified by the  _userID_ parameter as a friend on the social network. 
  
```
HRESULT _stdcall UnFollowPerson([in] BSTR userID);
```

## Parameters

 _userID_
  
> [in] A string that contains a social network user ID for a person.
    
## Remarks

The  _userID_ parameter must be a valid user ID for the person on the social network. 
  
If the Outlook Social Connector (OSC) provider has set **doNotFollowPerson** as **true** in the XML for **capabilities**, the provider must return the OSC_E_NOT_FOUND error in the case that the user ID passed in does not match a user on the network. If the provider has set **doNotFollowPerson** as **false** in **capabilities**, the provider should return the OSC_E_FAIL error. For information about error codes, see [Outlook Social Connector Provider Error Codes](outlook-social-connector-provider-error-codes.md).
  
## See also

#### Reference

[ISocialSession : IUnknown](isocialsessioniunknown.md)

