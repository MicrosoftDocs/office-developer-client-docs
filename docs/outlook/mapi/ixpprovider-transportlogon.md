---
title: "IXPProviderTransportLogon"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IXPProvider.TransportLogon
api_type:
- COM
ms.assetid: 534929f2-36a2-463d-8c4c-d86060cde127
description: "Last modified: July 23, 2011"
---

# IXPProvider::TransportLogon

  
  
**Applies to**: Outlook 
  
Establishes a session in which a client application logs on to a transport provider. 
  
```
HRESULT TransportLogon(
  LPMAPISUP lpMAPISup,
  ULONG_PTR ulUIParam,
  LPSTR lpszProfileName,
  ULONG FAR * lpulFlags,
  LPMAPIERROR FAR * lppMAPIError,
  LPXPLOGON FAR * lppXPLogon
);
```

## Parameters

 _lpMAPISup_
  
> [in] Pointer to the transport provider's support object for callback functions within MAPI for this session. This object remains valid until the transport provider releases it.
    
 _ulUIParam_
  
> [in] Handle to the parent window of any dialog boxes or windows this method displays. The  _ulUIParam_ parameter can be non-null, for example when the LOGON_SETUP flag is set in the  _lpulFlags_ parameter. 
    
 _lpszProfileName_
  
> [in] Pointer to the profile name of the user. The  _lpszProfileName_ parameter is primarily used when a dialog box must be presented. 
    
 _lpulFlags_
  
> [in, out] Bitmask of flags that controls how the logon session is established. The following flags can be set on input by the MAPI spooler:
    
LOGON_NO_CONNECT 
  
> The user account is logging on to this transport provider for purposes other than transmission and reception of messages. The transport provider should not attempt to make any connections to other messaging systems.
    
LOGON_NO_DIALOG 
  
> No dialog box should be displayed even if the currently saved user credentials are invalid or insufficient for logon.
    
LOGON_NO_INBOUND 
  
> The transport provider does not have to initialize for reception of messages and should not accept incoming messages. The MAPI spooler can use the [IXPLogon::TransportNotify](ixplogon-transportnotify.md) method later to signal the transport provider to enable incoming message processing. 
    
LOGON_NO_OUTBOUND 
  
> The transport provider does not have to initialize for sending messages, as the MAPI spooler does not provide any. If a client application requires a connection to a remote provider during the composition of a message so that it can make [IXPLogon::AddressTypes](ixplogon-addresstypes.md) method calls, the transport provider should make the connection. The MAPI spooler can use **TransportNotify** to signal the transport provider when outgoing operations can begin. 
    
MAPI_UNICODE 
  
> The passed-in string for the profile name is in Unicode format. If the MAPI_UNICODE flag is not set, the string is in ANSI format.
    
    The following flags can be set on output by the transport provider:
    
LOGON_SP_IDLE 
  
> Requests that the MAPI spooler frequently call the transport provider's [IXPLogon::Idle](ixplogon-idle.md) method for idle-time processing. 
    
LOGON_SP_POLL 
  
> Requests that the MAPI spooler frequently call the [IXPLogon::Poll](ixplogon-poll.md) method on the returned logon object to check for new messages. If this flag is not set, the MAPI spooler only checks for new messages when the transport provider uses the [IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md) method to notify the spooler that there are new messages to process. A transport provider effectively becomes send-only by not setting this flag and by not notifying the MAPI spooler of message receipt. 
    
LOGON_SP_RESOLVE 
  
> Requests that the MAPI spooler resolve to full addresses all message addresses for recipients not supported by this transport provider. Therefore that the transport provider can construct a reply path for all recipients.
    
MAPI_UNICODE 
  
> The returned strings in the [MAPIERROR](mapierror.md) structure, if any, are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
 _lppMAPIError_
  
> [out] Pointer to a pointer to the returned **MAPIERROR** structure, if any, that contains version, component, and context information for the error. The  _lppMAPIError_ parameter can be set to NULL if there is no **MAPIERROR** structure to return. 
    
 _lppXPLogon_
  
> [out] Pointer to the pointer to the returned transport provider logon object.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    
MAPI_E_FAILONEPROVIDER 
  
> This provider cannot log on, but this error should not disable the service. 
    
MAPI_E_UNCONFIGURED 
  
> The profile does not contain enough information for the logon to be completed. MAPI calls the provider's message service entry point function.
    
MAPI_E_UNKNOWN_CPID 
  
