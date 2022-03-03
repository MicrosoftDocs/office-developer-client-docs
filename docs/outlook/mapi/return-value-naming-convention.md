---
title: "Return Value Naming Convention"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 2c1cdd7b-82f1-46f2-a7ce-e0efe857b7cd
 
 
---

# Return Value Naming Convention

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
The MAPICODE.H header file contains many of the values that a client or service provider might return from an interface method implementation or might see returned from a call.
  
The codes to represent warning and failure conditions follow a different naming convention that begins with the prefix MAPI, an underscore, and either a W or an E to indicate the type of code. The rest of the code is a short character string to describe the condition. Each word in the string is separated by an underscore. For example, the error value MAPI_E_TOO_COMPLEX indicates that the implementation could not handle whatever was being requested in the call. The warning value MAPI_W_PARTIAL_COMPLETION indicates that the call succeeded, but that there were problems. Only part of the operation was completed successfully.
  

