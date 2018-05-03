---
title: "ISocialSessionLogonWeb"
ms.author: null
author: null
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f4217030-5fd1-4ec4-a83f-752717fbb787
description: "Logs on to the social network site by using forms-based authentication."
---

# ISocialSession::LogonWeb

Logs on to the social network site by using forms-based authentication.
  
```
HRESULT _stdcall LogonWeb([in] BSTR connectIn, [out] BSTR* connectOut);
```

## Parameters

 _connectIn_
  
> [in] A string that is **null**, an URL to a logon form on the web, or a string that contains logon credentials, depending on the context in the logon process when this method is called.
    
 _connectOut_
  
> [out] A string that contains logon credentials.
    
## Remarks

The Outlook Social Connector (OSC) calls the **LogonWeb** method only if the provider indicates that it supports forms-based authentication. The provider indicates that it requires forms-based authentication by setting **useLogonWebAuth** as **true** in the XML for **capabilities**. If the provider sets **useLogonWebAuth** as **false**, the OSC uses basic authentication and calls the [ISocialSession::Logon](isocialsession-logon.md) method. 
  
Logging on to a social network site by using forms-based authentication involves calling the **LogonWeb** and [ISocialSession::GetLogonUrl](isocialsession-getlogonurl.md) methods in a specific order: 
  
1. The OSC calls **LogonWeb** the first time, passing **null** to the  _connectIn_ parameter. 
    
2. The provider raises the OSC_E_AUTH_ERROR error to the OSC.
    
3. The OSC next calls **GetLogonUrl**.
    
4. The provider returns the appropriate URL to a logon page in the **GetLogonUrl** method. 
    
5. The OSC uses the URL returned by **GetLogonUrl** to display the forms-based logon page. 
    
6. The OSC then calls **LogonWeb** a second time, passing the URL to the logon form in the  _connectIn_ parameter. 
    
7. If authentication succeeds, the provider returns logon credentials in the  _connectOut_ parameter to the OSC. If authentication fails, the provider raises the OSC_E_AUTH_ERROR error to the OSC. 
    
If the OSC provider supports logging on using cached credentials, it specifies **useLogonCached** as **true** in the **capabilities** XML. The provider should place any logon credentials in the  _connectOut_ string that the provider wants the OSC to store across connections. The OSC does not interpret the  _connectOut_ string. After the OSC verifies that **useLogonCached** is **true**, the OSC encrypts the string for security before storing it in the Windows registry. The OSC passes this string to the  _connectIn_ parameter on subsequent attempts to log on to the social network by calling [ISocialSession2::LogonCached](isocialsession2-logoncached.md). 
  
For information about error codes, see [Outlook Social Connector Provider Error Codes](outlook-social-connector-provider-error-codes.md).
  
## See also

#### Reference

[ISocialSession : IUnknown](isocialsessioniunknown.md)
#### Concepts

[Forms-Based Authentication](forms-based-authentication.md)

