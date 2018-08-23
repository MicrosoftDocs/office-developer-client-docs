---
title: "Tightly Coupled Message Store Providers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 2eb493d7-bbd1-45b2-bd82-2bc452b2deab
description: "Last modified: July 23, 2011"
 
 
---

# Tightly Coupled Message Store Providers

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Message store providers can be tightly coupled with a transport provider. Tightly coupling MAPI service providers means implementing the two providers such that the store provider and transport provider can communicate to make the process of sending and receiving messages more efficient. The benefit of doing this is that performance improvements can result when two service providers can interact with each other directly rather than by means of MAPI spooler. To tightly couple a message store provider to a transport provider, the transport provider must place the message store provider's entry identifier in the **PR_OWN_STORE_ENTRYID** ([PidTagOwnStoreEntryId](pidtagownstoreentryid-canonical-property.md)) property in the transport provider's row in the MAPI status table. This enables MAPI spooler to connect the store provider to the transport provider.
  
There is no requirement that a message store provider ever be tightly coupled with any other service provider. The most common service provider to tightly couple with a message store provider is a transport provider. This is usually done so that sending and receiving messages can be accomplished without involving the MAPI spooler. For example, when the user submits an outgoing message, the combined message store provider and transport provider can send it directly. The combined service providers do not have to first notify MAPI spooler that there is a new message to process and then wait for MAPI spooler to initiate the process of transferring the message from the message store provider to the transport provider. This has particular benefits when a server-based message store is being used by minimizing network traffic between the user's computer and the server.
  
In general, there are no well-specified procedures for tightly coupling service providers. However, you should use the following guidelines:
  
- If the reason for tightly coupling service providers is performance, be aware that the coupling takes parts of the MAPI subsystem out of the processes that those parts would normally be involved in. This implies that the individual parts in the combined service provider should interact with each other in a way that simulates the interaction they would normally have with the parts of the MAPI subsystem that are not being used.
    
- When tightly coupled service providers do interact with other MAPI components, they must still interact with them in exactly the way they would if they were not tightly coupled. For example, if a user is using a combined message store provider and transport provider as their default message store but is using a separate transport provider to send messages — as can happen when a user takes a computer on the road and switches to a remote transport provider — the message store portion of the tightly coupled service provider must still interact with MAPI spooler just as if it were a standalone message store provider.
    
## See also



[Developing a MAPI Message Store Provider](developing-a-mapi-message-store-provider.md)

