---
title: "Developing a MAPI Address Book Provider"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 821cc42d-eebb-4327-b2d4-594421a5c22c
description: "Last modified: July 23, 2011"
 
 
---

# Developing a MAPI Address Book Provider

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
An address book provider supplies recipient information to client applications, to message store and transport providers, and to MAPI. Recipient information is organized hierarchically into storage compartments known as containers. Every address book in the profile contributes one or more top-level, or parent, containers to the MAPI address book, an integrated view of recipient information from all address book providers in a session. It is through the MAPI address book that clients and other service providers gain access to the data of an address book provider.
  
MAPI builds the integrated address book by:
  
1. Retrieving the top-level containers from each address book provider.
    
2. Retrieving each container's hierarchy table. 
    
3. Copying each hierarchy table into an integrated hierarchy table. It is the integrated hierarchy table that is exposed to the client. 
    
MAPI imposes few requirements on address book provider writers. The range of possible features you can implement as an address book writer is varied and flexible. For example, your provider could be limited to supplying a read-only view of a particular type of recipient information or implement a full set of features, perhaps allowing clients or providers to make additions or modifications to the recipient data and to impose search criteria for defining customized views. 
  
Your provider's data can reside locally in a file or database or on a remote server. Some address book providers are meant to work with a particular messaging system, tightly coupled with a transport provider, while others can operate with any messaging system.
  
MAPI defines a special type of address book provider called a personal address book, or PAB, that implements a single modifiable container and can hold recipient information copied from other containers as well as information created directly. Although any address book provider can implement a PAB and multiple PABs can be added to a profile, only one of these providers can be designated to operate as the PAB during any one session. 
  

