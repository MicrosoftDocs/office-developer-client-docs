---
title: "IABProviderLogon"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IABProvider.Logon
api_type:
- COM
ms.assetid: f9468715-1674-4d14-81c8-2f24dbaa0453
description: "Last modified: July 23, 2011"
---

# IABProvider::Logon

  
  
**Applies to**: Outlook 
  
Establishes a connection to an active session.
  
```cpp
HRESULT Logon(
  LPMAPISUP lpMAPISup,
  ULONG_PTR ulUIParam,
  LPSTR lpszProfileName,
  ULONG ulFlags,
  ULONG FAR * lpulcbSecurity,
  LPBYTE FAR * lppbSecurity,
  LPMAPIERROR FAR * lppMAPIError,
  LPABLOGON FAR * lppABLogon
);
```

## Parameters

 _lpMAPISup_
  
> [in] A pointer to the address book provider's support object.
    
 _ulUIParam_
  
> [in] A handle to the parent window for the logon dialog box that the **Logon** method displays, if permitted. The  _ulUIParam_ parameter contains the value of the parameter of the same name passed to MAPI in the previous call to the [MAPILogonEx](mapilogonex.md) function. 
    
 _lpszProfileName_
  
> [in] A pointer to the name of the session profile.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the logon is performed. The following flags can be set:
    
AB_NO_DIALOG 
  
> The provider should not display a dialog box during logon. If this flag is not set, the provider can display a dialog box to prompt the user for missing configuration information.
    
MAPI_DEFERRED_ERRORS 
  
> Enables **Logon** to return successfully, possibly before the logon process is finished. 
    
MAPI_UNICODE 
  
> All strings should be in Unicode format. If the MAPI_UNICODE flag is not set, the strings should be in ANSI format.
    
 _lpulcbSecurity_
  
> [in, out] A pointer to the size, in bytes, of the security credentials structure pointed to by the  _lppbSecurity_ parameter. On input, the value must be nonzero; on output, the value must be zero. In both cases, the pointers must be valid. 
    
 _lppbSecurity_
  
> [in, out] A pointer to a pointer to security credentials. On input, the value must be nonzero; on output, the value must be zero. In both cases the pointer must be valid.
    
 _lppMAPIError_
  
> [out] A pointer to a pointer to a [MAPIERROR](mapierror.md) structure. The  _lppMAPIError_ parameter can be set to NULL if there is no **MAPIERROR** structure to return. 
    
 _lppABLogon_
  
> [out] A pointer to a pointer to the provider's logon object.
    
## Return value

S_OK 
  
> A connection to an active session was successfully established.
    
MAPI_E_FAILONEPROVIDER 
  
> The provider cannot log on, but MAPI can continue to log on the other providers in the message service to which the provider belongs. 
    
MAPI_E_UNCONFIGURED 
  
> The provider has insufficient information to complete the logon. MAPI calls the provider's message service entry function.
    
MAPI_E_UNKNOWN_CPID 
  
> The server is not configured to support the client's code page.
    
MAPI_E_UNKNOWN_LCID 
  
> The server is not configured to support the client's locale information.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in the logon dialog box. 
    
## Remarks

Connections are established with each address book provider in the session profile when a client calls the [IMAPISession::OpenAddressBook](imapisession-openaddressbook.md) method. **OpenAddressBook** then calls each provider's **Logon** method. 
  
The profile name pointed to by the  _lpszProfileName_ parameter is displayed in the character set of the user's client as indicated by the presence or absence of the MAPI_UNICODE flag in the  _ulFlags_ parameter. 
  
## Notes to implementers

In your implementation of the **Logon** method, call the [IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md) method to register a unique identifier, or [MAPIUID](mapiuid.md) structure. Each of your objects will have an entry identifier that includes this **MAPIUID**. MAPI uses the **MAPIUID** to match an object with its provider. For example, when a client calls the [IMAPISession::OpenEntry](imapisession-openentry.md) method to open a messaging user, **OpenEntry** examines the **MAPIUID** portion of the entry identifier that was passed in and matches it with a **MAPIUID** registered by an address book provider. 
  
If a client logs on to your provider more than once, you may want to register a different **MAPIUID** for each logon. Registering unique **MAPIUID** structures enables MAPI to correctly route requests to the appropriate provider instance. However, you may want to have every logon object share one **MAPIUID**. In this case, you must be able to handle the routing yourself instead of relying on MAPI. For more information about how to create a **MAPIUID**, see [Registering Service Provider Unique Identifiers](registering-service-provider-unique-identifiers.md).
  
The support object that MAPI passes to your **Logon** method in the  _lpMAPISup_ parameter provides access to many of the methods included in the [IMAPISupport : IUnknown](imapisupportiunknown.md) interface. MAPI creates a support object that is customized to your type of provider. For example, if you need to log on to an underlying messaging system or directory service when you establish your connection, you can call the [IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md) method to retrieve security credentials for this particular logon session. 
  
If **Logon** is successful, be sure that you call the support object's [IUnknown::AddRef](http://msdn.microsoft.com/en-us/library/ms691379%28VS.85%29.aspx) method to increment its reference count. This enables your provider to hold onto the support object pointer for the rest of the session. If you do not call this **AddRef** method, MAPI will unload your provider. 
  
You can include the profile name passed in the  _lpszProfileName_ parameter in error dialog boxes, logon screens, or other user interfaces. To use the profile name, copy it to storage that you have allocated. 
  
Create a logon object and return a pointer to it in the  _lppABLogon_ parameter. MAPI uses this logon object to make calls to the methods in your [IABLogon](iablogoniunknown.md) implementation. 
  
If you require a password during logon, display a logon dialog box only if the AB_NO_DIALOG flag is not set. If the user cancels the logon process, typically by clicking the **Cancel** button in the dialog box, return MAPI_E_USER_CANCEL from **Logon**.
  
Typically, when an address book provider cannot log on, MAPI disables the message service to which the failing provider belongs—that is, MAPI will not try to establish connections for any of the other providers that belong to the service for the rest of the session's lifetime. However, if your provider cannot establish a connection and you want not to disable the entire service, return either MAPI_E_FAILONEPROVIDER or MAPI_E_UNCONFIGURED. MAPI will not disable the message service to which the provider belongs. 
  
Return MAPI_E_FAILONEPROVIDER if an error occurs that is not serious enough to prevent the other providers in the message service from establishing connections. Return MAPI_E_UNCONFIGURED if the necessary configuration information is missing from the profile and you cannot display a dialog box to prompt the user. MAPI will respond by calling your provider's message service entry point function with MSG_SERVICE_CONFIGURE set as the  _ulContext_ parameter to give the service a chance to configure itself, either programmatically or using a property sheet. When the message service entry point function has finished, MAPI retries the logon. 
  
## See also



[IABLogon::Logoff](iablogon-logoff.md)
  
[IABLogon::OpenEntry](iablogon-openentry.md)
  
[IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md)
  
[IMAPISupport::SetProviderUID](imapisupport-setprovideruid.md)
  
[MSGSERVICEENTRY](msgserviceentry.md)
  
[IABProvider : IUnknown](iabprovideriunknown.md)

