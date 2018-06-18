---
title: "Default Message Stores"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: efa178eb-feb2-443f-8f6b-2ea53a456bf2
description: "Last modified: July 23, 2011"
 
 
---

# Default Message Stores

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A default message store is one that client applications can use for general purpose messaging tasks. There are a number of optional features for message store providers that become required if the message store provider is to be used as the default message store. They are as follows:
  
- Implementing the special folders: the Inbox, Outbox, and search-results folders.
    
- Providing read and nonread reports.
    
- Allowing incoming and outgoing message submissions.
    
- Allowing the creation of messages with arbitrary message classes.
    
- Supporting named and multiple-value properties.
    
- Supporting the [IMSProvider::SpoolerLogon](imsprovider-spoolerlogon.md) method, even if the message store provider is tightly coupled with a transport provider. 
    
- Supporting associated contents tables. For more information, see [Contents Tables](contents-tables.md).
    
- Supporting notification of the MAPI spooler when there are messages in the outgoing message queue.
    
## See also



[Developing a MAPI Message Store Provider](developing-a-mapi-message-store-provider.md)

