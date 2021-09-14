---
title: "Testing and Debugging"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 0afceb1f-9086-4cc9-8ce4-fb9256a81a9c
description: "Last modified: July 23, 2011"
 
 
---

# Testing and Debugging

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Testing strategies differ depending on whether you are developing a client or service provider. Because a client application requires one or more service providers to operate, clients should be tested in an environment with different sets of service providers.
  
Service providers, however, should be tested in isolation before being integrated with other providers. MAPI provides tools that are meant to test the features of a service provider of a particular type. The [MFCMAPI](https://go.microsoft.com/fwlink/?LinkId=124154) sample application shows how to test the features of an address book provider and works with a message store provider. 
  
## See also



[MAPI Programming Overview](mapi-programming-overview.md)
  
[MFCMAPI as a Code Sample](mfcmapi-as-a-code-sample.md)

