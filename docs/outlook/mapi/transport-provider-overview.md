---
title: "Transport Provider Overview"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: a51547e6-8f0e-45f4-a341-3cfa735112c2
 
 
---

# Transport Provider Overview

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A transport provider is a dynamic-link library (DLL) which acts as an intermediary between the MAPI subsystem and one or more underlying messaging systems. A messaging system is some specific mechanism by which messages are sent and received. Some examples of messaging systems are:
  
- A shared network file system that the transport provider writes messages to directly.
    
- A TCP/IP network interface that the transport provider uses to connect to a messaging server.
    
- An online service that users connect to.
    
- A host-based messaging or office automation system.
    
- A set of remote procedure calls to a messaging server.
    
- Anything that can be used to transfer data from one computer to another.
    
A transport provider DLL must conform to the interface specified by MAPI. As a transport provider developer, you will implement this interface in terms of the functionality present in the messaging system.
  

