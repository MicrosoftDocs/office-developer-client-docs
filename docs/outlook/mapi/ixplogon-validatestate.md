---
title: "IXPLogonValidateState"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- IXPLogon.ValidateState
api_type:
- COM
ms.assetid: c3649daa-cba1-48e3-9ffb-069c1bcf8228
description: "Last modified: July 23, 2011"
---

# IXPLogon::ValidateState

  
  
**Applies to**: Outlook 
  
Checks the transport provider's external status. 
  
```cpp
HRESULT ValidateState(
  ULONG_PTR ulUIParam,
  ULONG ulFlags
);
```

## Parameters

 _ulUIParam_
  
> [in] A handle to the parent window of any dialog boxes or windows that this method displays.
    
 _ulFlags_
  
> [in] A bitmask of flags that controls how the status check is performed and the results of the status check. The following flags can be set:
    
ABORT_XP_HEADER_OPERATION 
  
> The user canceled the operation, typically by clicking the **Cancel** button in a dialog box. The transport provider has the option to continue working on the operation, or it can abort the operation and return MAPI_E_USER_CANCELED. 
    
CONFIG_CHANGED 
  
> Validates the state of currently loaded transport providers by causing the MAPI spooler to call their [IXPLogon::AddressTypes](ixplogon-addresstypes.md) method. This flag also provides the MAPI spooler an opportunity to correct critical transport-provider failures without forcing client applications to log off and then log on again. 
    
FORCE_XP_CONNECT 
  
> The user selected a connect operation. When this flag is used with the REFRESH_XP_HEADER_CACHE or PROCESS_XP_HEADER_CACHE flag, the connect action occurs without caching.
    
FORCE_XP_DISCONNECT 
  
> The user selected a disconnect operation. When this flag is used with REFRESH_XP_HEADER_CACHE or PROCESS_XP_HEADER_CACHE, the disconnect action occurs without caching.
    
PROCESS_XP_HEADER_CACHE 
  
> Entries in the header cache table should be processed, all messages marked with the MSGSTATUS_REMOTE_DOWNLOAD flag should be downloaded, and all messages marked with the MSGSTATUS_REMOTE_DELETE flag should be deleted. Messages that have both MSGSTATUS_REMOTE_DOWNLOAD and MSGSTATUS_REMOTE_DELETE set should be moved.
    
REFRESH_XP_HEADER_CACHE 
  
> A new list of message headers should be downloaded, and all message status marking flags should be cleared.
    
SUPPRESS_UI 
  
> Prevents the transport provider from displaying a user interface.
    
## Return value

S_OK 
  
> The call succeeded and returned the expected value or values.
    
MAPI_E_BUSY 
  
> Another operation is in progress; it should be allowed to complete, or it should be stopped before this operation is attempted.
    
MAPI_E_NO_SUPPORT 
  
> The remote transport provider involved does not support a user interface, and the client application itself should display the dialog box.
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in a dialog box. 
    
## Remarks

The MAPI spooler calls the **IXPLogon::ValidateState** method to support calls to the [IMAPIStatus::ValidateState](imapistatus-validatestate.md) method for the status object. The transport provider should respond to the **IXPLogon::ValidateState** call exactly as if the MAPI spooler had opened a status object for the current logon session and then called **IMAPIStatus::ValidateState** on that object. 
  
To support its implementation of **IMAPIStatus::ValidateState**, the MAPI spooler calls **IXPLogon::ValidateState** on all logon objects for all active transport providers that are running in a profile session. 
  
## See also



[IMAPIStatus::ValidateState](imapistatus-validatestate.md)
  
[IXPLogon::AddressTypes](ixplogon-addresstypes.md)
  
[IXPLogon : IUnknown](ixplogoniunknown.md)