> The provider cannot support the client's code page.
    
MAPI_E_UNKNOWN_LCID 
  
> The provider cannot support the client's locale information.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in a dialog box. 
    
## Remarks

The MAPI spooler calls the **IXPProvider::TransportLogon** method to establish a logon session for a user. 
  
Most transport providers use the [IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md) method provided with the support object pointed to by the  _lpMAPISup_ parameter for saving and retrieving user identity information, server addresses, and credentials. By using **OpenProfileSection**, a transport provider can save arbitrary information and associate it with a logon to a particular resource. For example, a provider can use **OpenProfileSection** to save the account name and password associated with a particular session and any server names or other necessary information that are required to access resources for that session. MAPI hides information associated with a resource from outside access. The profile section made available through  _lpMAPISup_ is managed by the MAPI spooler so data related to this user context is separated from data for other contexts. 
  
The transport provider must call the **IUnknown::AddRef** method on the support object and keep a copy of the pointer to this object as part of the provider logon object. 
  
The profile display name in  _lpszProfileName_ is provided so the transport provider can use it in error messages or logon dialog boxes. If the provider retains this name, it must be copied to storage allocated by the provider. 
  
Transport providers that are tightly coupled with other service providers may have to do additional work at logon to establish the good credentials required for operations between companion providers.
  
Usually, transport providers are opened when the user first logs on to a profile. Because the first logon to a profile therefore generally comes before logon to any message store, the MAPI spooler usually calls **TransportLogon** with both the LOGON_NO_INBOUND and LOGON_NO_OUTBOUND flags set in  _lpulFlags_. Later, when the appropriate message stores are available in the profile session, the MAPI spooler calls **TransportNotify** to initiate incoming and outgoing operations for the transport provider. 
  
Passing the LOGON_NO_CONNECT flag in  _lpulFlags_ signals offline operation of the transport provider. This flag indicates no external connections should be made; if the transport provider cannot establish a session without an external connection, it should return an error value for the logon. 
  
A transport provider should set the LOGON_SP_IDLE flag in  _lpulFlags_ at initialization time if it is designed to use time that the system otherwise spends idle. Such time is often used to handle automatic operations, such as automatic message downloading, timed message downloading, or timed message submission. If this flag is set, the MAPI spooler calls **Idle** when system idle time occurs to initiate such operations. The MAPI spooler does not call **Idle** at set intervals; rather, it is called only during true idle time. Therefore, providers should not work on any assumption about how frequently their **Idle** methods will be called. Providers that support idle-time operations should supply a configuration user interface for it in their provider property sheet. 
  
If the transport provider logon succeeds, the provider should return in the  _lppXPLogon_ parameter a pointer to a logon object. The MAPI spooler will use this object for additional provider access. If **TransportLogon** displays a logon dialog box and the user cancels logon typically by clicking the **Cancel** button in the dialog box the provider should return MAPI_E_USER_CANCEL. 
  
For most error values returned from **TransportLogon**, MAPI disables the message services to which the provider belongs. MAPI will not call any providers that belong to that service for the rest of the MAPI session. In contrast, when **TransportLogon** returns the MAPI_E_FAILONEPROVIDER error value from its logon, MAPI does not disable the message service to which the provider belongs. **TransportLogon** should return MAPI_E_FAILONEPROVIDER if it encounters an error that does not warrant disabling the service for the rest of the session. 
  
If a provider returns MAPI_E_UNCONFIGURED from its logon, MAPI will call the provider's message service entry function and then retry the logon. MAPI passes MSG_SERVICE_CONFIGURE as the context, to give the service a chance to configure itself. If the client has chosen to allow a user interface on the logon, the service can present its configuration property sheet so that the user can enter configuration information. 
  
If the provider finds that all the required information is not in the profile, it should return MAPI_E_UNCONFIGURED so that MAPI calls the provider's message service entry point function. 
  
## See also

#### Reference

[IXPProvider : IUnknown](ixpprovideriunknown.md)
  
[IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md)
  
[IMAPISupport::SpoolerNotify](imapisupport-spoolernotify.md)
  
[IXPLogon::AddressTypes](ixplogon-addresstypes.md)
  
[IXPLogon::Idle](ixplogon-idle.md)
  
[IXPLogon::Poll](ixplogon-poll.md)
  
[IXPLogon::TransportNotify](ixplogon-transportnotify.md)
  
[MAPIERROR](mapierror.md)

