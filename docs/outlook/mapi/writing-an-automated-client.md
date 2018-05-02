---
title: "Writing an Automated Client"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: b8f9ac1a-b377-4f83-8fb6-ed85ab9053d0
description: "Last modified: July 23, 2011"
 
 
---

# Writing an Automated Client

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
An automated client application is an application that runs unattended, displaying no user interface.
  
 By default, many MAPI interface methods show a user interface. All of these methods have flags that allow a client to either allow or suppress this display. Although MAPI expects service providers to honor these flags, there are some providers that do not always meet these expectations. A legitimate reason for not honoring the flags is the reliance of the service provider on another service that does not allow user interface suppression. If you are developing an automated client, pay careful attention to the service providers you are using and how they are configured. Do not assume that all of your calls to suppress a user interface will be successful. 
  
Automated clients must have the necessary information available for proper configuration of each of the message services in the profile. There are two ways to supply configuration information at logon time:
  
- The service provider can retrieve information from the profile.
    
- The service provider can prompt the user for information. 
    
Since the second option is unavailable to automated clients, these clients must use the first option. Clients must configure their profiles carefully to ensure that this option always works.
  
Automated clients always set the MAPI_NO_MAIL flag in the [MAPILogonEx](mapilogonex.md) function call to begin a MAPI session. 
  

