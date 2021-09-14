---
title: "Logging on to MAPI"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 05bafe43-a78a-4659-92f0-0b4fe444c64f
description: "Last modified: July 23, 2011"
---

# Logging on to MAPI
 
**Applies to**: Outlook 2013 | Outlook 2016 
  
Client applications log on to the MAPI subsystem by calling the **MAPILogonEx** function. For more information, see [MAPILogonEx](mapilogonex.md). **MAPILogonEx** validates the profile selection and the configuration of each service provider in the profile. Once configured, MAPI starts the address book providers before starting the message store providers. Transport providers are started when their services are first required. 
  
## Choose a profile
  
- Pass in a character string that represents the name of the profile in the  _lpszProfileName_ parameter to **MAPILogonEx**, or...
    
- Allow the user to specify the profile by passing NULL in the  _lpszProfileName_ parameter and setting the MAPI_LOGON_UI flag, or... 

- Select the default profile by passing NULL in the  _lpszProfileName_ parameter and setting the MAPI_USE_DEFAULT flag. 
    
If you require a specific profile other than the default profile, you must save its name in your own configuration database or use a specific naming convention. MAPI does not expose any profile attributes other than the name and default flag in the profile table, and the default profile flag is reserved for messaging client and related IPM applications.
  
Clients that supply partial profile or provider configuration information to **MAPILogonEx** must prompt the user for the additional data by allowing a dialog box to be displayed. If information is missing and **MAPILogonEx** cannot prompt the user to supply it, the logon fails. Clients that do not need user input can suppress the dialog box display. 
  
The flags that **MAPILogonEx** uses to enable a user interface are mutually exclusive; only one can be set. Leaving these flags unset suppresses the display of a user interface, causing **MAPILogonEx** to fail if necessary information is missing. That is, if you disable the user interface and pass NULL for the  _lpszProfileName_ parameter and do not set the MAPI_USE_DEFAULT flag, **MAPILogonEx** will fail because it cannot retrieve a profile name. 
  
The session that **MAPILogonEx** establishes can be an individual messaging session, a shared messaging session, or a nonmessaging session. Individual messaging sessions are private connections between your client and the MAPI subsystem and can be established by setting the MAPI_NEW_SESSION flag in the call to **MAPILogonEx**.
  
Shared messaging sessions are connections that multiple messaging clients can use. Shared sessions are typically established for clients use the same profile. To establish a new session as a shared session, set the MAPI_ALLOW_OTHERS flag. 
  
## Use an existing shared session
  
- Do not set the MAPI_NEW_SESSION flag.
    
- Do not set the MAPI_ALLOW_OTHERS flag.
    
- Pass NULL for the  _lpszProfileName_ parameter. 
    
- Pass NULL for the  _lpszPassword_ parameter. 
    
Nonmessaging sessions allow clients to access the MAPI subsystem, but do not allow messages to be sent or received. Configuration or administration applications are examples of clients that might need to establish nonmessaging sessions. To request a nonmessaging session, set the MAPI_NO_MAIL flag. Setting this flag logs your client on without informing the MAPI spooler. Clients that log on to MAPI with this flag cannot expect to ever receive read status reports.
  
The MAPI_NO_MAIL flag should only be set:
  
- If your client will not send or receive messages during the session.
    
- If your client has complete control over the contents of the profile and messages are sent and received using tightly coupled message store and transport providers, such as the Microsoft Exchange providers.
    
A messaging client can share a session with a nonmessaging client. The characteristics of one member of a shared session are not affected by the characteristics of other members. That is, if you log on with the MAPI_NO_MAIL and MAPI_ALLOW_OTHERS flags set, a messaging client logging on to your session has no affect on the operation of your client and vice versa. The messaging client will still be able to send and receive messages and your client will not.
  
**MAPILogonEx** defines a few other flags that you can set: 
  
- MAPI_FORCE_DOWNLOAD indicates that incoming messages should be downloaded before **MAPILogonEx** returns. Not setting this flag causes messages to be downloaded in the background at a later time. 
    
- MAPI_SERVICE_UI_ALWAYS requests that every message service in the profile display a configuration dialog box.
    
- MAPI_NT_SERVICE indicates that your client is implemented as a Windows service. This flag must be set if your client is a service.
    
With every successful logon, **MAPILogonEx** returns a pointer to a MAPI session. You can use this pointer to call the methods of the **IMAPISession** interface. For more information, see [IMAPISession : IUnknown](imapisessioniunknown.md). Session pointers, regardless of the type of session, are unique to the clients that receive them and are not valid across tasks.
  

