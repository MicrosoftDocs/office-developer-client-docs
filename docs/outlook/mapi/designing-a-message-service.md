---
title: "Designing a Message Service"
 
 
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
 
 
localization_priority: Normal
api_type:
- COM
ms.assetid: 32627ebb-547f-4fac-a406-e7243ec5521b
description: "Last modified: July 23, 2011"
---

# Designing a Message Service

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Before you begin to write code to support your message service, it is important to create a design. Resolve the following issues in your design process:
  
1. Determine how many service providers should be included in the message service. Include only related service providers (that is, providers that work with the same messaging system) in your service. Unrelated service providers do not belong in the same message service. Use the profile for integrating unrelated service providers and message services.
    
2. Determine what type of service providers should be included in the message service. Most messge services include one provider of each of the common types. That is, the typical message service has one address book provider, one message store provider, and one transport provider.
    
3. Determine how many DLLs should contain the message service. The number of DLLs that a message service uses depends on the following:
    
  - The degree of complexity that you as the writer of the message service are willing to handle.
    
  - The type of service providers in the message service.
    
  - The relationship that the message service might have with another message service.
    
    Because MAPI stores only one entry point for each provider type, do not include multiple providers of the same type in a single DLL. If it makes sense to include multiple providers of one type, either implement them in separate DLLs or have them share an entry point function. Another option is to implement related message services, or message services that are able to use the same installation and configuration code and the same DLL entry point function, in one DLL.
    
    If possible, keep it simple and use one DLL that contains the implementation of all the service providers in the message service and all the code to install and configure the message service. If this is not possible, you can implement one DLL for the installation and configuration code and either a single DLL for all of the service providers or one DLL for each provider.
    
4. Determine a name for the message service DLL or DLLs. 
    
## See also

#### Concepts

[Message Service Implementation](message-service-implementation.md)

