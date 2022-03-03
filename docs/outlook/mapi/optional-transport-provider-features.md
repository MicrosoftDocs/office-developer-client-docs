---
title: "Optional Transport Provider Features"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 0bec2c17-b41c-4e46-8961-a55bde1f7326
 
 
---

# Optional Transport Provider Features

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Optional features transport providers can implement include:
  
- Registering message and recipient options specific to the transport provider.
    
- Maintaining a profile, if necessary, to store configuration information and credentials to the messaging system.
    
- Performing any verification of credentials required by the messaging system.
    
- Supporting event notification for interested client applications with the [IMAPISupport::Notify](imapisupport-notify.md) method. 
    
- Displaying configuration property sheets and wizard dialog boxes to enable users to configure the transport provider's settings.
    
- Providing message delivery reports to client applications.
    

