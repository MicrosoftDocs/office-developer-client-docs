---
title: "Implementing Security"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 62db34a0-887c-4607-94ad-d8cae68b35c2
description: "Last modified: July 23, 2011"
---

# Implementing Security

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
If the messaging system requires it, the transport provider is responsible for implementing an appropriate level of security for access to the messaging system. Each incoming or outgoing message sent through a transport provider by the MAPI spooler is handled in the context of a provider logon session. The transport provider can display a logon dialog box to the user that prompts for a user's credentials before establishing such a connection. Alternatively, the transport provider can store the user's previously entered credentials in the secure property range within a profile section and use them for access without prompting.
  
When implementing your transport provider's security, consider the following:
  
- With multiple installed service providers, there can be a multitude of names and passwords associated with a user.
    
- MAPI allows multiple sessions with multiple identities. Providers are encouraged to support multiple sessions but are not required to do so.
    
- Each session with a transport provider is associated by MAPI with a discrete section in the user's profile. The transport provider can use the [IMAPISupport::OpenProfileSection](imapisupport-openprofilesection.md) method to gain access to this section, which can be used to store any information associated with this session, including credentials. 
    
- With multiple installed transport providers, it is not necessarily true that the user only has a single e-mail address. A user can have a separate e-mail address for each installed transport provider or can have a different address for each session on a single provider.
    
For more information about storing credentials in profile sections, see [Message Services and Profiles](message-services-and-profiles.md) and [IProfSect : IMAPIProp](iprofsectimapiprop.md).
  

