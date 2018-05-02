---
title: "MAPI Sessions"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: c5a7c137-393e-40ff-a2b9-afe02da2435a
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Sessions

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Before the client application can call an underlying messaging system, it must establish a session, or connection, with the MAPI subsystem.
  
Sessions are initiated when a user logs on, a process that accesses a valid profile and validates the messaging system and the message service credentials. Then, the process ensures that all of the profile's message services are correctly configured. The client interface you use determines the logon call. MAPI clients call the [MAPILogonEx](mapilogonex.md) function. 
  
Message service configuration is one of the most important parts of the logon process. The profile is the initial source for configuration information. If information for a particular message service is missing, the logon process tries to prompt the user to supply it. This is not always successful for two reasons: First, prompting the user requires the display of a dialog box. It is possible for clients to disallow the display of a user interface by passing a flag into the logon call. Second, the user could cancel the dialog box before the needed information can be added.
  
When a logon process fails one time, the user is informed of the failure and given the chance to retry or correct the error condition. Once again, a user interface will be displayed, if the client allows it, and the user will be prompted to enter whatever data is missing. If this second try is unsuccessful, MAPI disables all service providers in the message service for the duration of the session. In effect, the whole message service is disabled. This means that none of the service providers in the message service can work. This is done because if one provider fails logon, the other providers usually also fail. The logon process can fail due to an invalid path for a necessary resource, an incompatible version of MAPI, an unavailable messaging server, or data corruption. 
  
Clients can specify one of two types of sessions to be established in the logon call: an individual session or a shared session. Individual sessions are private connections; there is a one-to-one relationship between a client application and the session it is using. As a consequence, client applications that share a session also share a profile. Shared sessions are established once but can be used by other client applications that need to use them. The profile and credentials are specified only with the initial logon. 
  
Clients can log on multiple times as the same user or as multiple users. MAPI does not prevent this. Some service providers, however, might not be as flexible, returning the error value MAPI_E_SESSION_LIMIT on subsequent logon attempts. Service providers with underlying hardware limitations can be required to enforce a session limit.
  
The function calls for establishing a session have a collection of flags and parameters that control how the session is created. The client specifies an optional profile name and a window handle that acts as the parent window for any dialog boxes that are displayed. The flags include MAPI_NEW_SESSION, which requests that a new, individual session (rather than a shared session) be established, and the MAPI_LOGON_UI user interface flag. The user interface flag is set to request a logon dialog box.
  
The following illustration shows how these various parameters and flags establish a MAPI session.
  
 **MAPI session flowchart**
  
![MAPI session flowchart](media/amapi_47.gif)
  
For information about handling sessions from within a client application, see [MAPI Session Handling](mapi-session-handling.md)
  
## See also

#### Reference

[MAPILogonEx](mapilogonex.md)
  
[IMAPISession : IUnknown](imapisessioniunknown.md)
#### Concepts

[MAPI Session Handling](mapi-session-handling.md)
  
[MAPI Programming Overview](mapi-programming-overview.md)

