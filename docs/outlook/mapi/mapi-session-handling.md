---
title: "MAPI Session Handling"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 3bc4aea5-ab01-4ba5-a4ad-7a9a76c6bf55
description: "Last modified: July 23, 2011"
 
 
---

# MAPI Session Handling

  
  
**Applies to**: Outlook 
  
Before you can communicate with service providers and an underlying messaging system, you must establish a session. A MAPI session is a link from a client to other MAPI components. As the result of successfully starting a session, MAPI returns to clients a pointer to a session object — an object that implements the **IMAPISession** interface. For more information, see [IMAPISession : IUnknown](imapisessioniunknown.md). You can use the methods of the **IMAPISession** interface to access the objects of address book and message store providers, access several tables, display forms, set transport provider properties, and perform profile and message service administration. 
  
## In this section

[Starting a MAPI Session](starting-a-mapi-session.md)
  
> Describes how to start a MAPI session and includes links to topics with more detailed information.
    
[Ending a MAPI Session](ending-a-mapi-session.md)
  
> Describes how to end a MAPI session.
    
[Accessing Objects by Using the Session](accessing-objects-by-using-the-session.md)
  
> Describes how to use a session pointer to access session objects.
    
[Retrieving Primary and Provider Identity](retrieving-primary-and-provider-identity.md)
  
> Describes the properties used to retrieve primary and provider identity.
    
[Status Table and Status Objects](status-table-and-status-objects.md)
  
> Describes how to access information from the status table.
    

