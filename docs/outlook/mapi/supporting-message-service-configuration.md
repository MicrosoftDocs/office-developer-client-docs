---
title: "Supporting Message Service Configuration"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
localization_priority: Normal
api_type:
- COM
ms.assetid: bb6ab537-2876-474b-be7a-84734ace2bae
description: "Last modified: July 23, 2011"
 
 
---

# Supporting Message Service Configuration

  
  
**Applies to**: Outlook 
  
To support message service configuration, use the following procedure:
  
1. Implement an entry point function that conforms to the [MSGSERVICEENTRY](msgserviceentry.md) prototype. Message service entry point functions manage access to configuration data and are called in the following circumstances: 
    
  - When a client logs on to retrieve information to configure your message service.
    
  - When a client wants to view or change a configuration property. 
    
    Although most message services will provide entry point functions, as they should, these functions are not strictly required. Message services can provide access to configuration data in other ways. However, using an entry point function standardizes and simplifies the process of configuration.
    
    MAPI expects all message service entry point functions to be able to store and retrieve properties from the profile sections that are associated with their message service. You can support this functionality interactively, programmatically, or both interactively and programmatically.
    
    To support interactive configuration, provide a property sheet that displays the properties involved in configuring your message service. As an option, you can also supply property sheets for each configurable provider. Some message services restrict users to a read-only view of configuration properties; other message services allow users to make changes.
    
    To support programmatic configuration, your message service entry point function must be able to work without user intervention. If your message service can be called by the Profile Wizard, you must support programmatic configuration. If your message service does not allow itself to be configured by using the Profile Wizard, you can choose whether or not to support programmatic configuration.
    
    For more information about how to support configuration in a message service entry point function, see [MSGSERVICEENTRY](msgserviceentry.md).
    
2. Publish the name of your message service entry point function in the Mapisvc.inf configuration file by including the following entry in the message service section:
    
     `PR_SERVICE_ENTRY_NAME=<name of message service>`
    
3. Create one or more property sheet dialog boxes for displaying configuration data.
    
4. Perform the following tasks if you want to allow the Profile Wizard to configure your message service:
    
  - Implement an entry point function that conforms to the [WIZARDENTRY](wizardentry.md) prototype. 
    
  - Implement a standard Windows dialog box procedure that conforms to the [SERVICEWIZARDDLGPROC](servicewizarddlgproc.md) prototype. 
    
  - Enhance your message service entry point function to respond to additional events.
    
## See also



[Message Service Implementation](message-service-implementation.md)

