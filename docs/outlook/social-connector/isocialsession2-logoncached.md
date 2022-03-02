---
title: "ISocialSession2LogonCached"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 8cac444b-0e81-44ff-a7a0-87793b533e26
description: "Logs on to the social network site by using cached credentials."
---

# ISocialSession2::LogonCached

Logs on to the social network site by using cached credentials.
  
```cpp
HRESULT _stdcall LogonCached([in] BSTR connectIn, [in] BSTR userName, [in] BSTR password, [out] BSTR connectOut);
```

## Parameters

_connectIn_
  
> [in] A string that can be empty or contains the logon credentials, depending on the context in which the OSC is calling **LogonCached**.

_userName_
  
> [in] A string that contains the user name.

_password_
  
> [in] A string that contains the user's password.

_connectOut_
  
> [out] An opaque string that contains credentials.

## Remarks

This method is called for authentication only if **useLogonCached** is set as **true** in the **capabilities** XML returned by [ISocialProvider::GetCapabilities](isocialprovider-getcapabilities.md).
  
The Outlook Social Connector (OSC) calls **LogonCached**, and passes an empty string for _connectIn_ and non-empty _userName_ and _password_ strings. The provider uses _userName_ and  _password_ to log on to the social network, and returns an opaque _connectOut_ parameter to the OSC if authentication succeeds. If authentication fails, the provider returns the OSC_E_LOGON_FAILURE error to the OSC.
  
The _connectOut_ parameter is an opaque string to the OSC, and is passed to the _connectIn_ parameter on subsequent attempts by the OSC to log on to the social network. The provider should place any credentials in the _connectOut_ string that the provider wants the OSC to store across connections. The OSC does not interpret the string in _connectOut_, and encrypts the string for security purposes before storing it in the Windows registry.
  
## See also

- [ISocialSession2 : IUnknown](isocialsession2iunknown.md)
