---
title: "MAPILogonEx"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPILogonEx
api_type:
- HeaderDef
ms.assetid: 98091e5b-1abd-4814-9c7a-583b420ee11d
description: "Last modified: March 09, 2015"
---

# MAPILogonEx

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Logs a client application on to a session with the messaging system. 
  
|Property|Description|
|:-----|:-----|
|Header file:  <br/> |Mapix.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications  <br/> |
   
```cpp
HRESULT MAPILogonEx(
  ULONG_PTR ulUIParam,
  LPSTR lpszProfileName,
  LPSTR lpszPassword,
  FLAGS flFlags,
  LPMAPISESSION FAR * lppSession
);
```

## Parameters

 _ulUIParam_
  
> [in] Handle to the window to which the logon dialog box is modal. If no dialog box appears during the call, the  _ulUIParam_ parameter is ignored. This parameter can be zero. 
    
 _lpszProfileName_
  
> [in] Pointer to a string that contains the name of the profile to use when the user logs on. This string is limited to 64 characters.
    
 _lpszPassword_
  
> [in] Pointer to a string that contains the password of the profile. The  _lpszPassword_ parameter must be NULL. 
    
 _flFlags_
  
> [in] Bitmask of flags used to control how logon is performed. The following flags can be set:
    
MAPI_ALLOW_OTHERS 
  
> The shared session should be returned, which allows later clients to obtain the session without providing any user credentials. 
    
MAPI_BG_SESSION
  
> Log on to a session and run any operations in the background. In general, if a client intends to do processing on a background thread or in a separate process in a manner that is unobtrusive to the foreground thread, it should call with the MAPI_BG_SESSION flag. A client application such as an indexing engine or opening a Personal Folders File (PST) for background type access are some examples of where to use MAPI_BG_SESSION.MAPILogonEx.
    
MAPI_EXPLICIT_PROFILE 
  
> The default profile should not be used and the user should be required to supply a profile. 
    
MAPI_EXTENDED 
  
> Log on with extended capabilities. This flag should always be set.
    
MAPI_FORCE_DOWNLOAD 
  
> An attempt should be made to download all of the user's messages before returning. If the MAPI_FORCE_DOWNLOAD flag is not set, messages can be downloaded in the background after the call to MAPILogonEx returns. 
    
MAPI_LOGON_UI 
  
> A dialog box should be displayed to prompt the user for logon information if required. When the MAPI_LOGON_UI flag is not set, the calling client does not display a logon dialog box and returns an error value if the user is not logged on.
    
MAPI_NEW_SESSION 
  
> An attempt should be made to create a new MAPI session instead of acquiring the shared session. If the MAPI_NEW_SESSION flag is not set, MAPILogonEx uses an existing shared session even if the _lpszprofileName_ parameter is not NULL. 
    
MAPI_NO_MAIL 
  
> MAPI should not inform the MAPI spooler of the session's existence. The result is that no messages can be sent or received in the session except through a tightly coupled store and transport pair. A calling client sets this flag if it is acting as an agent, if configuration work must be done, or if the client is browsing the available message stores. 
    
MAPI_NT_SERVICE 
  
> The caller is running as a Windows service. Callers that are not running as a Windows service should not set this flag; callers that are running as a service must set this flag. 
    
MAPI_SERVICE_UI_ALWAYS 
  
> MAPILogonEx should display a configuration dialog box for each message service in the profile. The dialog boxes are displayed after the profile has been chosen but before any message service is logged on. The MAPI common dialog box for logon also contains a check box that requests the same operation. 
    
MAPI_TIMEOUT_SHORT 
  
> The logon should fail if blocked for more than a few seconds. 
    
MAPI_UNICODE 
  
> The passed-in strings are in Unicode format. If the MAPI_UNICODE flag is not set, the strings are in ANSI format. 
    
MAPI_USE_DEFAULT 
  
> The messaging subsystem should substitute the profile name of the default profile for the  _lpszProfileName_ parameter. The MAPI_EXPLICIT_PROFILE flag is ignored unless  _lpszProfileName_ is NULL or empty. 
    
 _lppSession_
  
> [out] Pointer to a pointer to the MAPI session interface.
    
## Return value

S_OK 
  
> The logon succeeded.
    
MAPI_E_LOGON_FAILED 
  
> The logon was unsuccessful, either because one or more of the parameters to MAPILogonEx were invalid or because there were too many sessions open already.
    
MAPI_E_TIMEOUT 
  
> MAPI serializes all logons through a mutex. This is returned if the MAPI_TIMEOUT_SHORT flag was set and another thread held the mutex. 
    
MAPI_E_USER_CANCEL 
  
> The user canceled the operation, typically by clicking the **Cancel** button in a dialog box. 
    
## Remarks

MAPI client applications call the MAPILogonEx function to log on to a session with the messaging system. All strings that are passed in and returned to and from MAPI calls are null-terminated and must be specified in the current character set or code page of the calling client or provider's operating system.
  
The  _lpszProfileName_ parameter is ignored if there is an existing previous session that called MapiLogonEx with the MAPI_ALLOW_OTHERS flag set and if the flag MAPI_NEW_SESSION is not set. If the  _lpszProfileName_ parameter is NULL or points to an empty string, and the  _flFlags_ parameter includes the MAPI_LOGON_UI flag, the MAPILogonEx function generates a logon dialog box that has an empty field for the profile name. 
  
When logging on to a specific profile, a client should pass the MAPI_NEW_SESSION flag into MAPILogonEx in addition to the profile name. Otherwise, if another client has established a shared session by logging on with MAPI_ALLOW_OTHERS, the client will be logged on to the shared session instead of to the profile requested. 
  
The MAPI_EXPLICIT_PROFILE flag does not cause the default profile name to be used when  _lpszProfileName_ is NULL or empty unless the MAPI_USE_DEFAULT flag is also present. 
  
The MAPI_NO_MAIL flag has several effects that cause the following when not using the MAPI spooler:
  
- No messages can be sent or delivered by the MAPI spooler during this session. Only tightly coupled store and transport providers can send and deliver messages. 
    
- Server based stores might still send or deliver messages. 
    
- Messages sent or delivered by server based stores are not processed by any hook providers. 
    
- Per-message and per-recipient options for transports are not available. 
    
- The status table does not contain entries for transport providers, and any transport functionality dependent on status objects (such as configuration) is not available. 
    
- The message spooler row in the status table contains the STATUS_FAILURE value. 
    
- Piggybacked logons are allowed, but those logons do not cause the previous logon to receive status object updates. 
    
A service should always log on using the MAPI_NO_MAIL flag. 
  
## MFCMAPI reference

For MFCMAPI sample code, see the following table.
  
|**File**|**Function**|**Comment**|
|:-----|:-----|:-----|
|MAPIObjects.cpp  <br/> |CMapiObjects::MAPILogonEx  <br/> |MFCMAPI uses the MAPILogonEx method to log on to MAPI. |
   
## See also



[IMAPISession::GetMsgStoresTable](imapisession-getmsgstorestable.md)
  
[IMAPISession::OpenMsgStore](imapisession-openmsgstore.md)


[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

