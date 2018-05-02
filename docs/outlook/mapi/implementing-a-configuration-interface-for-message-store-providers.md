---
title: "Implementing a Configuration Interface for Message Store Providers"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 508e6950-d483-4cbe-b817-8016f4aa5cd8
description: "Last modified: July 23, 2011"
 
 
---

# Implementing a Configuration Interface for Message Store Providers

 **Last modified:** July 23, 2011 
  
 * **Applies to:** Outlook * 
  
Message store providers are required to implement an interface that allows the user to configure the message store provider to run on that user's computer. Typically, the message store provider is configured when the message store provider is added to a user's profile. The message store provider's configuration interface generally handles tasks such as setting user names and passwords for protected message stores, choosing paths to necessary files, and creating the underlying storage mechanism it will use, if necessary.
  
The configuration interface you implement is accessed through additional entry points in your message service provider's DLL. For more information, see [Configuring a Message Service](configuring-a-message-service.md). The message store provider's configuration interface is the only user interface that a message store provider must implement.
  
## See also

#### Concepts

[Message Store Features](message-store-features.md)

