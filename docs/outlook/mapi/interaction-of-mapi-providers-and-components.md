---
title: "Interaction of MAPI Providers and Components"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: 2c0e010b-0432-4ef7-a243-3a4b46f0a19d
description: "Last modified: July 23, 2011"
 
 
---

# Interaction of MAPI Providers and Components

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
MAPI service providers of any kind must follow certain guidelines to work with other MAPI components. Each service provider must:
  
- Use the proper provider and logon objects for initialization.
    
- Return a dispatch table of provider entry points to the messaging system upon initialization.
    
- Register a MAPI status table row for each resource owned by the provider and call the [IMAPISupport::ModifyStatusRow](imapisupport-modifystatusrow.md) method at appropriate times. 
    
- Use the [IMAPISupport::NewUID](imapisupport-newuid.md) method to obtain valid unique identifiers (UIDs). 
    
- Support the common MAPI interfaces on objects it returns.
    
- Use the MAPI memory allocation functions to allocate memory returned to client applications and to release memory allocated by other parts of the MAPI subsystem.
    
- Maintain a profile section, if necessary, to store credentials to the underlying messaging system.
    
- Use the [IMAPISupport::RegisterPreprocessor](imapisupport-registerpreprocessor.md) method to register any message preprocessing functions. 
    
- Include the proper header files (including mapispi.h) that define common constants, structures, interfaces, and return values.
    
- Follow address format conventions for common address types.
    

