---
title: "Message Service Implementation"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: bb529cc7-ad09-4f86-89bc-0e8ad29a3f38
description: "Last modified: July 23, 2011"
 
 
---

# Message Service Implementation

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
A message service is one or more related service providers grouped together for the purpose of simplifying installation and configuration. All service providers should be included in a message service.
  
To implement a message service with one or more providers, use the following procedure:
  
1. Design the message service, determining the number and type of service providers to be included. For more information about how to design a message service, see [Designing a Message Service](designing-a-message-service.md).
    
2. Create a setup program to install the service providers in the message service. For more information about writing a message service setup program, see [Supporting Message Service Installation](supporting-message-service-installation.md). 
    
3. Create an entry point function to perform configuration. For more information about writing a message service entry point function, see [Supporting Message Service Configuration](supporting-message-service-configuration.md) and [MSGSERVICEENTRY](msgserviceentry.md). 
    
4. Create a public header file that contains the property tags and descriptions of valid values for any custom properties that the message service supports. 
    
## See also

#### Concepts

[MAPI Service Providers](mapi-service-providers.md)

