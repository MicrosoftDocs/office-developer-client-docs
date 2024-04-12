---
title: "Developing a MAPI Client Application"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: bcb59b08-e6d7-4739-8cb5-e545bd0d478f
 
 
---

# Developing a MAPI Client Application

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
MAPI client applications are written with the object oriented MAPI client interface. MAPI clients interact with one or more messaging systems through the MAPI subsystem and MAPI-compliant service providers. This interaction can occur in many different ways; there is an enormous variety in client applications. Most clients are messaging clients, either integrating messaging into their established feature set or performing messaging as their primary feature. Other features that MAPI clients might provide include profile administration or address book and message store management.
  
All messaging clients initialize the MAPI libraries and start a **session** with the MAPI subsystem. For more information, see [Accessing Objects by Using the Session](accessing-objects-by-using-the-session.md). After a session has been established, a client can:
  
- Handle outgoing messages, including replies, forwarded messages, and retransmissions.
    
- Handle incoming messages.
    
- Handle the message store by opening folders and messages, creating, modifying, copying, and sending messages, tracking conversations, and searching one or more folders.
    
- Handle the address book by creating and modifying recipients, locating entries, and traversing the container hierarchy.
    
- Handle a transport provider by performing reconfiguration, setting options and transport order, and sending messages on demand.
    
- Handle event notification.
    
- Handle forms.
    
- Handle profiles and message services.
    
Use the topics in this section to help you implement these basic tasks and the specific features that will make your MAPI client unique.
  

