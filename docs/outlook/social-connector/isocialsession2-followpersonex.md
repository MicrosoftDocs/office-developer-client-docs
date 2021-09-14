---
title: "ISocialSession2FollowPersonEx"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 17b4af7f-7967-422b-996c-792705c93ad3
description: "Adds the person identified by the emailAddresses and displayName parameters as a friend for the logged-on user on the social network."
---

# ISocialSession2::FollowPersonEx

Adds the person identified by the  _emailAddresses_ and  _displayName_ parameters as a friend for the logged-on user on the social network. 
  
```cpp
HRESULT _stdcall FollowPersonEx([in] SAFEARRAY(BSTR) emailAddresses, [in] BSTR displayName);
```

## Parameters

_emailAddresses_
  
> [in] An array that contains one or multiple valid SMTP addresses for a person on the social network.
    
_displayName_
  
> [in] A string that contains the display name of the person to be added as a friend.
    
## Remarks

If the Outlook Social Connector (OSC) provides more than on SMTP address in the array in the **emailAddresses** parameter, the OSC provider can assume the first element is the primary SMTP address. 
  
If the provider has set the **followPerson** element as **true** in the **capabilities** XML, and none of the elements for  _emailAddresses_ match a user on the network, the provider must return the OSC_E_NOT_FOUND error. If the provider has set **followPerson** as **false** in **capabilities**, the provider should return the OSC_E_FAIL error. 
  
If the **FollowPersonEx** method succeeds, the provider can use the string in the  _displayName_ parameter to address the person in any subsequent friend-confirmation email, rather than addressing the person by the SMTP address. On the other hand, the provider must be able to handle the OSC passing an empty string for the  _displayName_ parameter. 
  
If the provider implements the [ISocialSession2](isocialsession2iunknown.md) interface and has set **followPerson** as **true** in the capabilities XML, the OSC calls **FollowPersonEx** instead of [ISocialSession::FollowPerson](isocialsession-followperson.md). If the provider has set **followPerson** as **true** but does not implement the **ISocialSession2** interface, or **FollowPersonEx** returns the OSC_E_NOTIMPL error, the OSC calls **ISocialSession::FollowPerson**.
  
## See also

- [ISocialSession2 : IUnknown](isocialsession2iunknown.md)

