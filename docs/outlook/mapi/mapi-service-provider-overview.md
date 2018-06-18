---
title: "MAPI Service Provider Overview"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: e7cbc79f-3d60-4f21-a378-7b0088ee8ad3
description: "Last modified: June 25, 2012"
 
 
---

# MAPI Service Provider Overview

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Between the MAPI subsystem and the messaging systems are the various service providers. Service providers are like drivers that connect MAPI client applications to an underlying messaging system. There are three types of providers: message store providers, address book or directory providers, and message transport providers. MAPI supports each type of service independently, enabling a vendor to offer one or more custom service providers. For example, a vendor might want to create an address book provider that uses a corporate telephone book directory of employees or to create a message store provider that uses an existing database.
  
Service providers are typically written for specific messaging systems by software developers who have specialized knowledge or experience with a particular system. For example, the Microsoft Outlook 2013 and Microsoft Outlook 2010 Mobile Services use an address book provider to expose a mobile address book in Outlook. 
  
MAPI presents client applications with a unified view of address book and transport provider information. This integrated approach prevents the client application from having to map data to the appropriate provider. It also prevents the user from having to negotiate among multiple address book and transport provider addressing schemes. Message store provider information, however, is not unified, and clients that use multiple message store providers are responsible for handling them individually.
  
The service providers work with MAPI to create and send messages in the following way: messages are created by using a form that is appropriate for the specific type, or class, of message. Many messages are made with the standard note form that comes with the MAPI subsystem, either by the user of a client application or programmatically without user interaction. The completed message is addressed to one or more recipients — a user or group of users designated to receive the message. A recipient might or might not have an entry in a directory that one of the installed address book providers owns. Recipients that are not associated with an installed address book provider are called custom recipients or one-off addresses. A one-off address can be temporary, lasting only until the message is submitted. 
  
When the client application sends the message, the message store provider checks that each recipient has a unique and valid address and that the message has all of the information necessary for transmission. If there is a question about a recipient (for example, when there are multiple recipients with the same name), an address book provider takes care of resolving the ambiguity. The message is then placed in the outbound queue. 
  
## See also



[MAPI Features and Architecture](mapi-features-and-architecture.md)

