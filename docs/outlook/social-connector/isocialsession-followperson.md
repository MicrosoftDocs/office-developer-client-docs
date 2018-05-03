---
title: "ISocialSessionFollowPerson"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: de7f56e2-c131-4955-b945-0a72043e0f5a
description: "Adds the person identified by the emailAddress parameter as a friend for the logged-on user on the social network."
---

# ISocialSession::FollowPerson

Adds the person identified by the  _emailAddress_ parameter as a friend for the logged-on user on the social network. 
  
```
HRESULT _stdcall FollowPerson([in] BSTR emailAddress);
```

## Parameters

 _emailAddress_
  
> [in] A string that contains an email address of a person.
    
## Remarks

The  _emailAddress_ parameter must be a valid SMTP address. If the Outlook Social Connector (OSC) provider has set the **followPerson** method as **true** in **capabilities**, and the argument for  _emailAddress_ does not match a user on the network, the provider must return the OSC_E_NOT_FOUND error. If the provider has set **followPerson** as **false** in **capabilities**, the provider should return the OSC_E_FAIL error.
  
If the provider implements the [ISocialSession2](isocialsession2iunknown.md) interface and has set **followPerson** as **true** in **capabilities**, the OSC will call [ISocialSession2::FollowPersonEx](isocialsession2-followpersonex.md) instead of **ISocialSession::FollowPerson**. If the provider does not implement the **ISocialSession2** interface, or **ISocialSession2::FollowPersonEx** returns the OSC_E_NOTIMPL error, the OSC will call **ISocialSession::FollowPerson** as long as the provider has set **followPerson** as **true** in **capabilities**. For information about error codes, see [Outlook Social Connector Provider Error Codes](outlook-social-connector-provider-error-codes.md).
  
In deciding whether to implement **ISocalSession::FollowPerson** or **ISocialSession2::FollowPersonEx**, you should consider whether your provider needs the other methods in **ISocialSession2**, and whether you can use the  _djsplayName_ parameter in **FollowPersonEx**.
  
## See also

#### Reference

[ISocialSession : IUnknown](isocialsessioniunknown.md)

