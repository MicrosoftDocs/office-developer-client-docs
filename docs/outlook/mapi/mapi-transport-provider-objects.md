---
title: "MAPI transport provider objects"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 4f28fab8-2ce1-4398-a941-6d718c9bbd6a
description: "Last modified: July 23, 2011"
---

# MAPI transport provider objects
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
In addition to the standard provider and logon objects implemented by all service providers, transport providers are required to implement a status object. For the other service provider types, implementing a status object is optional. However, MAPI requires it for transport providers. Transport providers that support the downloading of message headers from a remote server also implement a folder and a table. 
  
The following illustration shows each of the objects that transport providers can implement with their corresponding interfaces. The illustration also indicates whether MAPI or a client is the object's user.
  
![Objects that transport providers implement](media/amapi_66.gif "Objects that transport providers implement")
  
## See also

- [MAPI Service Provider Objects](mapi-service-provider-objects.md)

